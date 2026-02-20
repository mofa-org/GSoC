# MoFA GSoC 2026 Project Ideas

> [中文版](./ideas-list-zh.md) |  English Version

This list contains detailed project ideas for Google Summer of Code 2026. While the overall outline is defined, internal details are open to modifications based on contributor suggestions under mentor guidance. We encourage contributors to propose their own approaches — the ideas below are starting points, not rigid specifications.

## About MoFA

[MoFA](https://mofa.ai/) (**Modular Framework for Agents**) is an open-source framework for building AI agents. Our recent project, **MoFA Studio**, is a desktop application for creating, running, and sharing AI-powered applications — built with Rust and Makepad, with [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) for on-device ML inference on Apple Silicon.

We mentor GSoC contributors on real-world problems spanning systems engineering, AI infrastructure, and developer tools.

__Website:__ [mofa.ai](https://mofa.ai/)

__GitHub Repos:__
- Core runtime: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio application: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI components: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)
- Node ecosystem: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

__Organization Contact:__ dev@mofa.ai
__GSoC Contributor Guidance:__ [README.md](./README.md)

---

## Idea 1: AgentForge — Composable Plugin System for Collaborative AI Development

### Abstract

In the age of vibe coding, individual developers can generate agent code rapidly with LLMs. However, **merging outputs from multiple vibe coders into a coherent system remains the hardest unsolved problem** — human review bandwidth is the bottleneck, not code generation speed.

**AgentForge** addresses this by building a composable plugin system for mofa-rs, where each developer independently creates a self-contained agent plugin with well-defined interfaces. The framework handles composition, validation, and conflict detection — enabling team-scale vibe coding without merge hell.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### Goals & Ideas

* **Plugin Interface Specification**: Define a clear contract for mofa-rs plugins — input types, output types, state schema, and lifecycle hooks. Each plugin is a self-contained unit that can be developed, tested, and vibe-coded independently
* **Validation Tooling**: Build tools that verify plugin interface compatibility before composition — type checking, schema validation, and conflict detection between plugins
* **Composition Engine**: Automatically wire multiple plugins together based on their interface declarations. Handle routing, data transformation, and error propagation across plugin boundaries
* **Plugin Isolation**: Ensure one plugin's failure doesn't crash others. Sandbox runtime state so plugins can be hot-swapped during development
* **Integration with Studio**: Generated plugin compositions can be loaded and run inside MoFA Studio

Contributors are also encouraged to explore alternative or complementary approaches, such as:

* **Semantic Node Search**: Index [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub) (400+ nodes) with vector embeddings to assist plugin discovery and composition
* **Flow Synthesis**: Convert natural language descriptions to executable plugin compositions
* **Makepad UI Generation**: Auto-generate UI for plugin configurations and outputs

#### Example Scenario

Three developers each vibe code an agent component:
- Developer A: a web scraping agent plugin
- Developer B: a summarization agent plugin
- Developer C: a notification agent plugin

AgentForge validates their interfaces are compatible, composes them into a pipeline, and runs the combined system — without any of the three developers reading each other's code.

#### Refs

* https://github.com/mofa-org/mofa/tree/main
* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa-node-hub
* https://makepad.dev/

__Skills Required__: Rust, plugin architecture design, type systems, LLM integration

__Time Estimate__: 120 hours (10 weeks)

__Difficulty__: Hard

---

## Idea 2: Studio Observability Dashboard

### Abstract

MoFA Studio runs complex AI pipelines involving multiple models (ASR, LLM, TTS) and agent interactions. Currently, when something goes wrong or runs slowly, developers have limited visibility into what's happening inside. This project will build a **real-time observability dashboard** embedded directly into MoFA Studio, providing developers with instant insight into model performance, resource usage, and agent behavior.

The dashboard will leverage MoFA Studio's existing [makepad-chart](https://github.com/mofa-org/makepad-chart) and [makepad-d3](https://github.com/mofa-org/makepad-d3) GPU-accelerated visualization components.

__Mentors__: BH3GEI (Yao Li), Bicheng Lou

### Goals & Ideas

* **Dashboard Server Development**:
  - Build HTTP server (using axum or similar) exposing REST APIs for metrics
  - Implement WebSocket endpoint for real-time streaming updates
  - Design efficient metrics aggregation and caching

* **API Design & Implementation**:
  - `/api/agents` — list all agents with status
  - `/api/agents/{id}` — detailed agent metrics
  - `/api/metrics` — system-wide metrics snapshot (model states, memory, latency)
  - WebSocket `/ws` — real-time event stream

* **Model & Inference Monitoring**:
  - Which models are currently loaded in memory and their sizes
  - Per-model inference metrics: tokens/s, time-to-first-token, batch utilization
  - Apple Silicon unified memory usage and pressure
  - Model load/unload events and durations

* **Pipeline Monitoring**:
  - End-to-end latency for multi-model pipelines (e.g., ASR → LLM → TTS)
  - Per-stage latency breakdown and bottleneck identification
  - Request queue depth and throughput

* **Studio Integration**:
  - Makepad-based real-time visualization panels using [makepad-chart](https://github.com/mofa-org/makepad-chart) and [makepad-d3](https://github.com/mofa-org/makepad-d3)
  - Agent status display (running, paused, error states)
  - Resource usage dashboard with time-series charts
  - Log aggregation with intelligent filtering

Contributors may also explore monitoring Dora-based dataflow runtimes if applicable, providing a unified monitoring interface across different orchestration backends.

#### Refs

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__Skills Required__: Rust, HTTP/WebSocket servers (axum/tokio), real-time data visualization, Makepad UI

__Time Estimate__: 90 hours (8 weeks)

__Difficulty__: Medium

---

## Idea 3: Edge Model Orchestrator

### Abstract

On edge devices, multiple models (ASR, LLM, TTS, embedding) compete for limited memory and compute. This project implements an intelligent **Model Scheduler** built into mofa-rs, enabling efficient multi-model orchestration on Apple Silicon devices.

Unlike traditional approaches that communicate with model servers over HTTP (e.g., Ollama), this orchestrator calls [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) model crates **directly at the Rust API level** — `load_model()`, `Generate`, `forward()` — with compile-time binding and zero serialization overhead. This unlocks a key advantage of Apple Silicon's unified memory: **output tensors from one model (e.g., ASR) can be passed directly to another model (e.g., LLM) as zero-copy MLX Arrays**, eliminating the serialization-deserialization overhead inherent in HTTP-based or cross-process architectures.

An existing prototype, [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm), already demonstrates single-model inference via this approach. This project extends it to multi-model concurrent scheduling.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

### Goals & Ideas

* **Architecture Design**:
  - Implement as a core component in mofa-rs (`mofa-foundation` layer)
  - Call OminiX-MLX crates directly via Rust API (compile-time dependency, no HTTP middle layer)
  - Design `ModelPool` managing multiple loaded model instances concurrently

* **Lifecycle Management**:
  - On-demand model loading with async initialization
  - Idle timeout-based automatic unloading (LRU eviction)
  - Memory pressure monitoring on Apple Silicon unified memory
  - Graceful shutdown with state preservation

* **Smart Scheduling**:
  - Route requests to the right model based on task type (ASR/LLM/TTS) and availability
  - Memory-aware admission control: reject or defer requests when memory is constrained
  - Dynamic precision degradation (e.g., auto-switch from 8-bit to 4-bit quantization under pressure)

* **Inference Pipeline**:
  - Chain multiple models into a pipeline (ASR → LLM → TTS) with zero-copy tensor passing via MLX Arrays
  - Streaming token output from LLM directly into TTS input
  - Per-stage latency tracking and bottleneck reporting

* **Degradation Strategies**:
  - Auto-fallback to smaller models when primary models fail or resources are constrained
  - Quality-of-service levels with corresponding model selections

* **Integration**:
  - Expose scheduling state and metrics to the Studio observability dashboard (Idea 2)
  - Provide clean API for agents to request inference without managing model lifecycle

#### Example Scenario

A voice assistant pipeline with:
- FunASR (ASR, ~2GB)
- Qwen (LLM, ~8GB)
- GPT-SoVITS (TTS, ~4GB)

On a 16GB MacBook, all three cannot be resident simultaneously. The orchestrator will:
- Keep LLM resident (core functionality)
- Load ASR on voice input, unload after 30s idle
- Load TTS only during synthesis, pass LLM output tokens directly as MLX Arrays (zero-copy)
- Under memory pressure, auto-switch Qwen from 8-bit to 4-bit quantization

#### Refs

* https://github.com/mofa-org/mofa-local-llm
* https://github.com/OminiX-ai/OminiX-MLX
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__Skills Required__: Rust, systems programming, resource management, Apple Silicon / GPU computing

__Time Estimate__: 140 hours (11 weeks)

__Difficulty__: Hard

---

## Idea 4: Session Recorder & Visual Debugger

### Abstract

Multi-agent systems are notoriously difficult to debug. When agents exchange dozens of messages and state changes, traditional logs become unreadable. This is especially true in the era of vibe coding, where LLM-generated agent code often works in demo but fails in production with no clear explanation.

This project builds a **time-travel debugger** for MoFA — a differentiating capability that gives developers a reason to run their agents on mofa-rs. Think of it as "Chrome DevTools for Agents": load any agent (hand-written or vibe-coded), record its execution, inspect message flow, and replay with modifications.

Building this debugger will also serve as an **architectural audit** for mofa-rs — the process of adding instrumentation hooks will force the framework to define clear internal APIs for event capture, state snapshots, and message interception.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

### Goals & Ideas

* **Event Interception**:
  - Hook into `mofa-kernel` message bus to capture all agent events
  - Serialize message flow, state transitions, and tool calls
  - Efficient storage format for long-running sessions
  - Define a clear, stable Hook API that becomes part of mofa-rs's public contract

* **Timeline Visualization**:
  - Makepad-integrated or web-based timeline view
  - See which agent sent what message to whom, when
  - Filter by agent, message type, or time range
  - Zoom in/out from millisecond to hour scale

* **State Inspection**:
  - Capture agent state snapshots at key points
  - Diff view: compare agent state before/after message handling
  - Inspect memory, context, and internal variables

* **Time-Travel Debugging**:
  - Replay recorded sessions at variable speed
  - Pause, step forward/backward through execution
  - Set breakpoints on specific message patterns
  - Re-run specific agent with modified input

* **Vibe Coding Support**:
  - Load and debug agents generated by LLMs without modification
  - Identify common failure patterns in vibe-coded agents
  - Export recordings for bug reports or as context for LLM-assisted fixing

* **Integration**:
  - Optional Studio panel for seamless development workflow
  - Export recordings for bug reports or documentation

#### Use Case

A developer vibe-codes a 5-agent workflow. It works in simple tests but fails intermittently with real data. With the recorder:
1. Load the vibe-coded agents into mofa-rs with recording enabled
2. When failure occurs, open the trace
3. See exact message sequence leading to error
4. Inspect agent state at last known good point
5. Replay with modifications to test fixes
6. Export the trace as context for LLM to generate a fix

#### Refs

* https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring

__Skills Required__: Rust, data visualization, systems design, debugging tools

__Time Estimate__: 140 hours (11 weeks)

__Difficulty__: Hard

---

## Idea 5: MoFA Input — Inference Stack Migration to OminiX-MLX

### Abstract

[MoFA Input](https://github.com/mofa-org/mofa-input) is a macOS global voice input method that runs entirely on-device. It currently uses llama.cpp with GGUF models for ASR (Whisper) and LLM (Qwen) inference. This project migrates the inference stack to [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX), replacing the llama.cpp backend with native Rust inference optimized for Apple Silicon.

Why migrate? MLX's Metal GPU acceleration is faster than llama.cpp on Apple Silicon, unified memory cuts overhead, and the rest of the MoFA ecosystem (Studio, mofa-local-llm) already uses OminiX-MLX.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### Goals & Ideas

* **ASR Migration**: Replace the current llama.cpp-based Whisper ASR with OminiX-MLX's `funasr-mlx` or `funasr-nano-mlx` crate. Validate accuracy and latency against the current implementation
* **LLM Migration**: Replace Qwen GGUF inference with OminiX-MLX's `qwen3-mlx` crate (safetensors format). Ensure streaming token output works with the existing UI
* **Swift-Rust FFI**: Adapt the existing Swift ↔ Rust FFI bridge to call OminiX-MLX APIs instead of llama.cpp. Maintain the current macOS input method architecture (Fn hotkey, floating bubble, history window)
* **Performance Benchmarking**: Compare latency, memory usage, and accuracy before and after migration on representative hardware (M1/M2/M3/M4)
* **Model Management**: Integrate with `~/.mofa/models/` model storage and leverage OminiX-MLX's safetensors format exclusively

#### Refs

* https://github.com/mofa-org/mofa-input
* https://github.com/OminiX-ai/OminiX-MLX

__Skills Required__: Rust, Swift, FFI/interop, Apple Silicon development

__Time Estimate__: 90 hours (8 weeks)

__Difficulty__: Easy

---

## Idea 6: Makepad AI Application Toolkit

### Abstract

MoFA's desktop applications (Studio, moly-ai) are built with [Makepad](https://makepad.dev/), a GPU-accelerated UI framework in Rust. While the organization has built foundational Makepad components ([makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-element](https://github.com/mofa-org/makepad-element)), there is currently no **reusable component library specifically designed for AI applications**.

This project builds a `makepad-ai-toolkit` — a set of polished, reusable Makepad widgets tailored for AI chat interfaces, model management, and inference visualization. These components will be immediately usable by MoFA Studio and any future Makepad-based AI application.

__Mentors__: BH3GEI (Yao Li), Bicheng Lou

### Goals & Ideas

* **Chat Interface Components**:
  - Chat bubble widget with support for user/assistant/system roles
  - Streaming text renderer (tokens appearing in real-time)
  - Markdown rendering within chat messages (code blocks, lists, headers)
  - Code syntax highlighting

* **Audio & Voice Components**:
  - Audio waveform visualizer (for ASR input / TTS output)
  - Recording indicator with real-time amplitude display
  - Audio playback controls with seek bar

* **Model Management UI**:
  - Model selector dropdown with model metadata (size, type, quantization)
  - Download progress indicator
  - Model status badges (loaded, unloading, error)

* **Inference Visualization**:
  - Token-per-second counter and latency display
  - Memory usage gauge (unified memory on Apple Silicon)
  - Inference progress indicator (prefill vs decode phases)

* **Integration**:
  - Package as a standalone Makepad crate (`makepad-ai-toolkit`) publishable on crates.io
  - Provide example applications demonstrating each component
  - Documentation with usage patterns for common AI application layouts

#### Refs

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/makepad-element
* https://makepad.dev/

__Skills Required__: Rust, UI/UX design, Makepad framework

__Time Estimate__: 90 hours (8 weeks)

__Difficulty__: Medium
