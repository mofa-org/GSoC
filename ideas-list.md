# MoFA GSoC 2026 Project Ideas

> English Version

This list contains detailed project ideas for Google Summer of Code 2026. While the overall outline is defined, internal details are open to modifications based on contributor suggestions under mentor guidance. We encourage contributors to propose their own approaches — the ideas below are starting points, not rigid specifications.

> **Before You Start**: Comment on the relevant GitHub issue to express interest and briefly describe your approach. **Wait for a maintainer to assign you before writing code.** This prevents duplicate work. See [Contributing Workflow](./README.md#contributing-before-gsoc) for details.
>
> **Proposal quality baseline**: Your proposal must include an architecture blueprint (component boundaries, interface contracts, data flow, failure/recovery strategy, and test plan). Evaluation is based on quality and depth, not quantity.

## Quick Reference: Ideas and Repositories

All current ideas are listed below in one table (ordered by idea number).

| Idea | Tags | Primary Repository | Other Repos Involved |
| --- | --- | --- | --- |
| 1. Cognitive Gateway | `Rust` `Gateway` `Systems Design` | [mofa](https://github.com/mofa-org/mofa) (`mofa-kernel`, `mofa-foundation`) | [mofa-studio](https://github.com/mofa-org/mofa-studio) |
| 2. Cognitive Observatory | `Rust` `Observability` `Evaluation` | [mofa-studio](https://github.com/mofa-org/mofa-studio) | [mofa](https://github.com/mofa-org/mofa) (`mofa-monitoring`), [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3) |
| 3. Cognitive Compute Mesh | `Rust` `Systems Programming` `Local + Cloud Inference` | [mofa](https://github.com/mofa-org/mofa) (`mofa-foundation`, `mofa-runtime`) | [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm), [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) |
| 4. Cognitive Workflow Engine | `Rust` `Workflow Orchestration` `DSL` | [mofa](https://github.com/mofa-org/mofa) (`mofa-kernel`, `mofa-foundation`) | [mofa-studio](https://github.com/mofa-org/mofa-studio) |
| 5. Cognitive Swarm Orchestrator | `Rust` `Multi-Agent` `HITL Governance` | [mofa](https://github.com/mofa-org/mofa) (`mofa-foundation`, `mofa-runtime`) | [mofa-studio](https://github.com/mofa-org/mofa-studio), [mofa-sdk](https://github.com/mofa-org/mofa/tree/main/crates/mofa-sdk) |

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

## Idea 1: Cognitive Gateway — Neural Interface Between AI Agents and the Physical-Digital World + Cache & Plugin Registry Ecosystem

### Reference Platform

**AgentGateway** — Linux Foundation's AI Agent gateway platform providing LLM/MCP/A2A protocol support, intelligent routing, security, and observability.

**Plano** — AI-native proxy server providing agent orchestration, model routing, filter chains, and prompt target management.

**crates.io** — Rust's official package registry with versioning, dependencies, and publishing workflow.

This project combines the above platforms and extends IoT capability abstraction, distributed cache system, and plugin registry ecosystem for physical world interaction and ecosystem extension.

### Brief Description

Build a Rust-native high-performance gateway connecting AI Agents to the digital world (LLM, MCP tools, A2A communication) and physical world (IoT devices, sensors, actuators), enabling agents to perceive and interact with the real world through semantic capability APIs. Also provides a **Distributed Cache Layer** to reduce backend calls, and **Plugin Registry Infrastructure** for capability adapter discovery and installation.

### Detailed Description

Today's AI Agents are trapped in the digital world—they can process text, generate images, call APIs, but cannot perceive or interact with the surrounding physical world. Meanwhile, traditional API gateways face fundamental challenges when handling stateful AI protocols like MCP and A2A. This project builds **Cognitive Gateway**, a unified nervous system designed from first principles for AI Agent communication.

**Architecture**:

```
┌─────────────────────────────────────────────────────────────────┐
│                        AI Agents                                 │
└─────────────────────────────────────────────────────────────────┘
                              │
                    Northbound API (REST/WebSocket)
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Cognitive Gateway                             │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  │
│  │  Router      │  │  Filter      │  │  Capability          │  │
│  │  (Routing)   │  │  Chain       │  │  Registry            │  │
│  └──────────────┘  └──────────────┘  └──────────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  │
│  │  Auth/RBAC   │  │  Rate        │  │  Event Bus           │  │
│  │  (Security)  │  │  Limiter     │  │                      │  │
│  └──────────────┘  └──────────────┘  └──────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                              │
                    Southbound Adapters
                              ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│ LLM API     │  │ MCP Server  │  │ IoT Hub     │  │ Agent-to-   │
│ (OpenAI)    │  │ (Tool Fed)  │  │ (HA/MQTT)   │  │ Agent (A2A) │
└─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘
```

**Digital World Interface** (aligned with AgentGateway + Plano):
- **LLM Gateway**: Multi-provider unified interface (OpenAI, Anthropic, Gemini), inference-aware routing, token counting and cost attribution
- **MCP Gateway**: Tool federation, OpenAPI to MCP conversion, tool discovery and registration
- **A2A Gateway**: Agent-to-Agent secure communication, capability discovery, collaboration protocols
- **Intelligent Routing**: Load balancing, circuit breaking, failover, model queue-based scheduling
- **Filter Chain**: Request/response preprocessing, content moderation, prompt injection protection
- **Security Layer**: Authentication (JWT, API Key, OAuth 2.0), authorization (RBAC + CEL expressions), audit logging

**Physical World Interface** (IoT Capability Abstraction):
- **Capability Abstraction Layer**: Semantic APIs (`speaker.tts()`, `camera.capture()`, `sensor.subscribe()`, `light.setBrightness()`)
- **Adapter Plugins**: Home Assistant, MQTT Broker, RTSP, vendor cloud APIs
- **Event Streams**: Device online/offline, state changes, motion detection, voice wake-up
- **Digital Twin**: Device simulation, scenario replay, offline testing

**Distributed Cache Layer** (New):
- **Multi-Level Cache**: L1 (in-memory) → L2 (Redis) → L3 (PostgreSQL)
- **Cache Invalidation**: TTL-based, event-driven, manual invalidation
- **Cross-Node Sync**: Cache coherence across distributed nodes
- **Cache Warming**: Preload frequently accessed LLM responses and IoT states
- **Smart Cache Keys**: Semantic similarity-based cache hits

**Plugin Registry Infrastructure** (New):
- **Plugin Registry API**: REST API for publishing, searching, downloading plugins
- **Signature Verification**: Ed25519 cryptographic signatures for plugin authenticity
- **CLI Tools**: `mofa plugin install/publish/search/verify`
- **Capability Discovery**: Schema-based plugin capability matching

### Expected Outcomes

**Phase 1: Core Framework (Weeks 1-4)**
- `mofa-gateway` crate foundation
- Routing engine: trie-based path matching, load balancing strategies
- Filter chain framework: pluggable request/response processing pipeline
- Configuration system: YAML config + hot reload support

**Phase 2: Digital World Interface (Weeks 5-10)**
- LLM Gateway: OpenAI-compatible API, multi-provider routing, token telemetry
- MCP Gateway: Tool registration, invocation proxy, OpenAPI conversion
- A2A Gateway basics: Agent discovery, secure communication
- Authentication/Authorization: JWT verification, RBAC policy engine

**Phase 3: Physical World Interface (Weeks 11-16)**
- Capability Abstraction Layer: `Capability` trait, `CapabilityRegistry`, schema versioning
- Home Assistant adapter: REST/WebSocket API integration
- MQTT adapter: subscribe/publish, device discovery
- Event Bus: pub/sub, event filtering, persistence

**Phase 4: Integration & Deployment (Weeks 17-20)**
- Control plane: REST API (`GET /capabilities`, `POST /invoke`), WebSocket event stream
- End-to-end demo: 3 scenarios (pure digital, pure physical, hybrid collaboration)
- Docker Compose deployment
- Documentation: architecture design, API reference, adapter development guide

**Phase 5: Cache & Plugin Ecosystem (Weeks 21-24)**
- L1/L2/L3 multi-level cache implementation
- Cross-node cache synchronization mechanism
- Plugin registry API with signature verification
- CLI tools: `mofa plugin install/publish/search/verify`
- Cache hit rate monitoring and optimization

### Minimum Viable Product (MVP)

Participants must deliver the following MVP before the bonding period ends:
- Running gateway service with HTTP request routing
- At least 1 LLM provider (OpenAI) routing support
- At least 1 IoT adapter (Home Assistant or MQTT)
- Basic authentication (API Key) and rate limiting
- L1 in-memory cache basic implementation
- Simple plugin registry API (CRUD operations)
- Simple command-line demo script

### Stretch Goals

- **Advanced routing**: Inference-aware routing (GPU queue depth, KV cache utilization)
- **Complete voice pipeline**: Streaming audio, continuous dialogue, interruption control
- **Observability integration**: OpenTelemetry tracing, Prometheus metrics, Grafana dashboard
- **More adapters**: Zigbee, Socket.IO, vendor cloud APIs (Xiaomi, Tuya)
- **Digital twin framework**: Device simulation, scenario replay

### Acceptance Criteria

- [ ] Agent-side code does not contain specific protocol details, only accesses services through capability APIs
- [ ] Gateway can run continuously for 24 hours without crashes, supports configuration hot reload
- [ ] At least 2 types of heterogeneous backends (LLM + IoT) work under the same capability layer
- [ ] Event/capability schema has versioning strategy, compatibility rules documented
- [ ] Unit test coverage ≥ 70%, integration tests cover core scenarios
- [ ] Reproducible deployment documentation and demo scripts
- [ ] Cache layer reduces backend calls ≥ 50% (based on benchmarks)
- [ ] Plugin installation time < 10 seconds (including signature verification)
- [ ] Cross-node cache consistency latency < 100ms

### Skills Required

- **Required**: Strong Rust programming (async/await, trait design, error handling)
- **Required**: Understanding of API gateway patterns and reverse proxy principles
- **Required**: Familiarity with HTTP/WebSocket protocols
- **Preferred**: IoT protocol experience (MQTT, Home Assistant)
- **Preferred**: Event-driven architecture and message queue experience
- **Preferred**: LLM API integration experience (OpenAI, Anthropic)

### Difficulty

**High** (350 hours)

### Getting Started

1. **Review existing code**:
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel - Microkernel core
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation - Foundation layer

2. **Study reference platforms**:
   - https://github.com/agentgateway/agentgateway - AgentGateway (Linux Foundation)
   - https://github.com/plano-ai/plano - Plano AI-native proxy server

3. **Complete micro-tasks**:
   - Implement a basic HTTP reverse proxy (`axum`)
   - Design capability traits for 3 common IoT devices (Speaker, Camera, Sensor)
   - Build an MQTT client prototype: connect → subscribe → receive messages

4. **Prepare proposal**:
   - Describe your understanding of the project architecture
   - Propose specific technical solutions you plan to implement
   - Estimate phase durations and define milestones

### Mentors
  - lijingrs (AmosLi)
  - yangrudan (CookieYang)

---

## Idea 2: Cognitive Observatory — Panoramic Monitoring Platform for AI Agent Systems + Memory & Knowledge Graph Ecosystem

### Reference Platform

**LangSmith** — LangChain's unified LLM application development platform covering observability, evaluation, prompt engineering, and deployment management. This project implements the complete LangSmith feature set including distributed tracing, real-time monitoring, insight analysis, evaluation framework, prompt versioning, and monitoring dashboards.

**LangChain** — A comprehensive framework for LLM applications. This project implements LangChain's memory systems.

**LlamaIndex** — A data framework for LLM applications with knowledge graph support, advanced indexing, and retrieval strategies.

### Brief Description

Build a LangSmith-level observability and evaluation platform providing panoramic visibility for all stages of the AI Agent lifecycle—from development debugging, quality evaluation to production monitoring and continuous improvement. Also integrates a **Three-Layer Memory System** for agent knowledge accumulation, and a **Knowledge Graph Engine** for structured information reasoning and debugging.

### Detailed Description

When multi-agent systems make wrong decisions, the question isn't "where did it go wrong?"—it's "where do I even start looking?" Traditional debugging tools are blind to the unique challenges of AI systems: non-deterministic LLM outputs, distributed agent decisions, complex workflow topologies.

This project builds **Cognitive Observatory**, implementing LangSmith's complete feature matrix:

**Observability**:
- **Tracing**: Detailed call chains, error and latency localization, non-intrusive integration, OpenTelemetry compatibility
- **Real-time Monitoring**: Pre-built dashboards (request count, error rate, P50/P99 latency, token usage, cost), custom charts, webhook alerts
- **Insights**: Conversation clustering, problem localization, pattern discovery

**Evaluation**:
- **Offline Evaluation**: Dataset management, benchmarking, regression testing, unit tests, backtesting
- **Online Evaluation**: Real-time quality monitoring, anomaly detection, production feedback collection
- **Evaluators**: Human review, code evaluation, LLM-as-judge, pairwise comparison
- **Continuous Improvement**: Evaluation result trace correlation, issue-to-test-case conversion

**Prompt Engineering**:
- **Prompt Hub**: Prompt template storage, variable mechanism, Playground instant testing
- **Version Control**: Commit history, tag marking, branching and merging
- **Performance Evaluation**: Prompt-dataset association, automatic scoring, multi-version comparison

**Deployment & Collaboration**:
- **Multi-workspace**: Organization/workspace hierarchy management, environment isolation
- **Permission Control**: RBAC roles (admin/editor/observer), custom roles
- **Data Management**: Encrypted storage, data residency, sensitive data masking

**Three-Layer Memory System** (New):
- **Episodic Memory**: Conversation history, interaction logs, event sequences with temporal indexing
- **Semantic Memory**: Vector-encoded facts, concepts, knowledge with entity linking
- **Procedural Memory**: Learned skills, strategies, workflow templates with execution metrics
- **Memory Consolidation Engine**: LLM-powered automatic knowledge extraction
- **Memory Decay**: Importance-based retention with configurable policies
- **Cross-Session Persistence**: Long-term memory with efficient retrieval

**Knowledge Graph Engine** (New):
- **Entity Extraction**: NER + LLM-powered entity recognition (for trace data entities)
- **Relation Inference**: Extract relationships from unstructured text (for decision chain analysis)
- **Graph Storage**: Neo4j or native graph database integration
- **Graph Retrieval**: Subgraph matching, path queries, neighbor expansion
- **Graph + Vector Fusion**: Combine structured and semantic retrieval
- **Schema Inference**: Automatic ontology construction from data

### Expected Outcomes

**Phase 1: Core Tracing & Observability (Weeks 1-4)**
- `mofa-observability` crate foundation
- OpenTelemetry-compatible distributed tracing system
- LLM telemetry: prompt/response logs, token counting, cost attribution
- Basic monitoring dashboard: request statistics, error rate, latency distribution
- Trace data storage: in-memory + PostgreSQL backend

**Phase 2: Evaluation Framework (Weeks 5-10)**
- Offline evaluation system: dataset management, test case organization
- Evaluator framework: `Evaluator` trait, LLM-as-judge, code evaluation
- Online evaluation: real-time quality monitoring, anomaly detection rules
- Evaluation result storage and query API
- Regression testing and benchmarking tools

**Phase 3: Prompt Engineering & Time Travel (Weeks 11-16)**
- Prompt hub: template storage, variable system, version control
- Prompt Playground: instant testing, multi-turn dialogue simulation
- Time-travel debugging: state snapshots, conversation replay, counterfactual exploration
- Insight analysis: conversation clustering, pattern discovery algorithms
- Human feedback integration: annotation queue, scoring system

**Phase 4: Dashboard & Integration (Weeks 17-20)**
- Web dashboard enhancement: React frontend, real-time WebSocket push
- Alert system: threshold configuration, webhook notifications (Slack/email)
- Grafana integration: Prometheus metrics export
- RBAC permission control: role management, API keys
- Docker Compose deployment
- Documentation: API reference, user guide, integration examples

**Phase 5: Memory System & Knowledge Graph (Weeks 21-26)**
- Three-layer memory system with distinct storage
- Memory consolidation engine with LLM summarization
- Memory decay with importance scoring
- Entity extraction with NER + LLM
- Relation inference from unstructured text
- Graph storage integration (Neo4j or native)
- Graph retrieval: subgraph, path, neighbor queries
- Memory and trace data integration (time-travel debugging support)

### Minimum Viable Product (MVP)

Participants must deliver the following MVP before the bonding period ends:
- Running tracing service with HTTP/gRPC data ingestion
- At least 1 evaluator (LLM-as-judge or code evaluation)
- Basic Web dashboard showing trace list and details
- Simple offline evaluation flow (dataset → evaluation → results)
- Command-line tool for submitting trace data
- Episodic and semantic memory with consolidation basic implementation
- Basic entity extraction pipeline

### Stretch Goals

- **Advanced insights**: AI-driven automatic problem diagnosis, root cause analysis
- **Multi-tenant support**: Complete workspace isolation, organization management
- **SSO integration**: OAuth 2.0, SAML enterprise authentication
- **Performance optimization**: Trace data compression, hot/cold tiered storage
- **SDK support**: Python/TypeScript SDK for application integration
- **Agent deployment**: LangSmith-style Agent Server integration

### Acceptance Criteria

- [ ] Tracing system captures complete agent execution chains (input, output, tool calls, LLM requests)
- [ ] Supports OpenTelemetry standard import/export, compatible with Jaeger/Grafana
- [ ] Evaluation framework supports at least 3 evaluator types
- [ ] Offline evaluation can execute on datasets and generate scoring reports
- [ ] Online evaluation can detect production anomalies in real-time and trigger alerts
- [ ] Prompt version control supports commit history, tags, rollback
- [ ] Time-travel debugging can replay any historical session
- [ ] Web dashboard response time < 500ms, supports real-time updates
- [ ] Unit test coverage ≥ 70%, integration tests cover core scenarios
- [ ] Reproducible deployment documentation and demo scripts
- [ ] Three-layer memory system with consolidation and decay fully implemented
- [ ] Memory retrieval latency < 100ms
- [ ] Knowledge graph supports entity extraction, relation inference, and graph retrieval
- [ ] Graph query latency < 200ms

### Skills Required

- **Required**: Strong Rust programming (async/await, trait design, error handling)
- **Required**: Understanding of OpenTelemetry and distributed tracing principles
- **Required**: Familiarity with SQL databases (PostgreSQL) and data modeling
- **Preferred**: Observability tool experience (Jaeger, Grafana, Prometheus)
- **Preferred**: Frontend experience (TypeScript/React)
- **Preferred**: LLM evaluation methods (LLM-as-judge, RAGAS, etc.)

### Difficulty

**High** (350 hours)

### Getting Started

1. **Review existing code**:
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring - Monitoring module
   - https://github.com/mofa-org/mofa/tree/main/examples/monitoring_dashboard - Monitoring example

2. **Study reference platforms**:
   - https://github.com/langchain-ai/langsmith-sdk - LangSmith SDK
   - https://github.com/open-telemetry/opentelemetry-rust - OpenTelemetry Rust SDK

3. **Complete micro-tasks**:
   - Implement a basic tracing subscriber that records function calls
   - Design an evaluator trait supporting custom scoring logic
   - Build a simple trace visualization prototype (CLI or Web)

4. **Prepare proposal**:
   - Describe your understanding of LangSmith's module functionality
   - Propose specific technical solutions you plan to implement
   - Estimate phase durations and define milestones

### Mentors
- lijingrs (AmosLi)
- BH3GEI (Yao Li)

---

## Idea 3: Cognitive Compute Mesh — Building the "HTTP Moment" for AI Inference + RAG & Vector Storage Ecosystem

### Reference Platforms

**LiteLLM** — Unified API gateway supporting 100+ LLM providers with consistent interface, automatic fallbacks, and cost tracking.

**vLLM** — High-throughput inference engine with PagedAttention, continuous batching, and production-grade serving.

**Ollama** — Local LLM runtime with model management, GPU acceleration, and REST API compatibility.

**Ray Serve** — General-purpose model serving framework with autoscaling, multi-model orchestration, and cross-cluster deployment.

**Kubernetes** — Container orchestration standard that proved "unified abstraction + pluggable backend" can dominate a domain.

**LlamaIndex** — A data framework for LLM applications with advanced indexing and retrieval strategies.

This project is not just building an inference gateway—it's establishing the **open protocol standard for AI inference**, making "inference as a service" as ubiquitous and plug-and-play as HTTP, while integrating **Production-grade RAG Pipeline** and **Multi-Backend Vector Storage** ecosystem.

### Abstract

**Vision**: Just as HTTP unified information transfer and SQL unified data querying, Cognitive Compute Mesh will establish the **open protocol standard for AI inference**—any agent, any model, any hardware, any location—write once, run everywhere.

**Core Proposition**: Today's AI inference is fragmented into silos—OpenAI, Anthropic, local Ollama, cloud vLLM, edge devices—each a separate world. Cognitive Compute Mesh builds a **Unified Inference Federation**, eliminating vendor lock-in and establishing an open ecosystem.

**Mentors**: BH3GEI (Yao Li), lijingrs (AmosLi)

### Problem & Opportunity

**Current Dilemma**:
- **Vendor Lock-in**: Migrating from OpenAI to Anthropic requires code rewrites
- **Fragmented Worlds**: Local inference (Ollama) and cloud inference (OpenAI) are two separate systems
- **Cost Black Box**: Inference costs are unpredictable, unoptimizable, unattributable
- **Innovation Barrier**: New inference services require one-by-one integration, no standard exists
- **Resource Waste**: GPU clusters, edge devices, local compute cannot coordinate

**Historical Inspiration**:
- Before HTTP: Each information transfer needed a dedicated protocol
- Before SQL: Each database required learning a new language
- Before Kubernetes: Each deployment needed custom scripts
- **Before Inference Protocol (Now)**: Each inference service requires re-integration

### Solution: Cognitive Compute Mesh

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     Cognitive Compute Mesh                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    Open Protocol Layer                               │   │
│  │  "Define once, compatible everywhere" — HTTP for inference          │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ Inference   │ │ Streaming   │ │ Tool Calling/               │   │   │
│  │  │ Request     │ │ Response    │ │ Multimodal/Embedding        │   │   │
│  │  │ Protocol    │ │ Protocol    │ │ Unified Abstraction         │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    Intelligent Routing Layer                         │   │
│  │  "Optimal path, automatic selection" — BGP for inference            │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ Cost        │ │ Latency     │ │ Geographic/Compliance       │   │   │
│  │  │ Optimization│ │ Optimization│ │ Smart Failover              │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    Federated Compute Layer                           │   │
│  │  "Boundless compute, seamless coordination" — Kubernetes for infer  │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ Local       │ │ Cloud       │ │ Edge/Specialized Hardware   │   │   │
│  │  │ OminiX-MLX  │ │ OpenAI etc. │ │ Groq/Cerebras/Custom        │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    Ecosystem Extension Layer                         │   │
│  │  "Everyone contributes, value flows" — crates.io for inference      │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ Backend SDK │ │ Model       │ │ Protocol Extensions/        │   │   │
│  │  │ Framework   │ │ Adapters    │ │ Community Contributions     │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Core Modules

**1. Open Protocol Layer**

Establishing the universal language for inference services:

- **Inference Request Protocol (IRP)**: Standardized inference request format supporting text, multimodal, tool calling
- **Streaming Response Protocol (SRP)**: Unified streaming response format with incremental output, heartbeat, cancellation
- **Capability Discovery Protocol (CDP)**: Automatic discovery of backend capabilities (models, modalities, tools)
- **Health Check Protocol (HCP)**: Standardized health status reporting and monitoring
- **Protocol Version Negotiation**: Backward-compatible protocol evolution mechanism

**2. Intelligent Routing Layer**

Optimal scheduling for inference requests:

- **Multi-Objective Optimization**: Multi-dimensional tradeoff of cost, latency, quality, compliance
- **Policy Engine**: Programmable routing policies (DSL or Rhai scripts)
- **Load-Aware Routing**: Dynamic scheduling based on queue depth, GPU utilization, memory pressure
- **Self-Healing**: Automatic fault detection, circuit breaking, degradation, recovery
- **Capacity Prediction**: Load prediction and warmup based on historical data

**3. Federated Compute Layer**

Integrating global inference compute:

- **Local Inference Backends**:
  - OminiX-MLX (macOS unified memory optimization)
  - llama.cpp (cross-platform CPU/GPU)
  - vLLM (high-performance serving)
- **Cloud Inference Backends**:
  - OpenAI, Anthropic, Google, AWS Bedrock
  - Azure OpenAI, Alibaba Cloud, Baidu Smart Cloud
- **Specialized Hardware Backends**:
  - Groq (LPU inference)
  - Cerebras (wafer-scale computing)
  - Edge TPU/NPU
- **Hybrid Pipelines**: Seamless orchestration of local ASR + cloud LLM + local TTS

**4. Ecosystem Extension Layer**

Building open contribution mechanisms:

- **Backend SDK**: Standardized framework for new backend integration in <2 hours
- **Model Adapters**: Plug-and-play support for new model formats
- **Protocol Extensions**: Standard extension points for custom capabilities
- **Contributor Incentives**: Usage statistics, quality ratings, community recognition
- **Trust System**: Code signing, security audits, vulnerability reporting

**5. Production RAG Pipeline** (New)

Integrating inference with retrieval-augmented generation:

- **Embedding Providers**: OpenAI, Cohere, Voyage, local ONNX/Candle models
- **Embedding Cache**: LRU cache with configurable TTL and batching
- **Hybrid Retrieval**: Dense vectors + BM25 sparse + ColBERT late interaction
- **Reciprocal Rank Fusion**: Combine multiple retrieval signals
- **Query Expansion**: LLM-powered query transformation and multi-query
- **Re-Ranking**: Cross-encoder, LLM-based, MMR diversity, freshness boosting
- **Inference Context Assembly**: Auto-inject retrieved context for inference requests

**6. Multi-Backend Vector Storage** (New)

Unified vector storage abstraction:

- **Unified Interface**: `VectorStore` trait with consistent API
- **Qdrant**: Production cloud deployment
- **pgvector**: PostgreSQL-native vector storage
- **Milvus**: Large-scale vector database
- **In-Memory HNSW**: Development and testing
- **Semantic Routing**: Backend selection based on vector similarity

### Ecosystem Value Proposition

| Stakeholder | Value Gained |
|-------------|--------------|
| **Agent Developers** | Write once, run everywhere—zero vendor lock-in |
| **Enterprises** | 50%+ cost optimization, risk distribution, compliance control |
| **Inference Providers** | One-click access to MoFA ecosystem, global developer reach |
| **Open Source Community** | Open standards, fair competition, innovation without barriers |
| **Hardware Vendors** | Standard interface, no need for one-by-one software adaptation |

### Expected Outcomes

**Phase 1: Protocol Foundation (Weeks 1-5)**
- Inference Request Protocol (IRP) design and implementation
- OpenAI-compatible protocol adapter
- Anthropic-compatible protocol adapter
- Streaming Response Protocol (SRP) implementation
- Protocol compatibility test suite

**Phase 2: Federated Compute (Weeks 6-12)**
- OminiX-MLX local backend integration (macOS priority)
- OpenAI cloud backend integration
- At least 1 additional cloud provider (Anthropic/Google)
- Local/cloud hybrid pipeline
- Zero-copy inference chain verification

**Phase 3: Intelligent Routing (Weeks 13-18)**
- Multi-objective routing policy engine
- Cost-optimization routing algorithm
- Latency-optimization routing algorithm
- Automatic failover system
- Capacity prediction and warmup

**Phase 4: Ecosystem Opening (Weeks 19-22)**
- Backend SDK framework release
- Model adapter interface
- Capability Discovery Protocol (CDP)
- Complete documentation and migration guides
- Community contribution process

**Phase 5: RAG Pipeline & Vector Storage (Weeks 23-28)**
- OpenAI and Cohere embedding providers
- Embedding cache with LRU eviction
- BM25 sparse retrieval implementation
- ColBERT late interaction (token-level matching)
- Reciprocal Rank Fusion algorithm
- Cross-encoder and LLM re-ranking
- MMR diversity and freshness boosting
- Qdrant and pgvector backend integration
- In-memory HNSW vector storage
- End-to-end RAG pipeline integration

### Minimum Viable Product (MVP)

Must deliver before bonding period ends:
- MVP implementation of Unified Inference Protocol (IRP)
- At least 1 local backend (OminiX-MLX or llama.cpp)
- At least 1 cloud backend (OpenAI)
- Basic routing policy (availability-first)
- End-to-end demo: same Agent code runs on local and cloud
- OpenAI embedding provider with caching
- Basic BM25 + dense hybrid retrieval
- At least 1 vector storage backend (Qdrant or pgvector)

### Stretch Goals

- **Multi-region Deployment**: Cross-geographic-region inference federation
- **Cost Attribution System**: Precise cost tracking down to agent, session, request level
- **Inference Marketplace Prototype**: Supply-demand matching for inference resources
- **Protocol Standardization Push**: Submit draft to industry standards organizations
- **More Backends**: Groq, Cerebras, edge devices

### Acceptance Criteria

- [ ] Unified protocol supports seamless conversion between OpenAI and Anthropic API styles
- [ ] Local backend implements zero-copy inference pipeline (ASR→LLM→TTS)
- [ ] Cloud backend supports automatic failover with recovery time <1 second
- [ ] Routing policies are configurable, supporting cost/latency/quality tradeoffs
- [ ] Backend SDK allows new backend integration in <4 hours
- [ ] Same Agent code runs unmodified on local, cloud, and hybrid modes
- [ ] Benchmarks: latency, throughput, cost vs single-provider optimized ≥30%
- [ ] Unit test coverage ≥80%, protocol compatibility tests 100% passing
- [ ] Documentation: protocol specification, backend development guide, migration tutorials
- [ ] At least 3 embedding providers (OpenAI, Cohere, Local) working
- [ ] Hybrid retrieval (Dense + BM25 + Graph) improves accuracy by ≥20% over dense-only
- [ ] Re-ranking improves precision@10 by ≥25%
- [ ] At least 3 vector storage backends (Qdrant, pgvector, in-memory HNSW) available
- [ ] Embedding batch of 100 texts < 5s, Hybrid retrieval < 200ms

### Technical Requirements

- **Primary Landing**: `mofa` main repository (`mofa-foundation`/`mofa-runtime`)
- **Prototype Validation**: `mofa-local-llm` as rapid iteration playground
- **Cross-Platform**: Must support macOS and Linux, Windows is a plus
- **Hardware Adaptation**: Priority on Apple Silicon, also support NVIDIA GPU

### Reference Resources

* https://github.com/mofa-org/mofa-local-llm - Local inference prototype
* https://github.com/OminiX-ai/OminiX-MLX - macOS inference engine
* https://github.com/BerriAI/litellm - LiteLLM unified gateway
* https://github.com/vllm-project/vllm - vLLM inference engine
* https://github.com/ray-project/ray - Ray distributed computing

### Skills Required

- **Required**: Strong Rust programming (async/await, trait design, systems programming)
- **Required**: Understanding of LLM inference principles and API design
- **Required**: Distributed systems experience (routing, load balancing, fault recovery)
- **Preferred**: Apple Silicon or GPU programming experience
- **Preferred**: Protocol design and standardization experience
- **Preferred**: Open source project contribution experience

### Difficulty

**High** (350 hours)

### Mentors
- BH3GEI (Yao Li)
- lijingrs (AmosLi)
---

## Idea 4: Cognitive Workflow Engine — Declarative Workflow Orchestration & Visualization Platform

### Reference Platforms

**Temporal** — Distributed workflow engine with durable execution, retries, and compensation transactions.

**n8n** — Open-source workflow automation platform with visual node editor, supporting 400+ integrations.

**Airflow** — Data engineering workflow orchestration with DAG definition, scheduling, and monitoring.

This project builds an **AI-native workflow engine** combining declarative DSL, visual editor, and MoFA ecosystem integration.

### Brief Description

Build a **Declarative Workflow Orchestration Engine** that enables users to define complex AI Agent workflows through YAML/JSON DSL or visual editor, supporting conditional branching, loops, error handling, human approval, parallel execution, and deep integration with MoFA's Gateway, Observatory, and Orchestrator.

### Detailed Description

Today's AI applications demand flexible workflow orchestration capabilities—from simple linear processing to complex multi-agent collaboration. Existing solutions are either too generic (Temporal, Airflow) or lack AI-native support (n8n). This project builds **Cognitive Workflow Engine**, a workflow engine designed specifically for AI Agents.

**Architecture**:

```
┌─────────────────────────────────────────────────────────────────┐
│                    Cognitive Workflow Engine                     │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Visual Workflow Editor                     ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ Drag &  │ │ Node    │ │ Live    │ │ AI-Assisted     │   ││
│  │  │ Drop    │ │ Library │ │ Preview │ │ Design          │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   DSL & Schema Layer                         ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ YAML/   │ │ JSON    │ │ Schema  │ │ Version Control │   ││
│  │  │ JSON DSL│ │ Schema  │ │ Validator│ │ & Migration    │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Execution Engine                           ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ DAG     │ │ State   │ │ Error   │ │ Persistence &   │   ││
│  │  │ Executor│ │ Machine │ │ Handler │ │ Recovery        │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Node Library                               ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ Agent   │ │ Cond.   │ │ Loop    │ │ Human Approval  │   ││
│  │  │ Invoke  │ │ Branch  │ │ Iterate │ │ (HITL)          │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ LLM     │ │ Tool    │ │ Data    │ │ Sub-Workflow    │   ││
│  │  │ Reason  │ │ Call    │ │ Transform│ │ Nesting        │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────┘
```

**Core Modules**:

**1. Declarative DSL**
- **YAML/JSON Workflow Definition**: Human-readable workflow description
- **Strongly-Typed Schema**: Type-safe node inputs/outputs
- **Expression Language**: JMESPath/CEL expressions for dynamic computation
- **Template System**: Parameterized workflows, environment variable substitution
- **Version Control Friendly**: Git diff-friendly DSL design

**2. Visual Editor**
- **Drag-and-Drop Node Editing**: React Flow or similar library implementation
- **Live Preview**: Real-time validation and preview during editing
- **AI-Assisted Design**: Workflow recommendations from natural language descriptions
- **Debug Panel**: Breakpoints, variable inspection, step-by-step execution
- **Import/Export**: Bidirectional conversion between DSL and visualization

**3. Execution Engine**
- **DAG Executor**: Topological sort, parallel scheduling, dependency resolution
- **State Machine Management**: Run, pause, resume, cancel, retry
- **Error Handling**: Retry strategies, compensation transactions, dead letter queue
- **Persistence**: PostgreSQL execution state storage, crash recovery support
- **Timeout Control**: Node-level and workflow-level timeouts

**4. Node Library**
- **Agent Node**: Invoke MoFA Agent (via Orchestrator)
- **LLM Node**: Direct LLM inference calls (via Compute Mesh)
- **Tool Node**: Invoke MCP tools (via Gateway)
- **Control Flow Nodes**: Conditional branching, loops, parallel, wait
- **Data Nodes**: Transform, filter, aggregate, merge
- **HITL Node**: Human approval, form input, selection

**5. Ecosystem Integration**
- **Gateway Integration**: Workflows can access IoT devices and external APIs
- **Observatory Integration**: Workflow execution tracing, performance analysis
- **Orchestrator Integration**: Complex multi-agent collaboration as workflow nodes

### Expected Outcomes

**Phase 1: DSL & Execution Engine (Weeks 1-5)**
- `mofa-workflow` crate foundation
- YAML/JSON DSL design and parser
- Schema validation system
- DAG executor: sequential, parallel execution
- Basic nodes: Agent invoke, LLM inference, conditional branch

**Phase 2: State Management & Persistence (Weeks 6-10)**
- State machine implementation: run/pause/resume/cancel
- PostgreSQL persistence layer
- Error handling: retry strategies, compensation transactions
- Crash recovery mechanism
- Workflow version management

**Phase 3: Visual Editor (Weeks 11-16)**
- React frontend foundation
- Drag-and-drop node editor
- Bidirectional DSL-visualization conversion
- Real-time validation and error hints
- Basic debugging features

**Phase 4: Advanced Nodes & Integration (Weeks 17-22)**
- Loop iteration node
- Sub-workflow nesting
- HITL approval node
- Gateway/Orchestrator integration
- AI-assisted workflow design
- Complete documentation and examples

**Phase 5: Production Ready (Weeks 23-26)**
- Expression language (JMESPath/CEL)
- Workflow template library
- Performance optimization and benchmarking
- CLI tools: `mofa workflow run/validate/export`
- Docker Compose deployment

### Minimum Viable Product (MVP)

Participants must deliver the following MVP before the bonding period ends:
- YAML DSL parser and validator
- Basic DAG executor (sequential + parallel)
- At least 3 node types (Agent invoke, conditional branch, LLM inference)
- PostgreSQL persistence
- Simple CLI runner: `mofa workflow run example.yaml`

### Stretch Goals

- **Distributed Execution**: Cross-node workflow scheduling
- **Workflow Marketplace**: Share and discover workflow templates
- **Real-time Collaboration**: Multi-user simultaneous workflow editing
- **Performance Analysis**: Workflow bottleneck identification and optimization suggestions
- **Natural Language to Workflow**: LLM-driven workflow generation

### Acceptance Criteria

- [ ] DSL supports both YAML and JSON formats, Schema validation 100% coverage
- [ ] Executor supports at least 8 node types
- [ ] State machine supports run/pause/resume/cancel/retry
- [ ] Can recover execution from persisted state after crash
- [ ] Visual editor supports drag, connect, delete nodes
- [ ] Bidirectional DSL-visualization conversion with no information loss
- [ ] Orchestrator integration: workflows can invoke Swarm orchestration
- [ ] Gateway integration: workflows can access IoT devices
- [ ] Unit test coverage ≥ 80%, integration tests cover core scenarios
- [ ] Documentation: DSL reference, node library, API docs

### Skills Required

- **Required**: Strong Rust programming (async/await, serde, sqlx)
- **Required**: Understanding of DAG and workflow engine principles
- **Required**: Frontend development experience (React, TypeScript)
- **Preferred**: Workflow engine development experience (Temporal, Airflow, n8n)
- **Preferred**: DSL/parser design experience
- **Preferred**: Visual graph editor experience (React Flow, X6)

### Difficulty

**High** (350 hours)

### Getting Started

1. **Review existing code**:
   - https://github.com/mofa-org/mofa/tree/main/examples/workflow_dsl - Workflow DSL example
   - https://github.com/mofa-org/mofa/tree/main/examples/workflow_orchestration - Workflow orchestration

2. **Study reference platforms**:
   - https://github.com/temporalio/temporal - Temporal workflow engine
   - https://github.com/n8n-io/n8n - n8n automation platform
   - https://github.com/apache/airflow - Airflow workflow orchestration

3. **Complete micro-tasks**:
   - Design a simple YAML workflow DSL
   - Implement DAG topological sort and parallel execution
   - Build a basic workflow state machine

4. **Prepare proposal**:
   - Describe your design approach for workflow DSL
   - Propose technical solution for visual editor
   - Estimate phase durations and define milestones

### Mentors
- lijingrs (AmosLi)
- yangrudan (CookieYang)


---


## Idea 5: Cognitive Swarm Orchestrator — Swarm Intelligence Coordination with Human-in-the-Loop Governance + Plugin Marketplace & Semantic Discovery Ecosystem

### Reference Platform

**OpenClaw** — A 24/7 task automation platform emphasizing single-agent execution. This project **does not replicate** OpenClaw's automation path, but builds a **Swarm orchestration layer**.

**ZeroClaw** — A lightweight Rust Agent runtime emphasizing performance. This project **does not compete** on runtime, but builds a **collaboration governance layer**.

**crates.io** — Rust's official package registry with versioning, dependencies, and publishing workflow.

**Differentiation**: 2026 is the "Era of Orchestration"—transitioning from single super-agents to specialized agent **swarm collaboration**. This project builds the **core orchestration and governance engine** for the MoFA ecosystem, integrating **Plugin Marketplace Core** (dependency resolution, trust scoring) and **Semantic Agent Discovery** capabilities.

### Brief Description

Build a **Swarm Orchestration Engine** that coordinates multiple specialized agents to complete complex tasks collaboratively, integrating with MoFA's Gateway (capability access), Smith (observability), and SDK (polyglot) to form a complete ecosystem loop, with human-in-the-loop (HITL) mechanisms ensuring critical decisions are supervised by humans. Also integrates **Plugin Marketplace Core** (dependency resolution, trust scoring, signature verification) and **Semantic Agent Discovery** (embedding-based capability matching) to build an open ecosystem.

### Detailed Description

**The Problem**: OpenClaw proved the value of single-agent automation, but complex tasks require **multi-agent collaboration**—just as a company relies on a team with different roles rather than one all-capable employee. The 2026 trend is from "Cambrian Explosion" (model diversity) to "Species Convergence" (**orchestration and integration**).

**The Solution**: **Cognitive Swarm Orchestrator** is the "brain center" of the MoFA ecosystem. It doesn't execute tasks directly, but:
1. **Understand Tasks** → Decompose into subtasks
2. **Form Teams** → Dynamic agent capability matching
3. **Orchestrate Collaboration** → Select optimal coordination pattern
4. **Supervise Execution** → Via Smith observability
5. **Govern Decisions** → Human approval at critical nodes

```
┌─────────────────────────────────────────────────────────────────┐
│                     MoFA Ecosystem Integration                   │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────┐   ┌─────────────────────────────────────────┐  │
│  │   Gateway   │←→│         Cognitive Swarm Orchestrator      │  │
│  │ (Capability)│   │  ┌─────────┐ ┌─────────┐ ┌──────────┐   │  │
│  └─────────────┘   │  │ Task    │ │ Swarm   │ │  HITL    │   │  │
│                    │  │ Analyzer│ │ Composer│ │ Governor │   │  │
│  ┌─────────────┐   │  └─────────┘ └─────────┘ └──────────┘   │  │
│  │    SDK     │←→│       ↓            ↓            ↓         │  │
│  │ (Polyglot) │   │  ┌─────────────────────────────────────┐ │  │
│  └─────────────┘   │  │     Coordination Patterns Engine     │ │  │
│                    │  │  Sequential │ Parallel │ Debate │ ... │ │  │
│  ┌─────────────┐   │  └─────────────────────────────────────┘ │  │
│  │   Smith    │←→└─────────────────────────────────────────┘  │
│  │(Observability)│                                             │
│  └─────────────┘                                               │
└─────────────────────────────────────────────────────────────────┘
```

**Core Modules**:

**1. Task Analyzer**
- LLM-powered task decomposition: Complex task → subtask DAG
- Dependency analysis and critical path identification
- Subtask difficulty and risk rating (for HITL decisions)
- Structured execution plan output

**2. Swarm Composer**
- **Dynamic team formation**: Auto-match based on agent capability registry
- **7 coordination patterns**: Sequential, Parallel, Debate, Consensus, MapReduce, Supervision, Routing
- **LLM pattern recommendation**: Auto-select optimal pattern based on task characteristics
- **Load balancing**: Consider agent busyness, success rate, expertise

**3. HITL Governor**
- **5-phase Secretary pattern**: Receive → Clarify → Schedule → Monitor → Report
- **Intelligent approval routing**: Route to appropriate approvers based on risk level
- **Context assembly**: Auto-summarize key info before human review
- **AI-assisted decisions**: Generate decision suggestions and risk analysis
- **Escalation mechanism**: Auto-escalate on timeout/dispute

**4. Governance Layer**
- **SLA management**: Deadline tracking, delay alerts
- **Audit trail**: Complete decision chain recording (compliance-ready)
- **Multi-channel notifications**: WebSocket, Email, Slack, Telegram, DingTalk
- **RBAC permissions**: Role definitions, capability grants

**5. Ecosystem Integration**
- **Gateway integration**: Access physical/digital world via capability APIs (Speaker, Camera, Sensor, etc.)
- **Smith integration**: Auto-report trace data, evaluation feedback for optimization
- **SDK integration**: Python/Go/Kotlin/Swift orchestration APIs

**6. Plugin Marketplace Core** (New)
- **Dependency Resolution**: SemVer-compatible dependency graph solver with conflict detection
- **Version Management**: Multiple versions, deprecation, latest resolution
- **Trust Scoring**: Community ratings, download counts, security audits
- **Signature Verification**: Ed25519 cryptographic signatures for plugin authenticity
- **Capability Composition**: Multi-plugin synergy analysis

**7. Semantic Agent Discovery** (New)
- **Embedding Matching**: Vector-based agent capability matching
- **Query Expansion**: LLM-powered task query transformation and multi-query
- **Hybrid Retrieval**: Dense vectors + BM25 sparse retrieval
- **Capability Registry API**: Agent capability publish, search, discovery endpoints

### Expected Outcomes (Deliverables)

**Phase 1: Core Orchestration Engine (Weeks 1-4)**
- `mofa-orchestrator` crate foundation
- `TaskAnalyzer`: Task decomposition, DAG generation
- `SwarmComposer`: Dynamic team formation, capability matching
- Basic coordination patterns: Sequential, Parallel

**Phase 2: Coordination Patterns & HITL (Weeks 5-10)**
- Complete 7 coordination patterns implementation
- `HITLGovernor`: 5-phase Secretary lifecycle
- Approval workflow engine: Role routing, escalation mechanism
- AI-assisted decisions: Context assembly, suggestion generation

**Phase 3: Governance & Ecosystem Integration (Weeks 11-16)**
- `GovernanceLayer`: SLA management, audit trail
- Multi-channel notification adapters (Slack, Telegram, Email, DingTalk)
- Gateway integration: Capability API calls
- Smith integration: Trace data reporting, evaluation feedback

**Phase 4: SDK & Production Ready (Weeks 17-20)**
- Orchestration API polyglot bindings (Python/Go/Kotlin/Swift)
- REST API for swarm status, approval queue, audit logs (integrated with Observatory for visualization)
- CLI tools: `mofa swarm deploy`, `mofa swarm status`
- Docker Compose deployment
- Documentation: Orchestration guide, best practices, integration examples

**Phase 5: Plugin Marketplace & Semantic Discovery (Weeks 21-26)**
- SemVer dependency resolver with conflict detection
- Ed25519 signature verification system
- Trust scoring and security audit framework
- Agent capability registry API with semantic search
- Embedding matching and query expansion
- Hybrid retrieval (Dense + BM25) integration

### Minimum Viable Product (MVP)

Participants must deliver the following MVP before the bonding period ends:
- Running orchestration service with task decomposition and subtask scheduling
- At least 2 coordination patterns (Sequential + Parallel) fully implemented
- Basic HITL flow: Manual approval API (visualization via Observatory integration)
- Gateway integration demo (access devices via capability API)
- Simple CLI demo: `mofa swarm run examples/swarm_demo.yaml`
- Basic dependency resolution (SemVer)
- Agent capability registry with simple search

### Stretch Goals

- **Advanced patterns**: LLM-optimized Debate and Consensus modes
- **Adaptive scheduling**: Learning-based task assignment from historical data
- **Cross-cluster orchestration**: Multi-tenant, multi-region swarm collaboration
- **Deep Smith integration**: Orchestration quality evaluation, auto pattern recommendation
- **Declarative DSL**: YAML-defined swarm orchestration rules

### Acceptance Criteria

- [ ] Support at least 5 coordination patterns, dynamically selectable via API
- [ ] Task decomposition generates valid DAG with dependency-aware parallel execution
- [ ] Complete HITL flow: Approval request → Human response → Execution continuation
- [ ] Audit trail covers all critical decision nodes
- [ ] Gateway integration: Agents can access devices via capability API
- [ ] Smith integration: Trace data auto-reported
- [ ] Unit test coverage ≥ 70%, integration tests cover core scenarios
- [ ] Reproducible deployment documentation and demo scripts
- [ ] Dependency resolution supports SemVer, conflict detection accuracy 100%
- [ ] Signature verification prevents plugin tampering
- [ ] Semantic search precision ≥ 80% (based on benchmarks)
- [ ] Trust scoring system fully implemented

### Comparison with Competitors

| Feature | OpenClaw | ZeroClaw | **This Project (Swarm Orchestrator)** |
|---------|----------|----------|--------------------------------------|
| **Positioning** | Single-agent automation | Lightweight runtime | **Multi-agent orchestration** |
| **Execution Mode** | Independent | Independent | **Collaborative orchestration** |
| **HITL** | Basic | None | **Full governance flow** |
| **Observability** | Basic logs | None | **Smith integration** |
| **Capability Access** | Limited | None | **Gateway integration** |
| **Polyglot** | None | None | **SDK integration** |

### Skills Required

- **Required**: Strong Rust programming (async/await, trait design)
- **Required**: Understanding of distributed systems and coordination patterns
- **Required**: Understanding of DAG and task scheduling principles
- **Preferred**: LLM application development experience (prompt engineering, agent patterns)
- **Preferred**: Workflow engine or orchestration system experience
- **Preferred**: Notification systems and message queue experience

### Difficulty

**High** (350 hours)

### Getting Started

1. **Review existing code**:
   - https://github.com/mofa-org/mofa/tree/main/examples/secretary_agent - Secretary Agent implementation
   - https://github.com/mofa-org/mofa/tree/main/examples/multi_agent_coordination - Multi-agent coordination examples

2. **Study reference platforms**:
   - https://github.com/OpenClaw/OpenClaw - OpenClaw automation patterns
   - https://github.com/ZeroClaw/zeroclaw - ZeroClaw lightweight runtime

3. **Complete micro-tasks**:
   - Implement a simple task decomposer (LLM-powered)
   - Design 2 coordination pattern schedulers (Sequential, Parallel)
   - Build a basic approval workflow prototype

4. **Prepare proposal**:
   - Describe your understanding of swarm orchestration
   - Propose technical approach for Gateway/Smith integration
   - Estimate phase durations and define milestones

### Mentors
-- lijingrs (AmosLi)
-- BH3GEI (Yao Li)

---

## Project 6: Cognitive Agent Testing & Evaluation Platform — Testing, Evaluation & Quality Assurance for AI Agents

### Reference Platforms

**LangSmith** — LangChain's observability and evaluation platform, but lacks systematic Agent testing framework.

**TruLens** — LLM application evaluation tool, focused on RAG evaluation with limited Agent capabilities.

**Promptfoo** — Prompt testing tool, but doesn't support Agent behavior testing.

**AgentBench** — Agent benchmark framework, but only provides evaluation datasets, not a testing framework.

**DeepEval** — LLM evaluation framework, lacks Agent-specific testing capabilities.

This project builds a **Rust-native Agent Testing & Evaluation Platform**, filling the gap all Agent frameworks have in quality assurance—just as software testing (JUnit/pytest) is to software engineering, Agent testing frameworks are equally important for Agent development.

### Brief Description

Build an **Agent Testing & Evaluation Platform** that implements: Agent behavior unit testing framework, regression testing system, performance benchmarking, security & adversarial testing, alignment evaluation, A/B testing framework, canary deployment, metrics library, with deep integration into MoFA's Memory System, Orchestrator, and Observatory—making Agent development as testable, verifiable, and trustworthy as software engineering.

### Detailed Description

**Agent development faces the same challenges software engineering faced 50 years ago**—without testing frameworks, you can only "run it and see." LangChain has LangSmith, but it's primarily an observability tool, not a testing framework; other frameworks lack systematic testing capabilities entirely. This project builds **Cognitive Agent Testing & Evaluation Platform**, making MoFA the first Agent framework with a complete quality assurance system.

**Architecture**:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                  Cognitive Agent Testing & Evaluation Platform              │
├─────────────────────────────────────────────────────────────────────────────┤
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                        Test Definition Layer                          │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Agent Test  │ │ Scenario    │ │ Mock        │ │ Test Data      │  │  │
│  │  │ Cases DSL   │ │ Builder     │ │ Framework   │ │ Generator      │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Assertion   │ │ Expectation │ │ Golden      │ │ Parameterized  │  │  │
│  │  │ Library     │ │ Matchers    │ │ Responses   │ │ Tests          │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                              ↓ Test Execution ↓                            │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                      Test Execution Engine                            │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Test Runner │ │ Parallel    │ │ Determinism │ │ State           │  │  │
│  │  │ (Async)     │ │ Execution   │ │ Control     │ │ Isolation       │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ LLM Mock    │ │ Tool Mock   │ │ Time Travel │ │ Record/Replay   │  │  │
│  │  │ Server      │ │ Server      │ │ (Memory)    │ │ System          │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                              ↓ Test Results ↓                             │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                      Evaluation & Metrics Layer                       │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Accuracy    │ │ Consistency │ │ Safety      │ │ Alignment      │  │  │
│  │  │ Metrics     │ │ Metrics     │ │ Metrics     │ │ Metrics        │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Performance │ │ Cost        │ │ Latency     │ │ Quality        │  │  │
│  │  │ Benchmarks  │ │ Analysis    │ │ Percentiles │ │ Scores         │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                              ↓ Reports & Actions ↓                        │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                     Deployment & CI/CD Integration                    │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ A/B Testing │ │ Canary      │ │ Rollback    │ │ Gate            │  │  │
│  │  │ Framework   │ │ Deployment  │ │ Mechanism   │ │ Enforcement     │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────────┐  │  │
│  │  │ Report      │ │ Alerting    │ │ Trend       │ │ GitHub/GitLab  │  │  │
│  │  │ Generator   │ │ System      │ │ Analysis    │ │ Integration    │  │  │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────────┘  │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Core Modules**:

**1. Test Definition Layer**
- **Agent Test DSL**: Declarative test case definition, similar to Jest/pytest style
- **Scenario Builder**: Build complex multi-turn dialogue scenarios, tool calling scenarios, multi-agent collaboration scenarios
- **Mock Framework**: Mock LLM responses, Mock tool execution, Mock external APIs
- **Test Data Generator**: Auto-generate variant test cases, boundary conditions, adversarial samples
- **Assertion Library**: Agent behavior assertions (response contains, tool call correct, state change as expected)
- **Expectation Matchers**: Semantic matching, fuzzy matching, structured matching
- **Golden Responses**: Record and replay expected responses
- **Parameterized Tests**: Same test case supports multiple input parameters

**2. Test Execution Engine**
- **Async Test Runner**: Support concurrent execution of large number of tests
- **Parallel Execution**: Multi-thread/multi-process test execution
- **Determinism Control**: Fixed random seed, Mock time, Mock LLM output
- **State Isolation**: Independent environment for each test case
- **LLM Mock Server**: Simulate LLM API, support preset responses and rule-based responses
- **Tool Mock Server**: Simulate tool execution, support preset results
- **Time Travel**: Replay historical states of Memory System
- **Record/Replay System**: Record real interactions, replay for testing

**3. Evaluation & Metrics Layer**
- **Accuracy Metrics**: Task completion rate, tool call accuracy, information extraction accuracy
- **Consistency Metrics**: Response consistency for same input, behavioral stability
- **Safety Metrics**: Refusal rate for harmful requests, no sensitive info leakage rate
- **Alignment Metrics**: Instruction following degree, value alignment
- **Performance Benchmarks**: Throughput, latency distribution, resource consumption
- **Cost Analysis**: Token consumption, API call count, cost estimation
- **Latency Percentiles**: P50/P90/P99 latency statistics
- **Quality Scores**: LLM-as-Judge, human evaluation interface

**4. Deployment & CI/CD Integration**
- **A/B Testing Framework**: Traffic splitting, metric comparison, statistical significance testing
- **Canary Deployment**: Small traffic validation, automatic rollback mechanism
- **Rollback Mechanism**: Automatic rollback to stable version based on metrics
- **Gate Enforcement**: Block deployment if tests fail
- **Report Generator**: HTML/JSON/JUnit format reports
- **Alerting System**: Metric anomaly alerts, regression alerts
- **Trend Analysis**: Historical metric trends, performance degradation detection
- **GitHub/GitLab Integration**: PR checks, CI pipeline integration

**5. Advanced Testing Capabilities**
- **Adversarial Testing**: Auto-generate adversarial samples, jailbreak attack testing, prompt injection testing
- **Boundary Testing**: Extreme inputs, extra-long context, concurrency stress
- **Regression Testing**: Auto-detect behavioral regressions, Golden Response comparison
- **Exploratory Testing**: Random exploration of Agent behavior space
- **Fault Injection**: Simulate LLM failures, network failures, tool failures

**6. MoFA Ecosystem Integration**
- **Memory System Integration**: Test memory persistence, memory retrieval accuracy
- **Orchestrator Integration**: Test multi-agent collaboration, task decomposition
- **Observatory Integration**: Correlate test results with observability
- **Gateway Integration**: Test IoT scenarios, physical world interaction

### Expected Outcomes

**Phase 1: Testing Framework Foundation (Weeks 1-5)**
- `mofa-testing` crate foundation
- Test case definition DSL
- Basic assertion library
- Test runner (sync)
- Simple report generation

**Phase 2: Mock System (Weeks 6-10)**
- LLM Mock Server implementation
- Tool Mock framework
- Determinism control (seed, time Mock)
- Test isolation mechanism
- Record/replay system foundation

**Phase 3: Evaluation Metrics Library (Weeks 11-16)**
- Accuracy, consistency, safety metrics
- Performance benchmarking framework
- LLM-as-Judge integration
- Metric aggregation and statistics
- Observatory integration

**Phase 4: Advanced Testing Capabilities (Weeks 17-22)**
- Adversarial test generator
- Boundary condition testing
- Regression testing system
- Fault injection framework
- Parameterized test support

**Phase 5: CI/CD Integration (Weeks 23-28)**
- A/B testing framework
- Canary deployment support
- GitHub/GitLab CI integration
- Gate system
- Alerting and notification

**Phase 6: Ecosystem Integration & Optimization (Weeks 29-35)**
- Memory System testing support
- Orchestrator testing support
- Gateway testing support (IoT Mock)
- Performance optimization (large-scale testing)
- Complete documentation and examples

### Minimum Viable Product (MVP)

Participants must deliver the following MVP before the bonding period ends:
- Basic test case definition DSL
- At least 10 common assertions
- Simple LLM Mock (preset responses)
- Test runner + basic reports
- Demo: Write 5+ test cases for a simple Agent

### Stretch Goals

- **Visual Test Editor**: Web UI to edit and run tests
- **Test Case Recommendation**: Auto-recommend test cases based on Agent behavior
- **Cross-Framework Compatibility**: Support testing LangChain/CrewAI Agents
- **Fuzzing Tests**: Auto-discover Agent boundary conditions
- **Evaluation Dataset**: Build open-source Agent evaluation dataset

### Acceptance Criteria

- [ ] Support at least 50 assertion types
- [ ] LLM Mock supports OpenAI/Anthropic/Gemini protocols
- [ ] Test execution supports 1000+ concurrent tests
- [ ] Single test execution latency < 100ms (excluding LLM calls)
- [ ] Deterministic testing: 100% same output for same input
- [ ] Metrics library contains at least 30 metrics
- [ ] Support at least 5 report formats (HTML/JSON/JUnit/Allure/Markdown)
- [ ] GitHub Actions integration available
- [ ] Adversarial testing covers OWASP LLM Top 10
- [ ] A/B testing supports statistical significance testing
- [ ] Memory System integration testing available
- [ ] Orchestrator integration testing available
- [ ] Unit test coverage ≥ 90%
- [ ] Documentation: Testing guide, assertion reference, CI/CD integration guide

### Skills Required

- **Required**: Strong Rust programming (traits, macros, async/await)
- **Required**: Understanding of software testing principles (unit testing, integration testing, mocking)
- **Required**: Familiarity with CI/CD processes (GitHub Actions, GitLab CI)
- **Preferred**: LLM evaluation experience (LLM-as-Judge, benchmarking)
- **Preferred**: Security testing experience (adversarial attacks, jailbreak testing)
- **Preferred**: A/B testing and statistical analysis experience

### Difficulty

**High** (350 hours)

### Getting Started

1. **Review existing code**:
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel/src/agent - Agent core
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation - Foundation implementations

2. **Study reference platforms**:
   - https://github.com/traceloop/openllmetry - OpenTelemetry for LLM
   - https://github.com/promptfoo/promptfoo - Prompt testing tool
   - https://github.com/confident-ai/deepeval - LLM evaluation framework
   - https://github.com/EvalStore/EvalStore - Evaluation store

3. **Complete micro-tasks**:
   - Implement a simple Agent test assertion library (at least 5 assertions)
   - Implement basic LLM Mock Server (preset responses)
   - Write test cases for a simple Agent
   - Implement test report generation (JSON format)

4. **Prepare proposal**:
   - Describe your understanding of Agent testing challenges
   - Analyze limitations of existing tools
   - Propose your feasible architecture design
   - Estimate phase durations and define milestones

### Mentors
- lijingrs (AmosLi)
- yangrudan (CookieYang)

---

## Optional Chinese Translation

- Ideas list: [zh/ideas-list.md](./zh/ideas-list.md)
