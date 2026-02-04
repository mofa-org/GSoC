# MoFA GSoC 2025 Project Ideas

> [中文版](./ideas-list-zh.md) | English Version

This list contains detailed project ideas for Google Summer of Code 2025. While the overall outline is defined, internal details are open to modifications based on contributor suggestions under mentor guidance.

## About MoFA

[MoFA](https://mofa.ai/) (**Modular Framework for Agents**) is an open-source framework for building AI agents. Our flagship product, **MoFA Studio**, is a desktop application for creating, running, and sharing AI-powered applications — built with Rust and Makepad.

We are excited to mentor GSoC contributors on challenging, real-world problems at the intersection of systems engineering, AI infrastructure, and developer tools.

__Website:__ [mofa.ai](https://mofa.ai/)

__GitHub Repos:__
- Core runtime: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa) (`feature/mofa-rs` branch)
- Studio application: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Node ecosystem: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

__Organization Contact:__ dev@mofa.ai
__GSoC Contributor Guidance:__ [README.md](./README.md)

---

## Idea 1: AppGen — The App Generator

### Abstract

MoFA Studio currently hosts 8+ built-in apps and supports WebView plugins. However, creating new apps requires manual coding. **AppGen** will be a built-in Studio app that allows users to generate personalized applications from natural language descriptions.

Users describe what they want (e.g., "a tool that fetches weather and generates a daily report"), and AppGen will intelligently select from [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub) (400+ nodes), compose workflows, and generate a working Studio app with Makepad UI automatically.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### Goals & Ideas

* **Semantic Node Search**: Index [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub) (400+ nodes) with vector embeddings; retrieve relevant components from natural language queries
* **Flow Synthesis**: Convert high-level descriptions to executable dataflows using mofa-rs runtime
* **Makepad UI Generation**: Generate intuitive Makepad-based interfaces from data schemas; support form-based, chat-based, and dashboard-based layouts
* **Self-Integration**: Generated apps can be automatically embedded into Studio as WebView plugins or native Rust apps
* **Customization**: Allow visual refinement of UI and logic after initial generation
* **Export & Share**: Package generated apps for distribution or sharing

#### Refs

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa-node-hub
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs
* https://makepad.dev/

__Skills Required__: Rust, Makepad UI, LLM integration, natural language processing

__Time Estimate__: 120 hours (10 weeks)

__Difficulty__: Hard

---

## Idea 2: Studio Observability Dashboard

### Abstract

MoFA-rs includes a monitoring foundation with metrics collection capabilities. This project will build a **complete Dashboard server** with REST APIs and WebSocket support, and integrate these capabilities directly into MoFA Studio, providing real-time visibility into agent execution.

The current `mofa-monitoring` crate has metrics collection; this project will extend it with a production-ready HTTP/WebSocket server and Studio-side visualization.

__Mentors__: BH3GEI (Yao Li), Bicheng Lou

### Goals & Ideas

* **Dashboard Server Development**:
  - Build HTTP server (using axum or similar) exposing REST APIs for metrics
  - Implement WebSocket endpoint for real-time streaming updates
  - Design efficient metrics aggregation and caching

* **API Design & Implementation**:
  - `/api/agents` — list all agents with status
  - `/api/agents/{id}` — detailed agent metrics
  - `/api/metrics` — system-wide metrics snapshot
  - `/api/flows` — dataflow execution status
  - WebSocket `/ws` — real-time event stream

* **Studio Integration**:
  - Makepad-based real-time visualization panels
  - Agent status display (running, paused, error states)
  - Message flow visualization with call chain tracing
  - Resource usage dashboard (CPU, memory, model loading)
  - Log aggregation with intelligent filtering

* **Hybrid Runtime Support**:
  - Support both Dora-based (current) and mofa-rs-native runtimes
  - Unified interface for monitoring across backends

#### Refs

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-monitoring
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-runtime

__Skills Required__: Rust, HTTP/WebSocket servers (axum/tokio), real-time data visualization, Makepad UI

__Time Estimate__: 90 hours (8 weeks)

__Difficulty__: Medium

---

## Idea 3: Edge Model Orchestrator

### Abstract

Edge devices running AI applications face a unique challenge: multiple models (ASR, LLM, TTS, embedding) compete for limited memory and GPU resources. This project implements an intelligent **Model Lifecycle Manager** as a core component of the `mofa-foundation` layer, enabling efficient multi-model orchestration at the edge.

The orchestrator will be integrated with mofa-rs runtime, serving as a foundational service that manages model loading, scheduling, and resource allocation.

__Mentors__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

### Goals & Ideas

* **Architecture Design**:
  - Implement as a service component in `mofa-foundation` layer (above `mofa-runtime`, below business logic)
  - Design clean API for `mofa-runtime` to invoke orchestration services
  - Support pluggable backends (Ollama, llama.cpp, custom model servers)

* **Lifecycle Management**:
  - On-demand model loading with async initialization
  - Idle timeout-based automatic unloading
  - Memory pressure monitoring and proactive management
  - Graceful shutdown with state preservation

* **Smart Scheduling**:
  - Route requests to optimal models based on task type (ASR/LLM/TTS), latency requirements, and availability
  - Support model parallelism and batching where applicable
  - Priority-based preemptive scheduling

* **Resource Management**:
  - Enforce memory/GPU quotas with graceful preemption
  - Model swapping strategies (LRU, priority-based, predictive)
  - Resource usage tracking and reporting to monitoring system

* **Degradation Strategies**:
  - Auto-fallback to smaller models when primary models fail or resources are constrained
  - Quality-of-service levels with corresponding model selections
  - Circuit breaker pattern for unreliable model services

* **Integration**:
  - Seamless integration with existing `mofa-foundation/llm` provider system
  - Expose orchestration decisions to Studio observability dashboard

#### Example Scenario

A voice assistant pipeline with:
- Whisper (ASR, 2GB VRAM)
- Qwen (LLM, 8GB VRAM)
- GPT-SoVITS (TTS, 4GB VRAM)

Total exceeds available memory. The orchestrator will:
- Keep LLM resident (core functionality)
- Load ASR on voice input, unload after 30s idle
- Load TTS only during synthesis
- Fallback to smaller models if loading fails

#### Refs

* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-runtime
* https://github.com/ollama/ollama

__Skills Required__: Rust, systems programming, resource management, GPU/edge computing

__Time Estimate__: 140 hours (11 weeks)

__Difficulty__: Hard
