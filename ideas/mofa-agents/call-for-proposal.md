# MoFA Agents: Support All Models

> GSoC 2026 Call for Proposal — Model Orchestration Track

---

## 1. The Open Questions

AI agents don't just talk — they listen, see, speak, draw, and reason. A single agent workflow might chain a speech recognition model (ASR), a large language model (LLM), a text-to-speech model (TTS), and an image generation model — all in one pipeline. Yet most tools today support only a narrow slice of this spectrum.

MoFA's ambition is to be a framework where **any model whose primary use case is inference** is a first-class citizen. This CFP asks you to wrestle with three hard questions:

### Question 1: How should MoFA support LLMs, VLMs, TTS, ASR, and all other inference models?

Today's model landscape is vast and fragmented:

| Modality | Examples | Input → Output |
|----------|----------|----------------|
| **LLM** (Large Language Model) | Qwen, Llama, Mistral, DeepSeek | Text → Text |
| **VLM** (Vision-Language Model) | Qwen-VL, LLaVA, Gemma 3 | Image+Text → Text |
| **ASR** (Automatic Speech Recognition) | Whisper, FunASR Paraformer | Audio → Text |
| **TTS** (Text-to-Speech) | GPT-SoVITS, Bark, VITS | Text → Audio |
| **Image Generation** | Stable Diffusion, FLUX | Text → Image |
| **Embedding** | BGE, E5, GTE | Text → Vector |
| **Reranker** | BGE-Reranker, Cohere | Text pairs → Score |
| **Video Generation** | Wan, CogVideo | Text → Video |
| **Multimodal (Omni)** | GPT-4o, Qwen-Omni | Any → Any |

Each modality has different input/output types, latency profiles, memory footprints, and execution patterns (streaming vs. batch, real-time vs. offline). A framework that claims to "support all models" must have an abstraction that is general enough to cover this diversity without becoming so abstract that it's useless.

**The design challenge**: What is the right trait/interface for a "model" in MoFA? Is it one universal `InferenceBackend` trait, or a family of modality-specific traits (`TextGenerator`, `SpeechRecognizer`, `ImageGenerator`, ...)? How do you handle models that span multiple modalities (e.g., GPT-4o accepts text, image, and audio)?

### Question 2: How can MoFA quickly support new model types as they emerge?

The pace of innovation in AI models is relentless. In 2023, "models" meant LLMs. By 2024, vision-language models and voice models were mainstream. In 2025, omni-models that handle text, image, audio, and video in a single architecture emerged. By the time you read this, there may be new modalities we can't predict.

A framework that hard-codes support for today's model types will be obsolete tomorrow. MoFA needs a **model integration architecture** that allows:

- New model types to be added without modifying framework core code
- Community contributors to add support for new models independently
- Model providers to write their own MoFA adapters
- Graceful handling of models that don't fit existing categories

**The design challenge**: How do you design a plugin/adapter system for model integration that is both easy to extend and type-safe? How do you handle the tension between a generic interface (easy to add new models) and a specific interface (better tooling, better error messages, better performance)?

### Question 3: Why can MoFA support them better than existing orchestrators?

This is the hardest question, and it requires honest answers.

<p align="center">
  <img src="./images/ai-native-frameworks-ecosystem.png" alt="The AI-Native Framework Ecosystem" width="80%">
</p>

---

## 2. The Landscape: What Exists Today and Where the Gaps Are

### The Current Model Orchestration Ecosystem

Let's be honest about what's already out there — and what each tool gets right and wrong.

#### Ollama — The Docker for LLMs

Ollama made local LLM inference accessible: `ollama run llama3` and you're chatting. It supports 100+ LLM families and some vision models, with a clean OpenAI-compatible API. But Ollama is **text-in, text-out**. No native ASR, TTS, or image generation. Audio capabilities for omni-models (e.g., MiniCPM-o) aren't functional even when the model theoretically supports them. One model at a time, no multi-model orchestration.

#### LM Studio — The Desktop LLM Experience

LM Studio provides a polished GUI for downloading and running LLMs locally, with both llama.cpp and MLX backends on macOS. It covers LLMs and VLMs, but like Ollama, **no native audio or image generation**. TTS and ASR require external tool integration. Closed-source. Single-model focused.

#### vLLM — The Production Serving Engine

vLLM is the gold standard for high-throughput LLM serving, with PagedAttention, continuous batching, and speculative decoding. **vLLM-Omni** (released late 2025) extends this to multi-modal serving — modality encoders (ViT, Whisper), LLM core, and modality generators (DiT for images/audio). But vLLM is **NVIDIA GPU only, server-oriented**. No Apple Silicon support. Not designed for on-device or edge deployment.

