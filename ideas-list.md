# MoFA GSoC 2026 Project Ideas

> English Version

This list contains detailed project ideas for Google Summer of Code 2026. While the overall outline is defined, internal details are open to modifications based on contributor suggestions under mentor guidance. We encourage contributors to propose their own approaches — the ideas below are starting points, not rigid specifications.

> **Before You Start**: Comment on the relevant GitHub issue to express interest and briefly describe your approach. **Wait for a maintainer to assign you before writing code.** This prevents duplicate work. See [Contributing Workflow](./README.md#contributing-before-gsoc) for details.
>
> **Proposal quality baseline**: Your proposal must include an architecture blueprint (component boundaries, interface contracts, data flow, failure/recovery strategy, and test plan). Evaluation is based on quality and depth, not quantity.

## Quick Reference: Ideas and Repositories

### Core Ideas — Framework & Infrastructure

These are our mainline priorities: the core agent framework, ML orchestration, and developer tooling.

| Idea                           | Tags                                          | Primary Repository                                                       | Other Repos Involved                                                                                                |
| ------------------------------ | --------------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| 1. AgentForge                  | `Rust` `Systems Design` `Plugin Architecture` | [mofa](https://github.com/mofa-org/mofa) (mofa-kernel, mofa-foundation)  | [mofa-studio](https://github.com/mofa-org/mofa-studio)                                                              |
| 3. Unified Inference Orchestrator | `Rust` `Systems Programming` `Local + Cloud Inference` | [mofa](https://github.com/mofa-org/mofa) (mofa-foundation, mofa-runtime) | [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm), [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) |
| 4. Session Recorder & Debugger | `Rust` `Systems Design` `Data Visualization`  | [mofa](https://github.com/mofa-org/mofa) (mofa-kernel, mofa-monitoring)  | [mofa-studio](https://github.com/mofa-org/mofa-studio)                                                              |

### Community Ideas — UI & Applications

These are valuable projects with a focus on frontend, product applications, and platform integration. They are not on the critical path but are welcome if you have strong interest in these areas.

| Idea                       | Tags                                              | Primary Repository                                     | Other Repos Involved                                                                                                                                                               |
| -------------------------- | ------------------------------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2. Observability Dashboard | `Rust` `Makepad UI` `HTTP/WebSocket`              | [mofa-studio](https://github.com/mofa-org/mofa-studio) | [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [mofa](https://github.com/mofa-org/mofa) (mofa-monitoring)       |
| 5. MoFA Input Migration    | `Rust` `macOS` `C++/Rust Interop` `Apple Silicon` | [mofa-input](https://github.com/mofa-org/mofa-input)   | [mofa](https://github.com/mofa-org/mofa) (inference layer, see Idea 3), [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX)                                                      |
| 6. Makepad AI Toolkit      | `Rust` `Makepad UI` `Component Design`            | New repo: `makepad-ai-toolkit`                         | [mofa-studio](https://github.com/mofa-org/mofa-studio), [makepad-element](https://github.com/mofa-org/makepad-element), [makepad-chart](https://github.com/mofa-org/makepad-chart) |

## CFP Index (English Only)

- Framework & Infrastructure Track: [MoFA, an AI Native Framework for Agent](./ideas/framework-for-ai/call-for-proposal.md)
- Model Orchestration Track: [MoFA Agents: Support All Models](./ideas/mofa-agents/call-for-proposal.md)
- Human-Computer Interaction Track: [MoFA's HCI for AI Native Agent Framework](./ideas/studio-for-ai/call-for-proposal.md)
- Critical Analysis Track: [Why MoFA](./ideas/why-mofa/call-for-proposal.md)

---

## Open Tasks — Start Contributing Here

These are concrete, self-contained tasks across the MoFA codebase. They are a good way to get familiar with the project before or during GSoC. **Comment on the relevant issue to claim one** — see [issue assignment rules](./README.md#how-we-select-contributors).

| #   | Task | Repository |
| --- | --- | --- |
| 1   | Implement or improve framework runtime (Dora / WASM / Tokio) | [mofa](https://github.com/mofa-org/mofa) |
| 2   | `mofa-ffi`: multi-language SDK bindings | [mofa](https://github.com/mofa-org/mofa) |
| 3   | Implement or improve message bus, event-driven & message-driven architecture | [mofa](https://github.com/mofa-org/mofa) |
| 4   | Improve graph-based workflow engine and DSL | [mofa](https://github.com/mofa-org/mofa) |
| 5   | `mofa-monitoring` development | [mofa](https://github.com/mofa-org/mofa) |
| 6   | `mofa-cli` — flesh out subcommands | [mofa](https://github.com/mofa-org/mofa) |
| 7   | Implement Codex-style context compression | [mofa](https://github.com/mofa-org/mofa) |
| 8   | Implement classic [agentic design patterns](https://github.com/xindoo/agentic-design-patterns) using MoFA, and iterate on the framework | [mofa](https://github.com/mofa-org/mofa) |
| 9   | Enrich built-in tools and skills | [mofa](https://github.com/mofa-org/mofa) |
| 10  | Add RAG and vector database integration | [mofa](https://github.com/mofa-org/mofa) |
| 11  | Integrate [socketioxide](https://github.com/Totodore/socketioxide), AWS S3 SDK | [mofa](https://github.com/mofa-org/mofa) |
| 12  | Implement framework-level control plane + gateway | [mofa](https://github.com/mofa-org/mofa) |
| 13  | Integrate [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) into mofa core as the built-in local inference module | [mofa](https://github.com/mofa-org/mofa), [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) |
| 14  | Linux inference backend adaptation for mofa-local-llm (Rust, see Idea 3) | [mofa](https://github.com/mofa-org/mofa) |
| 15  | Refactor MoFA Studio's Dora dataflow dependency using mofa-rs native runtime | [mofa-studio](https://github.com/mofa-org/mofa-studio), [mofa](https://github.com/mofa-org/mofa) |
| 16  | Cron-based periodic Agent execution, designed for high concurrency and massive message notification scenarios | [mofa](https://github.com/mofa-org/mofa) |
| 17  | Human-in-the-loop: pause at any node for manual review | [mofa](https://github.com/mofa-org/mofa) |
| 18  | Support visual debugging | [mofa](https://github.com/mofa-org/mofa) |
| 19  | MessageGraph implementation | [mofa](https://github.com/mofa-org/mofa) |
| 20  | Gap analysis: identify and implement missing capabilities for agent platform scenarios by benchmarking against other agent frameworks | [mofa](https://github.com/mofa-org/mofa) |
| 21  | Integrate TTS and ASR services from **2–3 cloud vendors**, while strictly adhering to the **design principles of microkernel architecture**. | [mofa](https://github.com/mofa-org/mofa) |
| 22  | Establishing a Framework-Level Agent with End-to-End Voice Integration (ASR → LLM → TTS) | [mofa](https://github.com/mofa-org/mofa) |
| 23  | Security Governance (PII Redaction, Content Moderation, Tool Permission Sandbox) | [mofa](https://github.com/mofa-org/mofa) |
| 24  | Complete `mofa-cli` subcommand implementations — `agent logs`, `plugin install/uninstall`, plugin repository integration (currently stub commands) | [mofa](https://github.com/mofa-org/mofa) |
| 25  | Implement OpenAI/Anthropic-compatible API Gateway — `/v1/chat/completions` endpoint, multi-backend load balancing, rate limiting, request routing | [mofa](https://github.com/mofa-org/mofa) |
| 26  | Implement production-grade observability — Prometheus metrics, OpenTelemetry tracing, structured logging, alerting rules | [mofa](https://github.com/mofa-org/mofa) |
| 27  | Implement complete RAG Pipeline — Document loading, chunking, embedding, vector storage (Qdrant), retrieval with full workflow | [mofa](https://github.com/mofa-org/mofa) |
| 28  | Implement Agent testing framework — Unit testing, integration testing, Mock tools, standard test utilities for Agent development | [mofa](https://github.com/mofa-org/mofa) |
| 29  | Agent state persistence and recovery — Checkpoint/restore Agent execution state for fault tolerance and resumption | [mofa](https://github.com/mofa-org/mofa) |
| 30  | Streaming response optimization — Unified abstraction for SSE/WebSocket streaming across LLM providers | [mofa](https://github.com/mofa-org/mofa) |
| 31  | Error handling and retry mechanisms — Fault tolerance, retry strategies, graceful degradation for Agent execution | [mofa](https://github.com/mofa-org/mofa) |
| 32  | Enhanced plugin hot-reloading — Runtime plugin dynamic loading/unloading/updating without framework restart | [mofa](https://github.com/mofa-org/mofa) |
| 33  | Agent performance benchmarking — Standardized performance test suite and benchmark data for Agent execution | [mofa](https://github.com/mofa-org/mofa) |
| 34  | Tool execution sandbox — Secure isolated execution environment for untrusted Tools | [mofa](https://github.com/mofa-org/mofa) |
| 35  | Multi-modal Agent capabilities — Image, audio, video input/output support for multi-modal LLMs | [mofa](https://github.com/mofa-org/mofa) | 

### Openwork Spotlight (Not a GSoC Idea): Discord Collaboration Assistant with `mofaclaw`

This is an **openwork** exploration item under the Open Tasks section. It is **not** one of the formal GSoC ideas above.

**Goal**
- Build a Discord-facing collaboration assistant (intended to gradually replace the current OpenClaw usage in group workflows) to showcase real MoFA framework capabilities.

**Proposed Scope (for now)**
- GitHub operations tools in Discord:
  - Create issues, summarize PRs, assign owners, label triage support.
- Webhook -> Discord thread mapping:
  - Route issue/PR events into stable Discord channels/threads.
- Repository knowledge Q&A:
  - Answer questions from docs/README/issues with source links.
- Daily/periodic summaries:
  - New issues, PR review queue, and blocked items.
- Duplicate detection hints:
  - Suggest potentially duplicate questions/issues before new ones are filed.
- Reliability mechanisms:
  - Retry, idempotency, queueing, and rate limiting.
- Compatibility with existing commands:
  - Keep alias compatibility for common OpenClaw commands during migration.

**Current Guardrails**
- No automatic issue close permissions in this openwork scope.
- No audit log module in this phase.
- No observability dashboard requirement in this phase.

We apologize that the project is undergoing significant changes and we have not yet had time to break these down into well-labeled issues. We will gradually create `good first issue` labels based on these tasks and other smaller issues that arise as the project evolves. If you are unsure where to start, ask in [Discord](https://discord.gg/hKJZzDMMm9).



While AI coding can rapidly implement simple functionalities, for a framework, mere implementation is insufficient—practical applicability and productivity must be considered. We aim for every feature to meet enterprise‑grade delivery standards. AI cannot judge whether a feature aligns with the framework’s philosophy, and this is precisely where the value of a programmer shines. As a "programmer‑magician" who weaves code with AI, you infuse the framework with soul through unique insight and experience. Therefore, we expect each PR to be validated in real‑world practice, ensuring it genuinely delivers value and serves a tangible purpose. We recommend seeking authentic use‑case scenarios under examples/to verify and iteratively refine our framework, making it more robust and well‑rounded.

---

## About MoFA

[MoFA](https://mofa.ai/) (**Modular Framework for Agents**) is an open-source framework for building AI agents. Our recent project, **MoFA Studio**, is a desktop application for creating, running, and sharing AI-powered applications — built with Rust and Makepad, with [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) for on-device ML inference on Apple Silicon.

We mentor GSoC contributors on real-world problems spanning systems engineering, AI infrastructure, and developer tools.

__Website:__ [mofa.ai](https://mofa.ai/)

__GitHub Repos:__

- Core runtime: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio application: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI components: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)

__Organization Contact:__ dev@mofa.ai
__GSoC Contributor Guidance:__ [README.md](./README.md)

---

## Idea 1: AgentForge — Composable Plugin System for Collaborative AI Development

### Abstract

In the age of vibe coding, individual developers can generate agent code rapidly with LLMs. However, **merging outputs from multiple vibe coders into a coherent system remains the hardest unsolved problem** — human review bandwidth is the bottleneck, not code generation speed.

**AgentForge** addresses this as a runtime-native capability in mofa-rs: Layer 1 uses AI to generate contract-first micro-modules, and Layer 2 lets a higher-level agent or a human control composition and system-level decisions. The framework handles validation, conflict detection, auditability, and rollback — enabling team-scale vibe coding without merge hell.

__Mentors__: BH3GEI (Yao Li), lijingrs (AmosLi)

### Goals & Ideas

* **Two-Layer Collaboration Model**:
  
  - **Layer 1 (AI-generated micro-modules)**: Generate small, self-contained modules under strict contracts (input/output schemas, dependencies, tests, risk tags)
  - **Layer 2 (composition & system control)**: A higher-level agent or human reviewer controls architecture-level composition, quality gates, merge/reject decisions, and rollback

* **Runtime-Native Vibe Flow**:
  
  - Integrate vibe task lifecycle directly into `mofa-runtime` (plan -> generate -> validate -> gate -> merge/rollback)
  - Treat outputs as verifiable artifacts (patch/test/report), not free-form text only
  - Keep the same control model available through CLI/runtime APIs; UI is optional, not the core deliverable

* **Plugin Contract**: Define a stable `PluginManifest` with JSON Schema contracts for plugin inputs/outputs, state schema, and lifecycle hooks
* **Compatibility Validation**: Provide a `validate` command to check contract compatibility, schema/type mismatch, and composition safety before runtime
* **Composition Executor**: Implement DAG-based plugin orchestration and execution with integration tests
* **Runtime Isolation**: Use Wasm sandboxing as the default isolation boundary for plugins

### MVP

- Land `PluginManifest` and JSON Schema contracts in the main `mofa` repo
- Define the Layer 1 micro-module contract (I/O schema, dependency metadata, test/risk metadata)
- Implement `validate` command for compatibility checks
- Deliver one Layer 2 controller path (higher-level agent or human-driven) for composition decisions and quality gates
- Deliver one end-to-end runtime flow: `intent -> micro-modules -> composition -> gate -> merge/rollback`
- Build a DAG-based composition executor for contract-driven plugin wiring
- Provide a minimal runnable plugin example under Wasm sandbox
- Provide 3 collaboration scenarios (parallel edits on one module, cross-module dependency composition, rollback after failing gates)
- Add integration tests for composition and failure paths

### Stretch Goals

- Semantic node search over `mofa-node-hub`
- Natural-language-to-flow synthesis
- Auto-generated UI for plugin configuration/output

### Out of Scope

- Full no-code workflow generator as primary deliverable
- Production-grade plugin marketplace/distribution system
- IDE product features or large Studio UI surfaces as primary deliverables
- Prompt-only vibe demos without verifiable patch/test/report artifacts

### Acceptance Criteria

- `validate` catches contract incompatibility before execution
- Layer 1 outputs can be composed through Layer 2 control with explicit gate decisions (merge/reject/rollback)
- At least one composition conflict and one rollback path are covered in tests
- All stages emit auditable records for reproduction (inputs, gate decisions, outputs)
- The same flow supports Layer 2 control by either a higher-level agent or a human reviewer
- 3 example collaboration scenarios run end-to-end in CI
- Plugin composition code and tests are merged in the main `mofa` repo

### Repo Landing Plan

- **Main landing repo**: `mofa` (`mofa-kernel` / `mofa-foundation`)
- **Optional demo integration**: `mofa-studio`

#### Example Scenario

Three developers each vibe code an agent component:

- Developer A: a web scraping agent plugin
- Developer B: a summarization agent plugin
- Developer C: a notification agent plugin

AgentForge validates their interfaces are compatible, composes them into a pipeline, and runs the combined system — without any of the three developers reading each other's code.

#### Refs

* https://github.com/mofa-org/mofa/tree/main

* https://github.com/mofa-org/mofa-studio

* https://makepad.dev/

__Skills Required__: Rust, plugin architecture design, type systems, LLM integration

__Time Estimate__: 175 hours (medium project size)

__Difficulty__: Hard

---

## Idea 2: Studio Observability Dashboard

### Abstract

MoFA Studio runs complex AI pipelines involving multiple models (ASR, LLM, TTS) and agent interactions. Currently, when something goes wrong or runs slowly, developers have limited visibility into what's happening inside. This project will build a **real-time observability dashboard** embedded directly into MoFA Studio, providing developers with instant insight into model performance, resource usage, and agent behavior.

The dashboard will leverage MoFA Studio's existing [makepad-chart](https://github.com/mofa-org/makepad-chart) and [makepad-d3](https://github.com/mofa-org/makepad-d3) GPU-accelerated visualization components.

__Mentors__: BH3GEI (Yao Li), yangrudan (CookieYang)

### Goals & Ideas

* **Backend Metrics Service**: Build a runtime metrics service with REST + WebSocket APIs
* **Studio Panels**: Add real-time observability panels in MoFA Studio
* **Bottleneck Visibility**: Surface latency/throughput/queue/model-state signals for practical debugging

### Scope Boundary (vs Idea 4)

- Idea 2 is for online observability only
- Session replay, time-travel debugging, and breakpointing belong to Idea 4

### MVP

- Stable `/api/agents`, `/api/metrics`, and WebSocket `/ws`
- At least 4 core views in Studio: latency, throughput, queue depth, model load state
- One end-to-end scenario showing bottleneck localization
- Basic tests and reproducible setup docs

### Stretch Goals

- Unified monitoring across additional runtime backends (including Dora-based flows)
- More advanced correlation views and filtering UX

### Out of Scope

- Time-travel replay/debugger capabilities
- Full historical trace reconstruction (Idea 4 scope)

### Acceptance Criteria

- Backend metrics service and Studio panels are both delivered
- API contracts are documented and exercised in tests
- Operators can identify at least one real bottleneck from the dashboard output

### Repo Landing Plan

- **Main landing repo**: `mofa-studio` (UI + API service integration)
- **Supporting integration**: `mofa` (`mofa-monitoring` / `mofa-runtime`)

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

## Idea 3: Unified Inference Orchestrator (Local + Cloud)

### Abstract

MoFA agents should run with one inference contract across **local runtimes and cloud APIs**. This project builds a unified inference orchestration layer in mofa-rs: pluggable backends, policy-based routing, and runtime-level lifecycle/scheduling.

For local inference, MoFA should call backends directly at the Rust API level (`load_model()`, `Generate`, `forward()`) with no HTTP middle layer when possible. For cloud inference, MoFA should provide provider adapters (OpenAI-compatible API first) under the same framework abstraction.

The current macOS path with [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) is a strong local reference, especially for unified-memory zero-copy pipelines. But final deliverables must land in the main `mofa` repo and work with both local and cloud backends. [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) is a prototype/reference repo, not the final landing target.

__Mentors__: BH3GEI (Yao Li), lijingrs (AmosLi)

### Platform Scope & Hardware Access

- MoFA inference is not macOS-only. Our vision is a general, pluggable framework across macOS, Linux, and future backends.
- This idea is not local-only either. Proposal scope must include **at least one local backend path and one cloud API adapter path**.
- Project deliverables must be integrated into the mofa-rs mainline (`mofa-foundation` / `mofa-runtime`), not kept as a standalone demo.
- `mofa-local-llm` is for prototyping and experiments; production deliverables must land in the main `mofa` repo.
- Cross-platform is a core requirement: proposals should include one implemented local backend (macOS or Linux) plus a clear compatibility plan for the other platform.
- If you need specific hardware or remote servers for final validation, discuss it with mentors early.

### Delivery Boundaries (Recommended)

- **Must land in the main `mofa` repo**: backend abstractions, local/cloud routing policy, scheduler core, lifecycle management, `mofa-runtime` integration, and core tests.
- **Can remain in `mofa-local-llm`**: demo GUI, standalone demo server, and experimental scripts/prototypes.
- **Recommended flow**: validate quickly in `mofa-local-llm`, then migrate stable capabilities into the main `mofa` repo.

### Track Options

- **Core requirement (mandatory)**: one unified inference path that supports both local and cloud adapters under one API contract.
- **Implementation focus (choose one local backend for primary validation)**:
  - macOS focus: prioritize OminiX-MLX integration and unified-memory scheduling behavior
  - Linux focus: prioritize Linux backend adaptation + scheduler + benchmarking
- Cross-platform compatibility design for the non-primary platform is mandatory.

### Goals & Ideas

* **Architecture Design**:
  
  - Implement as a core component in mofa-rs (`mofa-foundation` layer)
  - Define a pluggable backend abstraction for local runtimes and cloud providers
  - Implement OminiX-MLX as the default macOS local backend and at least one OpenAI-compatible cloud adapter
  - Keep one unified request/response contract for agents, regardless of local or cloud execution
  - Design `ModelPool` (local models) and provider session management (cloud)

* **Lifecycle Management**:
  
  - On-demand model loading with async initialization
  - Idle timeout-based automatic unloading (LRU eviction)
  - Memory pressure monitoring on Apple Silicon unified memory
  - Graceful shutdown with state preservation

* **Smart Scheduling**:
  
  - Route requests to local or cloud backends based on policy (e.g., local-first, latency-first, cost-first)
  - Route requests to the right model based on task type (ASR/LLM/TTS) and availability
  - Memory-aware admission control: reject or defer requests when memory is constrained
  - Provider-aware retry/failover for cloud calls
  - Dynamic precision degradation (e.g., auto-switch from 8-bit to 4-bit quantization under pressure)

* **Inference Pipeline**:
  
  - Chain multiple models into a pipeline (ASR → LLM → TTS) with zero-copy tensor passing via MLX Arrays where local backends support it
  - Support hybrid pipelines (e.g., local ASR/TTS + cloud LLM, or local-first with cloud fallback)
  - Streaming token output from LLM directly into TTS input
  - Per-stage latency tracking and bottleneck reporting

* **Degradation Strategies**:
  
  - Auto-fallback to smaller models when primary models fail or resources are constrained
  - Quality-of-service levels with corresponding model selections

* **Integration**:
  
  - Expose scheduling state and metrics to the Studio observability dashboard (Idea 2)
  - Provide clean API for agents to request inference without managing model lifecycle

### MVP

- Land unified inference abstractions in the main `mofa` repo
- Deliver at least one local backend + one cloud API adapter under the same runtime contract
- Implement scheduler core, lifecycle management, and local/cloud routing policies with tests
- Integrate with `mofa-runtime` so agents can request inference via one unified API
- Provide reproducible benchmarks (latency, throughput, memory usage, local-vs-cloud routing behavior)

### Stretch Goals

- Multi-cloud provider support and cost-aware routing
- Dynamic precision switching policies with workload-aware tuning
- Additional backend implementations beyond the selected track

### Out of Scope

- Shipping GUI-only demos without mainline runtime integration
- Local-only designs that cannot interoperate with cloud APIs
- Platform-specific one-off hacks that bypass backend abstraction

### Acceptance Criteria

- Core orchestration code is merged into `mofa-foundation` / `mofa-runtime`
- Same agent API can run through local, cloud, and hybrid paths via configuration
- Chosen local track (macOS or Linux) has end-to-end runnable path with tests
- At least one failover scenario (local unavailable -> cloud fallback, or reverse) is tested
- Benchmarks are documented and reproducible by mentors

### Repo Landing Plan

- **Main landing repo**: `mofa` (`mofa-foundation` / `mofa-runtime`)
- **Prototype/reference repo**: `mofa-local-llm` (non-final deliverables)

#### Example Scenario

A voice assistant pipeline with:

- FunASR (ASR, ~2GB)
- Qwen (LLM, ~8GB)
- GPT-SoVITS (TTS, ~4GB)

On a 16GB MacBook, all three cannot be resident simultaneously. The orchestrator will:

- Keep local ASR/TTS active for low-latency interaction
- Route LLM to local by default, with cloud fallback when local memory pressure or latency thresholds are exceeded
- If local LLM is available, pass tensors via zero-copy local path; otherwise switch to cloud adapter without changing agent code
- Recover to local path when resources return to healthy state

#### Refs

* https://github.com/mofa-org/mofa-local-llm
* https://github.com/OminiX-ai/OminiX-MLX
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__Skills Required__: Rust, systems programming, resource management, Apple Silicon or Linux GPU computing

__Time Estimate__: 175 hours (medium project size)

__Difficulty__: Hard

---

## Idea 4: Session Recorder & Visual Debugger

### Abstract

Multi-agent systems are notoriously difficult to debug. When agents exchange dozens of messages and state changes, traditional logs become unreadable. This is especially true in the era of vibe coding, where LLM-generated agent code often works in demo but fails in production with no clear explanation.

This project builds a **time-travel debugger** for MoFA — a differentiating capability that gives developers a reason to run their agents on mofa-rs. Think of it as "Chrome DevTools for Agents": load any agent (hand-written or vibe-coded), record its execution, inspect message flow, and replay with modifications.

Building this debugger will also serve as an **architectural audit** for mofa-rs — the process of adding instrumentation hooks will force the framework to define clear internal APIs for event capture, state snapshots, and message interception.

__Mentors__: BH3GEI (Yao Li), lijingrs (AmosLi)

### Phased Delivery Plan (Required)

1. Event capture + storage + CLI replay
2. Timeline UI
3. Breakpoints + state diffing

### Schema Versioning Requirement

- Define event schema and schema versioning strategy first
- Backward/forward compatibility expectations must be documented before scaling features

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

### MVP

- Event capture hooks in `mofa-kernel`
- Durable storage format with schema versioning
- CLI replay capable of deterministic step-through for recorded sessions

### Stretch Goals

- Rich timeline UI interactions and breakpoint UX
- LLM-assisted failure pattern analysis

### Out of Scope

- UI-only trace viewer without reliable replay core
- Unversioned ad-hoc trace formats

### Acceptance Criteria

- Same input + same runtime version can replay key failure traces deterministically
- Schema versioning and migration notes are documented
- CLI replay and at least one UI path are available

### Repo Landing Plan

- **Main landing repo**: `mofa` (`mofa-kernel` / `mofa-monitoring`)
- **Optional UI integration**: `mofa-studio`

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

__Time Estimate__: 175 hours (medium project size)

__Difficulty__: Hard

---

## Idea 5: MoFA Input — Inference Stack Migration to MoFA's Native Inference Layer

### Abstract

[MoFA Input](https://github.com/mofa-org/mofa-input) is a macOS global voice input method that runs entirely on-device. It currently uses llama.cpp with GGUF models for ASR (Whisper) and LLM (Qwen) inference via a C++ interop layer. This project migrates the inference stack to MoFA's own native Rust inference layer (currently backed by [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) on macOS, see Idea 3), replacing the C++ llama.cpp backend entirely.

Why migrate? Pure Rust eliminates the C++ interop complexity, MLX's Metal GPU acceleration is faster than llama.cpp on Apple Silicon, and aligning with MoFA's pluggable inference backend (Idea 3) ensures MoFA Input benefits from any future backend improvements without additional migration work.

__Mentors__: BH3GEI (Yao Li), yangrudan (CookieYang)

### Scope Options

- **Scoped option (90h)**: ASR migration + interface layer integration
- **Full option (175h)**: ASR + LLM + full C++ to Rust migration

### Rollback Strategy (Required)

- Keep legacy path behind feature flags during migration
- If latency/accuracy regress beyond agreed thresholds, system must switch back safely

### Goals & Ideas

* **ASR Migration**: Replace the current llama.cpp-based Whisper ASR with MoFA's inference layer (e.g., `funasr-mlx` or `funasr-nano-mlx` on macOS). Validate accuracy and latency against the current implementation
* **LLM Migration**: Replace Qwen GGUF inference with MoFA's inference layer (e.g., `qwen3-mlx` on macOS, safetensors format). Ensure streaming token output works with the existing UI
* **C++→Rust Migration**: Replace the existing C++ llm_server (llama.cpp) with pure Rust inference calls via MoFA's backend abstraction (Idea 3), eliminating the C++ interop layer. Maintain the current macOS input method architecture (Fn hotkey, floating bubble, history window)
* **Performance Benchmarking**: Compare latency, memory usage, and accuracy before and after migration on representative hardware (M1/M2/M3/M4)
* **Model Management**: Integrate with `~/.mofa/models/` model storage and leverage OminiX-MLX's safetensors format exclusively

### MVP

- Complete the selected scope option with measurable benchmark report
- Add feature-flag rollback path to legacy inference stack
- Ensure compatibility with current MoFA Input interaction model

### Stretch Goals

- Complete full migration if starting from scoped option
- Broaden model compatibility and tuning presets

### Out of Scope

- Removing rollback path before production confidence
- Unmeasured migration with no before/after benchmark evidence

### Acceptance Criteria

- Migration path is functional and benchmarked on representative hardware
- Rollback path is tested and documented
- No critical regression in core user flow (voice input to text output)

### Repo Landing Plan

- **Main landing repo**: `mofa-input`
- **Shared backend dependencies**: `mofa` inference abstractions from Idea 3

#### Refs

* https://github.com/mofa-org/mofa-input
* https://github.com/OminiX-ai/OminiX-MLX

__Skills Required__: Rust, C++/Rust interop, macOS development, Apple Silicon

__Time Estimate__: 90 hours (scoped) or 175 hours (full migration)

__Difficulty__: Medium

---

## Idea 6: Makepad AI Application Toolkit

### Abstract

MoFA's desktop applications (Studio, moly-ai) are built with [Makepad](https://makepad.dev/), a GPU-accelerated UI framework in Rust. Traditional "component catalog + manual composition" workflows are not enough for AI-native products: agents can generate code quickly, but cannot reliably use generic UI libraries without a task-aware UI contract.

This project keeps the `makepad-ai-toolkit` name, but focuses on an **AI-native UI generation model**: agents generate structured UI intents/patches, the toolkit validates and renders them safely, and Studio/MoFA runtime can manage them in real time. The primary value is runtime integration and controllable generation, not building a large generic component list.

__Mentors__: BH3GEI (Yao Li), yangrudan (CookieYang)

### Goals & Ideas

* **AI-Native UI Contract**:
  
  - Define a structured schema for agent-generated UI intents and incremental UI patches
  - Support task-oriented primitives and composable layouts for agent products (not just low-level widget calls)
  - Include validation rules, versioning, and clear error reporting for invalid patches

* **Generation Runtime**:
  
  - Build a runtime path where agents can stream UI patches and Studio can apply updates in real time
  - Add safety gates for high-risk actions (approval, reject, rollback)
  - Preserve deterministic fallback to manual/static UI when generation fails

* **MoFA Integration (Primary Deliverable)**:
  
  - Integrate with `mofa-studio` so generated UI can be inspected, controlled, and updated at runtime
  - Integrate with `mofa` runtime events (agent state, tool calls, trace metadata) as first-class UI data sources
  - Keep Idea 2 (GUI orchestration) and Idea 6 decoupled: this idea provides generation/runtime capability, not orchestration product scope

* **Component Work (Limited and Purpose-Driven)**:
  
  - Add or refine base components only when required by AI-native generation flows
  - Reuse existing Makepad ecosystem work whenever possible

### MVP

- Define and document the AI-native UI generation contract (schema + patch protocol + validation rules)
- Implement one end-to-end runtime demo: `agent output -> UI patch stream -> Studio render -> user feedback -> runtime update`
- Integrate at least 2 real MoFA workflows where UI is generated/updated at runtime
- Provide guardrail behavior (approve/reject/rollback) with tests and reproducible demo steps

### Stretch Goals

- Multi-provider generation adapters and richer policy controls
- Better prompt-to-UI templates and domain presets
- Publish crate and maintain versioned changelog/release notes

### Out of Scope

- Building a large generic component catalog without AI-generation runtime value
- Re-implementing existing sibling projects (for example A2UI renderer work) from scratch
- Component gallery with no production integration

### Acceptance Criteria

- At least 2 MoFA workflows support runtime AI-generated UI updates in `mofa-studio`
- Invalid/unsafe UI patches are rejected with clear errors and safe fallback behavior
- Approve/reject/rollback paths are test-covered and reproducible
- Toolkit contract/runtime APIs are documented and reusable by contributors

### Repo Landing Plan

- **Main landing repo**: `makepad-ai-toolkit` (new repo)
- **Required production integration**: `mofa-studio`
- **Required runtime integration**: `mofa` (event/trace interfaces)

#### Refs

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/makepad-element
* https://github.com/ZhangHanDong/makepad-component
* https://makepad.dev/

__Skills Required__: Rust, UI/UX design, Makepad framework

__Time Estimate__: 90 hours (8 weeks)

__Difficulty__: Medium

---

## Optional Chinese Translation

- Ideas list: [zh/ideas-list.md](./zh/ideas-list.md)
