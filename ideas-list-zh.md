# MoFA GSoC 2025 项目提案

> 中文版 | [English Version](./ideas-list.md)

本文档包含 Google Summer of Code 2025 的详细项目提案。整体框架已定，具体细节可在导师指导下根据贡献者建议进行调整。

## 关于 MoFA

[MoFA](https://mofa.ai/)（**Modular Framework for Agents**）是一个用于构建 AI Agent 的开源框架。我们的产品 **MoFA Studio** 是一个桌面应用，用于创建、运行和分享 AI 驱动的应用——基于 Rust、Makepad 和 Dora 构建。

我们诚邀 GSoC 贡献者加入，在系统工程、AI 基础设施和开发者工具的交叉领域，挑战真实世界的问题。

__官网:__ [mofa.ai](https://mofa.ai/)

__GitHub 仓库:__
- 核心运行时: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa) (`feature/mofa-rs` 分支)
- Studio 应用: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- 节点生态: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

__组织联系邮箱:__ dev@mofa.ai
__GSoC 贡献者指南:__ [README.md](./README.md)

---

## 项目一：AppGen —— 应用生成器

### 摘要

MoFA Studio 目前内置 8+ 应用，并支持 WebView 插件。但创建新应用仍需手动编码。**AppGen** 将是一个内置的 Studio 应用，允许用户从自然语言描述生成个性化应用。

用户描述需求（如："一个获取天气并生成日报的工具"），AppGen 将从 [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)（400+ 节点）中智能选择组件，编排工作流，并自动生成带有 Makepad UI 的可运行 Studio 应用。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### 目标与想法

* **语义节点搜索**：使用向量嵌入索引 [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)（400+ 节点）；从自然语言查询中检索相关组件
* **流程合成**：将高层描述转换为使用 mofa-rs 运行时的可执行数据流
* **Makepad UI 生成**：从数据模式生成直观的 Makepad 界面；支持表单、聊天和仪表板布局
* **自集成**：生成的应用可自动嵌入 Studio 作为 WebView 插件或原生 Rust 应用
* **个性化定制**：允许在初始生成后对 UI 和逻辑进行可视化调整
* **导出与分享**：打包生成的应用以供分发或分享

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa-node-hub
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs
* https://makepad.dev/

__所需技能__: Rust, Makepad UI, LLM 集成, 自然语言处理

__时间估计__: 120 小时（10 周）

__难度__: 高

---

## 项目二：Studio 可观测性面板

### 摘要

MoFA-rs 包含监控基础架构，具备指标收集能力。本项目将构建一个**完整的 Dashboard 服务器**，支持 REST API 和 WebSocket，并将这些能力直接集成到 MoFA Studio 中，为 Agent 执行提供实时可见性。

当前的 `mofa-monitoring` crate 已有指标收集功能；本项目将扩展其功能，添加生产级的 HTTP/WebSocket 服务器和 Studio 端可视化。

__导师__: BH3GEI (Yao Li), Bicheng Lou

### 目标与想法

* **Dashboard 服务器开发**:
  - 构建 HTTP 服务器（使用 axum 或类似框架），暴露指标的 REST API
  - 实现 WebSocket 端点用于实时流式更新
  - 设计高效的指标聚合和缓存机制

* **API 设计与实现**:
  - `/api/agents` — 列出所有 Agent 及其状态
  - `/api/agents/{id}` — 详细的 Agent 指标
  - `/api/metrics` — 系统级指标快照
  - `/api/flows` — 数据流执行状态
  - WebSocket `/ws` — 实时事件流

* **Studio 集成**:
  - 基于 Makepad 的实时可视化面板
  - Agent 状态显示（运行中、暂停、错误状态）
  - 消息流可视化，支持调用链追踪
  - 资源使用面板（CPU、内存、模型加载）
  - 日志聚合与智能过滤

* **混合运行时支持**:
  - 同时支持基于 Dora（当前）和原生 mofa-rs 的运行时
  - 跨后端的统一监控接口

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-monitoring
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-runtime

__所需技能__: Rust, HTTP/WebSocket 服务器 (axum/tokio), 实时数据可视化, Makepad UI

__时间估计__: 90 小时（8 周）

__难度__: 中

---

## 项目三：边缘模型编排器

### 摘要

在边缘设备上运行 AI 应用面临独特挑战：多个模型（ASR、LLM、TTS、embedding）争夺有限的内存和 GPU 资源。本项目实现一个智能的**模型生命周期管理器**，作为 `mofa-foundation` 层的核心组件，实现高效的边缘多模型编排。

该编排器将与 mofa-rs 运行时集成，作为基础服务管理模型加载、调度和资源分配。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

### 目标与想法

* **架构设计**:
  - 作为 `mofa-foundation` 层的服务组件实现（位于 `mofa-runtime` 之上，业务逻辑之下）
  - 设计清晰的 API 供 `mofa-runtime` 调用编排服务
  - 支持可插拔后端（Ollama、llama.cpp、自定义模型服务器）

* **生命周期管理**:
  - 按需模型加载，支持异步初始化
  - 基于空闲超时的自动卸载
  - 内存压力监控和主动管理
  - 带状态保存的优雅关闭

* **智能调度**:
  - 基于任务类型（ASR/LLM/TTS）、延迟要求和可用性将请求路由到最优模型
  - 在适用情况下支持模型并行和批处理
  - 基于优先级的抢占式调度

* **资源管理**:
  - 强制执行内存/GPU 配额，支持优雅抢占
  - 模型交换策略（LRU、基于优先级、预测性）
  - 资源使用追踪和向监控系统报告

* **降级策略**:
  - 当主模型失败或资源受限时自动回退到更小模型
  - 服务质量级别与相应的模型选择
  - 不可靠模型服务的熔断模式

* **集成**:
  - 与现有 `mofa-foundation/llm` provider 系统无缝集成
  - 向 Studio 可观测性面板暴露编排决策

#### 示例场景

一个语音助手流程包含：
- Whisper（ASR，2GB VRAM）
- Qwen（LLM，8GB VRAM）
- GPT-SoVITS（TTS，4GB VRAM）

总计超过可用内存。编排器将：
- 保持 LLM 常驻（核心功能）
- 语音输入时加载 ASR，空闲 30 秒后卸载
- 仅在合成期间加载 TTS
- 加载失败时回退到更小模型

#### 参考链接

* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/feature/mofa-rs/crates/mofa-runtime
* https://github.com/ollama/ollama

__所需技能__: Rust, 系统编程, 资源管理, GPU/边缘计算

__时间估计__: 140 小时（11 周）

__难度__: 高