#### HuggingFace — The Universal Model Hub

HuggingFace hosts 2M+ models across every modality. The `transformers` library supports LLMs, VLMs, ASR, TTS, image generation, and more. But it's **Python-only**, with significant overhead for on-device deployment. MPS backend on Apple Silicon has gaps (no FP16 in many cases, some ops fall back to CPU). No built-in multi-model orchestration — you wire it yourself.

#### Cherry Studio — The Universal Client

Cherry Studio connects to 50+ cloud and local AI providers through a unified desktop interface. But it's **a client, not an engine** — it depends entirely on external providers for actual inference. No native TTS, ASR, or image generation. It aggregates, it doesn't orchestrate.

### MoFA's Building Blocks

MoFA is not starting from zero. Two existing projects form the foundation:

#### OminiX-MLX — Native Rust Inference on Apple Silicon

[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) is a Rust ecosystem for high-performance ML inference on Apple Silicon, using Apple's MLX framework with Metal GPU acceleration. Its three-layer architecture — `mlx-rs` (Rust bindings to MLX), `mlx-rs-core` (shared inference infrastructure), and model-specific crates — already supports:

- **LLM**: Qwen2/3, GLM-4, Mixtral, Mistral, MiniCPM
- **VLM**: Moxin-7B (DINOv2 + SigLIP + Mistral)
- **ASR**: FunASR Paraformer
- **TTS**: GPT-SoVITS voice cloning
- **Image Generation**: FLUX.2-klein, Z-Image

The key advantage: **zero-copy tensor passing** between models via Apple Silicon unified memory. An ASR model's output tensors can be fed directly into an LLM without serialization. This is architecturally impossible in Python-based frameworks.

#### mofa-local-llm — The HTTP Bridge

[mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) wraps OminiX-MLX behind an OpenAI-compatible HTTP API server. Built with Tokio async runtime, inference runs on a dedicated OS thread communicating through message-passing channels. It auto-detects model types from configuration files and routes to the appropriate inference engine.

Currently very early (basic Qwen2 LLM inference verified; other modalities remain untested).

### The Gap: What Nobody Has Built Yet

Here's the honest comparison:

| Capability | Ollama | LM Studio | vLLM | HuggingFace | Cherry Studio | MoFA (current) |
|---|---|---|---|---|---|---|
| LLM | Yes | Yes | Yes | Yes | Via providers | Yes |
| VLM | Yes | Yes | Yes | Yes | Preview | Limited |
| ASR | No | No | RC stage | Yes | No | Untested |
| TTS | No | No | RC stage | Yes | No | Untested |
| Image Gen | No | No | RC stage | Yes | No | Untested |
| Multi-model orchestration | No | No | Yes (Omni) | Manual | Aggregator | No |
| On-device Apple Silicon | Metal/llama.cpp | Metal+MLX | No | MPS (partial) | No | Native Rust+Metal |
| Zero-copy between models | No | No | No | No | No | Architecturally possible |
| Rust-native | No | No | No | No | No | Yes |

**The gap**: No existing tool provides a unified, on-device, multi-modal inference platform that can orchestrate LLM + VLM + ASR + TTS + image generation through a single framework with intelligent resource management and zero-copy data passing.

OminiX-MLX comes closest in terms of modality breadth on Apple Silicon, but lacks orchestration. vLLM-Omni has the most sophisticated orchestration, but is NVIDIA-only and server-oriented. HuggingFace has the broadest model coverage, but is Python-only with no built-in orchestration.

<p align="center">
  <img src="./images/ai-transforming-frameworks.jpeg" alt="How AI is Transforming Frameworks: New Opportunities" width="80%">
</p>

### Why MoFA Can Do This Better — The Honest Case

MoFA's structural advantages are real, but they are *potential*, not *proven*:

1. **Rust-native with zero-copy semantics.** When ASR output feeds into an LLM on Apple Silicon unified memory, Python frameworks must serialize and deserialize tensors. MoFA (via OminiX-MLX) can pass MLX Arrays directly — zero-copy, zero-overhead. This advantage compounds in multi-model pipelines.

2. **Framework-level orchestration, not bolted-on.** vLLM-Omni adds multi-modal support on top of an LLM serving engine. MoFA can design multi-model orchestration from the ground up — scheduling, memory management, and pipeline construction as first-class framework concepts.

3. **Pluggable backend abstraction.** MoFA's `InferenceBackend` trait (see [Idea 3](../../ideas-list.md)) is designed to be backend-agnostic. OminiX-MLX is the default macOS backend, but the same agent code should work with a CUDA backend on Linux or a future NPU backend on other hardware — without modification.

4. **Edge-first, cloud-compatible.** Most orchestrators are cloud-first (vLLM, HuggingFace Endpoints) or desktop-only (Ollama, LM Studio). MoFA aims for edge-first with cloud as a fallback — the same agent runs on a MacBook, a Raspberry Pi, or a cloud GPU, with the framework handling the differences.

5. **Agent-native, not model-serving.** Ollama, vLLM, and LM Studio are *model servers* — they serve inference. MoFA is an *agent framework* — models are tools that agents use. This means MoFA can provide agent-level abstractions: "use the best available model for this task", "fall back to a smaller model under memory pressure", "route this request to cloud if local inference is too slow."

But these are architectural bets, not delivered features. The work of proving them out is exactly what this CFP is about.

---

## 3. Call for Proposal — Give Us a Feasible Action Plan

We've laid out the questions and the landscape. Now we want to see **your plan** for how MoFA should actually solve this.

### What Your Proposal Should Include

#### A. Model Abstraction Design

Propose a concrete abstraction for how MoFA represents models:

- What does the core trait/interface look like? Show us Rust signatures, not just prose.
- How does it handle the diversity of input/output types across modalities?
- How does it handle models that span multiple modalities (e.g., omni-models)?
- How does it balance generality (easy to add new model types) with specificity (good developer experience for common model types)?

#### B. Model Integration Architecture

Propose how new models get added to MoFA:

- What does a model adapter/plugin look like? Walk through the process of adding support for a new model family.
- How do model adapters get discovered, loaded, and managed at runtime?
- How does this work with different backends (OminiX-MLX on macOS, CUDA on Linux, cloud APIs as fallback)?
- How does MoFA handle model format differences (safetensors, GGUF, PyTorch checkpoints)?

#### C. Multi-Model Pipeline Design

Propose how multiple models work together in a single agent pipeline:

- How does an agent express "I need ASR, then LLM, then TTS" as a pipeline?
- How does the framework handle data passing between models (especially zero-copy on unified memory)?
- How does scheduling work when multiple models compete for limited memory?
- What happens when a model in the pipeline fails or is unavailable?

#### D. Feasibility Validation

Show that your plan is grounded in reality:

- Pick one concrete pipeline (e.g., ASR → LLM → TTS) and sketch how it would work end-to-end in MoFA.
- Identify the hardest technical risk in your plan and propose how to mitigate it.
- Propose a phased timeline: what can be built in weeks 1-4, 5-8, 9-12?
- What existing MoFA code ([mofa](https://github.com/mofa-org/mofa), [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm), [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX)) would you build on, and what would you need to write from scratch?

### What We Value

- **Concrete over abstract.** Show us code sketches, API designs, architecture diagrams — not just bullet points of features.
- **Honest scope.** A proposal that admits "multi-backend support is a stretch goal; the core deliverable is a working ASR→LLM→TTS pipeline on Apple Silicon" is better than one that promises everything.
- **Engagement with existing work.** We want to see that you've cloned mofa-local-llm, tried OminiX-MLX, and understand what already exists before proposing what to build next.
- **Forward-thinking extensibility.** Your design should make it easy for the *next* contributor to add support for a model type that doesn't exist yet.

### How to Get Started

1. **Clone and build the stack.**
   - [mofa](https://github.com/mofa-org/mofa) — the core framework
   - [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) — the HTTP inference bridge
   - [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) — the inference engine (macOS only)
2. **Run inference.** Get a Qwen model running through mofa-local-llm. Try loading different model types in OminiX-MLX if you have Apple Silicon.
3. **Study the competition.** Install Ollama and/or LM Studio. Try vLLM if you have an NVIDIA GPU. Understand what the developer experience is like today.
4. **Read [Idea 3: Edge Model Orchestrator](../../ideas-list.md)** — it covers the scheduling and memory management aspects of multi-model orchestration.
5. **Design your abstraction.** Before writing code, sketch the trait hierarchy. Think about edge cases. Discuss your design on [Discord](https://discord.gg/hKJZzDMMm9).
6. **Write a proposal** with a feasible, phased action plan. See the [proposal template](../../proposal-template.md).

### A Note on Scope

This is a large problem space. We do not expect a single GSoC project to solve all of it. A strong proposal will **scope aggressively** — pick the most impactful slice, deliver it well, and design the abstraction so that future contributors can extend it. "Working ASR→LLM→TTS pipeline with a clean model trait that others can implement" is a better outcome than "half-finished support for every modality."

---

*MoFA is an open-source project under the MIT/Apache-2.0 license.*
*Organization contact: dev@mofa.ai | Discord: https://discord.gg/hKJZzDMMm9*
