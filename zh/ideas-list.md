# MoFA GSoC 2026 项目提案

> 中文版 |  [English Version](../ideas-list.md)

本文档包含 Google Summer of Code 2026 的详细项目提案。整体框架已定，具体细节可在导师指导下根据贡献者建议进行调整。我们鼓励贡献者提出自己的方案——以下想法是起点，而非刚性规范。

> **开始之前**：请先在相关 GitHub issue 下留言表达兴趣，并简要描述你的思路。**等待维护者分配后再开始编码。** 这可以避免重复劳动。详见[贡献流程](./README.md#在-gsoc-之前贡献)。

## 速查：项目提案与对应仓库

### 核心项目 — 框架与基础设施

以下为主线优先方向：核心 Agent 框架、ML 编排与开发者工具。

| 项目 | 技能标签 | 主仓库 | 相关仓库 |
|------|---------|--------|---------|
| 1. AgentForge | `Rust` `系统设计` `插件架构` | [mofa](https://github.com/mofa-org/mofa)（mofa-kernel、mofa-foundation） | [mofa-studio](https://github.com/mofa-org/mofa-studio) |
| 3. 统一推理编排器 | `Rust` `系统编程` `本地 + 云端推理` | [mofa](https://github.com/mofa-org/mofa)（mofa-foundation、mofa-runtime） | [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm)、[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) |
| 4. 会话记录器与调试器 | `Rust` `系统设计` `数据可视化` | [mofa](https://github.com/mofa-org/mofa)（mofa-kernel、mofa-monitoring） | [mofa-studio](https://github.com/mofa-org/mofa-studio) |

### 社区项目 — UI 与应用

以下项目聚焦前端、产品应用与平台集成。不在关键路径上，但若你对这些方向有浓厚兴趣，欢迎选择。

| 项目 | 技能标签 | 主仓库 | 相关仓库 |
|------|---------|--------|---------|
| 2. 可观测性面板 | `Rust` `Makepad UI` `HTTP/WebSocket` | [mofa-studio](https://github.com/mofa-org/mofa-studio) | [makepad-chart](https://github.com/mofa-org/makepad-chart)、[makepad-d3](https://github.com/mofa-org/makepad-d3)、[mofa](https://github.com/mofa-org/mofa)（mofa-monitoring） |
| 5. MoFA Input 迁移 | `Rust` `macOS` `C++/Rust 互操作` `Apple Silicon` | [mofa-input](https://github.com/mofa-org/mofa-input) | [mofa](https://github.com/mofa-org/mofa)（推理层，见项目 3）、[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) |
| 6. Makepad AI 组件库 | `Rust` `Makepad UI` `组件设计` | 新仓库：`makepad-ai-toolkit` | [mofa-studio](https://github.com/mofa-org/mofa-studio)、[makepad-element](https://github.com/mofa-org/makepad-element)、[makepad-chart](https://github.com/mofa-org/makepad-chart) |

## CFP 索引（统一英文版）

- 框架与基础设施方向：[MoFA, an AI Native Framework for Agent](../ideas/framework-for-ai/call-for-proposal.md)
- 模型编排方向：[MoFA Agents: Support All Models](../ideas/mofa-agents/call-for-proposal.md)
- 人机交互方向：[MoFA's HCI for AI Native Agent Framework](../ideas/studio-for-ai/call-for-proposal.md)
- 批判性分析方向：[Why MoFA](../ideas/why-mofa/call-for-proposal.md)

---

## 开放任务 — 从这里开始贡献

以下是 MoFA 代码库中具体的、可独立完成的任务。它们是在 GSoC 之前或期间熟悉项目的好方式。**在相关 issue 下留言即可认领** —— 见[认领规则](./README.md#我们如何选人)。

| # | 任务 | 仓库 |
|---|------|------|
| 1 | 实现或完善框架 runtime（Dora / WASM / Tokio） | [mofa](https://github.com/mofa-org/mofa) |
| 2 | `mofa-ffi`：多语言 SDK 绑定 | [mofa](https://github.com/mofa-org/mofa) |
| 3 | 实现或完善消息总线、事件驱动与消息驱动架构 | [mofa](https://github.com/mofa-org/mofa) |
| 4 | 完善基于 graph 的 workflow 引擎和 DSL | [mofa](https://github.com/mofa-org/mofa) |
| 5 | `mofa-monitoring` 开发 | [mofa](https://github.com/mofa-org/mofa) |
| 6 | `mofa-cli` 各子命令的细化开发 | [mofa](https://github.com/mofa-org/mofa) |
| 7 | 实现 Codex 风格的上下文压缩 | [mofa](https://github.com/mofa-org/mofa) |
| 8 | 用 MoFA 框架实现经典[智能体设计模式](https://github.com/xindoo/agentic-design-patterns)，并据此迭代改进框架 | [mofa](https://github.com/mofa-org/mofa) |
| 9 | 丰富内置工具和 skills | [mofa](https://github.com/mofa-org/mofa) |
| 10 | 增加 RAG 和向量数据库集成 | [mofa](https://github.com/mofa-org/mofa) |
| 11 | 集成 [socketioxide](https://github.com/Totodore/socketioxide)、AWS S3 SDK | [mofa](https://github.com/mofa-org/mofa) |
| 12 | 实现框架级控制平面 + gateway | [mofa](https://github.com/mofa-org/mofa) |

| 13 | 将 [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) 整合进 mofa 核心框架，作为内置本地推理模块 | [mofa](https://github.com/mofa-org/mofa)、[mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) |
| 14 | 为 mofa-local-llm 做 Linux 推理后端适配（Rust，参考项目 3） | [mofa](https://github.com/mofa-org/mofa) |
| 15 | 用 mofa-rs 原生 runtime 重构 MoFA Studio 中的 Dora dataflow 依赖 | [mofa-studio](https://github.com/mofa-org/mofa-studio)、[mofa](https://github.com/mofa-org/mofa) |
| 16 | 基于 Cron 的定时 Agent 执行，面向高并发和大规模消息通知场景 | [mofa](https://github.com/mofa-org/mofa) |
| 17 | Human-in-the-loop：在任意节点暂停以进行人工审核 | [mofa](https://github.com/mofa-org/mofa) |
| 18 | 支持可视化调试 | [mofa](https://github.com/mofa-org/mofa) |
| 19 | MessageGraph 实现 | [mofa](https://github.com/mofa-org/mofa) |
| 20 | 差距分析：对标其他 Agent 框架，识别并实现智能体平台场景下尚缺的功能 | [mofa](https://github.com/mofa-org/mofa) |

抱歉，项目目前变动较大，我们还没来得及将这些任务梳理为完善的 issue。我们会尽快根据这些任务以及项目发展中出现的其他小问题，逐步补充 `good first issue` 标签。如果不确定从哪里开始，可在 [Discord](https://discord.gg/hKJZzDMMm9) 中提问。

AI 编码可以快速实现简单功能，但对于一个框架而言，仅仅"实现了"是不够的——还必须考虑实际可用性和生产力。我们希望每个功能都达到企业级交付标准。AI 无法判断一个功能是否契合框架的理念，而这恰恰是程序员价值的体现。作为与 AI 协作编码的"魔法师"，你通过独特的洞察和经验赋予框架灵魂。因此，我们期望每个 PR 都经过真实场景验证，确保其真正交付价值、服务于实际用途。建议在 `examples/` 下寻找真实的使用场景来验证和迭代完善我们的框架，使其更加健壮和全面。

---

## 关于 MoFA

[MoFA](https://mofa.ai/)（**Modular Framework for Agents**）是一个用于构建 AI Agent 的开源框架。我们的近期项目 **MoFA Studio** 是一个桌面应用，用于创建、运行和分享 AI 驱动的应用——基于 Rust 和 Makepad 构建，使用 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 实现 Apple Silicon 上的本地 ML 推理。

我们在系统工程、AI 基础设施和开发者工具方面指导 GSoC 贡献者解决真实世界的问题。

__官网:__ [mofa.ai](https://mofa.ai/)

__GitHub 仓库:__
- 核心运行时: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio 应用: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI 组件: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)


__组织联系邮箱:__ dev@mofa.ai
__GSoC 贡献者指南:__ [README.md](./README.md)

---

## 项目一：AgentForge —— 面向协作式 AI 开发的可组合插件系统

### 摘要

在 vibe coding 时代，单个开发者可以借助 LLM 快速生成 Agent 代码。然而，**将多位 vibe coder 的产出合并为一个连贯系统仍然是最大的未解难题**——人类的 review 带宽才是瓶颈，而非代码生成速度。

**AgentForge** 通过 mofa-rs 上“运行时原生”的两层协作模型来解决这个问题：第一层由 AI 生成契约优先的微模块，第二层由高阶 Agent 或人类负责组合与系统级决策。框架负责验证、冲突检测、可审计记录与回滚——实现团队级 vibe coding 而无合并噩梦。

__导师__: BH3GEI (Yao Li), lijingrs (AmosLi)

### 目标与想法

* **两层协作模型**:
  - **第一层（AI 生成微模块）**：在严格契约下生成小而自包含的模块（输入/输出 schema、依赖元数据、测试与风险标签）
  - **第二层（组合与系统控制）**：由高阶 Agent 或人类评审者负责架构级组合、质量门禁、合并/拒绝决策与回滚

* **运行时原生的 Vibe 流程**:
  - 将 vibe 任务生命周期直接接入 `mofa-runtime`（plan -> generate -> validate -> gate -> merge/rollback）
  - 产出必须是可验证工件（patch/test/report），而不是只输出自由文本
  - 通过 CLI/运行时 API 即可使用同一控制模型；UI 只是可选入口，不是核心交付

* **插件契约**：定义稳定的 `PluginManifest` 与 JSON Schema 契约（输入/输出、状态模式、生命周期钩子）
* **兼容性校验**：提供 `validate` 命令，在运行前检查契约兼容、类型/模式冲突与组合安全性
* **组合执行器**：实现基于 DAG 的插件编排与执行，并覆盖集成测试
* **运行时隔离**：以 Wasm sandbox 作为默认插件隔离机制，降低插件间干扰风险

### 最小验收（MVP）

- 在 `mofa` 主仓落地 `PluginManifest` 与 JSON Schema 契约
- 定义第一层微模块契约（I/O schema、依赖元数据、测试/风险元数据）
- 实现 `validate` 校验命令
- 交付一条第二层控制路径（高阶 Agent 或人工驱动），用于组合决策与质量门禁
- 交付一条端到端运行时流程：`intent -> micro-modules -> composition -> gate -> merge/rollback`
- 实现基于 DAG 的组合执行器
- 提供 Wasm sandbox 下的最小可运行插件样例
- 提供 3 类协作场景（同模块并行修改、跨模块依赖组合、门禁失败后的回滚）
- 补齐组合与失败路径的集成测试

### Stretch Goals

- 基于 `mofa-node-hub` 的语义节点检索
- 自然语言到流程组合的自动生成
- 插件配置/输出的自动化 UI 生成

### Out of Scope

- 把完整 no-code 工作流生成器作为主交付
- 一步到位的生产级插件市场/分发系统
- 将 IDE 产品功能或大规模 Studio 界面作为主交付
- 只有 prompt 演示、没有 patch/test/report 可验证工件的 vibe 流程

### 验收标准（Acceptance Criteria）

- `validate` 能在运行前拦截契约不兼容
- 第一层产出可经由第二层控制完成组合，并有明确门禁决策（合并/拒绝/回滚）
- 至少覆盖 1 类组合冲突与 1 条回滚路径测试
- 全流程具备可审计记录，可复现关键输入、门禁决策与输出
- 同一流程支持“高阶 Agent 控制”与“人工控制”两种第二层模式
- 3 类协作场景可在 CI 中端到端跑通
- 组合框架与测试代码已并入 `mofa` 主仓

### 落仓计划（Repo Landing Plan）

- **主落仓**：`mofa`（`mofa-kernel` / `mofa-foundation`）
- **可选演示接入**：`mofa-studio`

#### 示例场景

三位开发者各自 vibe code 一个 Agent 组件：
- 开发者 A：一个网页抓取 Agent 插件
- 开发者 B：一个摘要生成 Agent 插件
- 开发者 C：一个通知推送 Agent 插件

AgentForge 验证它们的接口兼容，将其组合为流水线，并运行整个系统——三位开发者无需阅读彼此的代码。

#### 参考链接

* https://github.com/mofa-org/mofa/tree/main
* https://github.com/mofa-org/mofa-studio

* https://makepad.dev/

__所需技能__: Rust, 插件架构设计, 类型系统, LLM 集成

__时间估计__: 175 小时（中等规模）

__难度__: 高

---

## 项目二：Studio 可观测性面板

### 摘要

MoFA Studio 运行涉及多个模型（ASR、LLM、TTS）和 Agent 交互的复杂 AI 流水线。目前，当出现问题或运行缓慢时，开发者对内部状况的可见性有限。本项目将构建一个**实时可观测面板**，直接嵌入 MoFA Studio，为开发者提供对模型性能、资源使用和 Agent 行为的即时洞察。

该面板将利用 MoFA Studio 现有的 [makepad-chart](https://github.com/mofa-org/makepad-chart) 和 [makepad-d3](https://github.com/mofa-org/makepad-d3) GPU 加速可视化组件。

__导师__: BH3GEI (Yao Li), yangrudan (CookieYang)

### 范围边界（与项目四区分）

- 本项目聚焦**在线观测与实时可视化**。
- 本项目不包含会话重放、时间旅行调试、断点调试（这些属于项目四）。
- 重点是把指标采集、聚合、推送和 Studio 面板打通。

### 目标与想法

* **后端指标服务**：构建运行时指标服务（REST + WebSocket）
* **Studio 可视化面板**：在 Studio 内落地实时观测面板
* **瓶颈可见性**：让开发者能直接看到延迟、吞吐、队列、模型状态等关键信号

### 最小验收（MVP）

- 稳定提供 `/api/agents`、`/api/metrics` 与 WebSocket `/ws`。
- 在 Studio 中落地至少 4 类核心视图：延迟、吞吐、队列深度、模型加载状态。
- 提供至少 1 个端到端示例，能定位出实际瓶颈。
- 提供基础测试与使用文档，支持他人复现。

### Stretch Goals

- 统一接入更多编排后端的监控（含 Dora 流程）
- 增强关联分析视图与筛选体验

### Out of Scope

- 会话重放、时间旅行调试能力
- 完整历史轨迹重建（属于项目四）

### 验收标准（Acceptance Criteria）

- 后端指标服务与 Studio 面板两部分都交付
- API 契约有文档且有测试覆盖
- 面板输出可用于定位至少 1 类真实瓶颈

### 落仓计划（Repo Landing Plan）

- **主落仓**：`mofa-studio`（UI + 指标服务集成）
- **配套集成**：`mofa`（`mofa-monitoring` / `mofa-runtime`）

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__所需技能__: Rust, HTTP/WebSocket 服务器 (axum/tokio), 实时数据可视化, Makepad UI

__时间估计__: 90 小时（8 周）

__难度__: 中

---

## 项目三：统一推理编排器（本地 + 云端）

### 摘要

MoFA Agent 应该在**本地运行时与云端 API**之间使用同一套推理契约。本项目要在 mofa-rs 中构建统一推理编排层：可插拔后端、策略路由，以及运行时级别的生命周期和调度管理。

对于本地推理，优先通过 Rust API 直接调用后端（`load_model()`、`Generate`、`forward()`），在可行场景下避免 HTTP 中间层。对于云端推理，需要在同一抽象下提供 provider 适配器（优先 OpenAI-compatible API）。

当前基于 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 的 macOS 路线是很好的本地参考，尤其适合统一内存上的零拷贝链路。但最终交付必须回到 `mofa` 主仓，并同时覆盖本地与云端路径。[mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) 是原型/参考仓，不是最终落仓目标。

__导师__: BH3GEI (Yao Li), lijingrs (AmosLi)

### 平台范围与硬件条件

- MoFA 推理不是只做 macOS。我们的目标是做一个通用、可插拔的推理框架，能在 macOS、Linux 以及后续更多后端上跑通。
- 这个项目也不是“只做本地”。提案范围必须包含**至少一条本地后端路径 + 一条云端 API 适配路径**。
- 本项目交付须并入 mofa-rs 主干（`mofa-foundation` / `mofa-runtime`），而不是只做一个独立 demo。
- `mofa-local-llm` 主要用于原型验证和实验展示；正式产出应回到 `mofa` 主仓落地。
- 跨平台是硬性要求：提案需包含一个已实现的本地后端（macOS 或 Linux），并给出另一个平台的兼容落地计划。
- 如果后期需要特定硬件或远程服务器做最终验证，请尽早和导师沟通。

### 交付边界（建议）

- **必须合入 `mofa` 主仓**：后端抽象接口、本地/云端路由策略、调度器核心、生命周期管理、与 `mofa-runtime` 的集成代码、核心测试。
- **可留在 `mofa-local-llm`**：演示 GUI、独立 demo server、实验性脚本与快速验证代码。
- **推荐做法**：先在 `mofa-local-llm` 验证，再将稳定能力回迁到 `mofa` 主仓。

### 实施路线

- **核心要求（必选）**：在同一 API 契约下同时支持本地后端与云端适配器。
- **实现聚焦（二选一，作为主验证平台）**：
  - macOS 聚焦：优先打通 OminiX-MLX 后端，验证统一内存下的调度与零拷贝链路。
  - Linux 聚焦：优先补齐 Linux 推理后端 + 调度器 + 基准测试。
- 对“非主验证平台”的跨平台兼容设计是必选项。

### 目标与想法

* **架构设计**:
  - 作为 mofa-rs 的核心组件实现（`mofa-foundation` 层）
  - 定义可插拔的统一抽象，覆盖本地运行时与云端 provider
  - 以 OminiX-MLX 作为默认 macOS 本地后端，并至少实现一个 OpenAI-compatible 云端适配器
  - 对 Agent 暴露统一请求/响应契约，不因本地或云端执行而改变
  - 设计 `ModelPool`（本地模型）与 provider 会话管理（云端）

* **生命周期管理**:
  - 按需模型加载，支持异步初始化
  - 基于空闲超时的自动卸载（LRU 淘汰）
  - Apple Silicon 统一内存压力监控
  - 带状态保存的优雅关闭

* **智能调度**:
  - 基于策略在本地与云端之间路由请求（如 local-first、latency-first、cost-first）
  - 基于任务类型（ASR/LLM/TTS）和可用性将请求路由到正确的模型
  - 内存感知准入控制：内存受限时拒绝或延迟请求
  - 云端 provider 失败重试与故障切换
  - 动态精度降级（如压力下自动从 8-bit 切换到 4-bit 量化）

* **推理流水线**:
  - 在本地后端支持时，通过 MLX Array 零拷贝将多个模型串联为流水线（ASR → LLM → TTS）
  - 支持混合流水线（如本地 ASR/TTS + 云端 LLM，或本地优先 + 云端回退）
  - LLM 流式 token 输出直接输入 TTS
  - 分阶段延迟追踪和瓶颈报告

* **降级策略**:
  - 当主模型失败或资源受限时自动回退到更小模型
  - 服务质量级别与相应的模型选择

* **集成**:
  - 向 Studio 可观测性面板暴露调度状态和指标（项目二）
  - 为 Agent 提供清晰 API，请求推理而无需管理模型生命周期

### 最小验收（MVP）

- 在 `mofa` 主仓落地统一推理抽象。
- 在同一运行时契约下交付至少一个本地后端 + 一个云端 API 适配器。
- 实现调度器核心、生命周期管理、本地/云端路由策略，并覆盖基础测试。
- 完成与 `mofa-runtime` 的基本集成，Agent 可通过统一接口发起推理请求。
- 交付可复现 benchmark（延迟、吞吐、内存占用、本地/云端路由行为）。

### Stretch Goals

- 多云 provider 支持与成本感知路由
- 加入更细粒度的动态精度切换策略与负载自适应
- 在所选路线之外补充额外后端实现

### Out of Scope

- 只做 GUI demo，不做主仓运行时集成
- 只能本地运行、无法与云端 API 互通的设计
- 绕开后端抽象的临时平台特化 hack

### 验收标准（Acceptance Criteria）

- 核心编排能力已并入 `mofa-foundation` / `mofa-runtime`
- 同一 Agent API 可通过配置在本地、云端和混合路径运行
- 选定本地路线（macOS 或 Linux）具备端到端可运行链路与测试
- 至少一个故障切换场景（本地不可用切云端，或反向）有测试覆盖
- benchmark 可被导师复现并复核

### 落仓计划（Repo Landing Plan）

- **主落仓**：`mofa`（`mofa-foundation` / `mofa-runtime`）
- **原型/参考仓**：`mofa-local-llm`（非最终交付落点）

#### 示例场景

一个语音助手流水线包含：
- FunASR（ASR，~2GB）
- Qwen（LLM，~8GB）
- GPT-SoVITS（TTS，~4GB）

在 16GB MacBook 上，三者无法同时驻留。编排器将：
- 保持本地 ASR/TTS 以保障低延迟交互
- LLM 默认走本地，内存压力或延迟超阈值时自动回退云端
- 本地 LLM 可用时走零拷贝链路；不可用时切换云端，Agent 代码无需修改
- 资源恢复后自动回切到本地路径

#### 参考链接

* https://github.com/mofa-org/mofa-local-llm
* https://github.com/OminiX-ai/OminiX-MLX
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__所需技能__: Rust, 系统编程, 资源管理, Apple Silicon 或 Linux GPU 计算

__时间估计__: 175 小时（中等规模）

__难度__: 高

---

## 项目四：会话记录器与可视化调试器

### 摘要

多 Agent 系统是出了名的难调试。当 Agent 之间交换数十条消息和状态变更时，传统日志变得难以阅读。在 vibe coding 时代尤其如此——LLM 生成的 Agent 代码往往在演示中正常工作，但在生产环境中莫名失败。

本项目为 MoFA 构建一个**时间旅行调试器**——一个使开发者选择在 mofa-rs 上运行 Agent 的差异化能力。把它想象成"Agent 的 Chrome DevTools"：加载任何 Agent（手写或 vibe code 生成的），记录执行过程，检查消息流，并以修改后的状态重放。

构建此调试器同时也是对 mofa-rs 的一次**架构审计**——添加插桩钩子的过程将迫使框架为事件捕获、状态快照和消息拦截定义清晰的内部 API。

__导师__: BH3GEI (Yao Li), lijingrs (AmosLi)

### 分阶段交付（强制）

1. 事件采集 + 存储 + CLI 回放
2. 时间线 UI
3. 断点与状态差异对比

### Schema 版本策略（强制）

- 先定义事件模型与 schema versioning
- 在扩展功能前明确兼容与迁移策略，避免后续返工

### 目标与想法

* **事件拦截**：
  - Hook 进 `mofa-kernel` 消息总线捕获所有 Agent 事件
  - 序列化消息流、状态转换和工具调用
  - 长时间会话的高效存储格式
  - 定义清晰、稳定的 Hook API，使其成为 mofa-rs 公共契约的一部分

* **时间线可视化**：
  - Makepad 集成或基于 Web 的时间线视图
  - 查看哪个 Agent 何时向谁发送了什么消息
  - 按 Agent、消息类型或时间范围筛选
  - 毫秒到小时尺度的缩放

* **状态检查**：
  - 在关键点捕获 Agent 状态快照
  - 差异视图：比较消息处理前后的 Agent 状态
  - 检查内存、上下文和内部变量

* **时间旅行调试**：
  - 可变速度回放记录会话
  - 暂停、前进/后退执行
  - 在特定消息模式上设置断点
  - 以修改后的输入重新运行特定 Agent

* **Vibe Coding 支持**：
  - 无需修改即可加载和调试 LLM 生成的 Agent
  - 识别 vibe code Agent 中的常见失败模式
  - 导出记录作为 LLM 辅助修复的上下文

* **集成**：
  - 可选 Studio 面板实现无缝开发工作流
  - 导出记录用于 bug 报告或文档

### 最小验收（MVP）

- 在 `mofa-kernel` 完成事件采集 Hook
- 提供带版本号的可持久化存储格式
- 提供 CLI 回放能力，可稳定按步骤重放关键轨迹

### Stretch Goals

- 更完整的时间线交互和断点 UI 体验
- LLM 辅助的失败模式分析

### Out of Scope

- 只有 UI 查看器，没有可靠回放内核
- 无版本管理的临时轨迹格式

### 验收标准（Acceptance Criteria）

- 同输入 + 同运行时版本下，可稳定复现关键失败轨迹
- schema 版本策略与迁移说明文档齐全
- CLI 回放与至少一条 UI 路径可用

### 落仓计划（Repo Landing Plan）

- **主落仓**：`mofa`（`mofa-kernel` / `mofa-monitoring`）
- **可选 UI 集成**：`mofa-studio`

#### 使用场景

开发者 vibe code 了一个 5-Agent 工作流。在简单测试中正常，但在真实数据下间歇性失败。使用记录器：
1. 在启用记录的情况下将 vibe code 的 Agent 加载到 mofa-rs
2. 发生失败时打开轨迹
3. 查看导致错误的精确消息序列
4. 在最后已知良好点检查 Agent 状态
5. 以修改回放测试修复
6. 导出轨迹作为上下文，让 LLM 生成修复方案

#### 参考链接

* https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring

__所需技能__: Rust, 数据可视化, 系统设计, 调试工具

__时间估计__: 175 小时（中等规模）

__难度__: 高

---

## 项目五：MoFA Input —— 推理栈迁移至 MoFA 原生推理层

### 摘要

[MoFA Input](https://github.com/mofa-org/mofa-input) 是一个完全在本地运行的 macOS 全局语音输入法。目前通过 C++ 互操作层使用 llama.cpp + GGUF 模型进行 ASR（Whisper）和 LLM（Qwen）推理。本项目将推理栈迁移至 MoFA 自身的原生 Rust 推理层（macOS 上当前以 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 为后端，见项目三），完全替代 C++ llama.cpp 后端。

为什么迁移？纯 Rust 消除了 C++ 互操作的复杂性，MLX 的 Metal GPU 加速在 Apple Silicon 上快于 llama.cpp，且与 MoFA 的可插拔推理后端（项目三）对齐，确保 MoFA Input 能自动受益于未来的后端改进，无需额外迁移工作。

__导师__: BH3GEI (Yao Li), yangrudan (CookieYang)

### 范围选项

- **收敛版（90h）**：ASR 迁移 + 接口层集成
- **全量版（175h）**：ASR + LLM + C++ 到 Rust 全量迁移

### 回退策略（强制）

- 迁移期间保留旧路径 feature flag
- 若延迟/准确率超出约定阈值，可安全切回旧路径

### 目标与想法

* **ASR 迁移**：将当前基于 llama.cpp 的 Whisper ASR 替换为 MoFA 推理层（macOS 上如 `funasr-mlx` 或 `funasr-nano-mlx`）。验证准确率和延迟与当前实现的对比
* **LLM 迁移**：将 Qwen GGUF 推理替换为 MoFA 推理层（macOS 上如 `qwen3-mlx`，safetensors 格式）。确保流式 token 输出与现有 UI 兼容
* **C++→Rust 迁移**：通过 MoFA 的后端抽象（项目三）以纯 Rust 推理调用取代现有 C++ llm_server（llama.cpp），消除 C++ 互操作层。保持当前 macOS 输入法架构（Fn 热键、悬浮球、历史窗口）
* **性能基准测试**：在代表性硬件（M1/M2/M3/M4）上对比迁移前后的延迟、内存占用和准确率
* **模型管理**：集成 `~/.mofa/models/` 模型存储，统一使用 OminiX-MLX 的 safetensors 格式

### 最小验收（MVP）

- 完成所选范围，并给出可复现 benchmark 报告
- 实现并验证旧栈回退路径（feature flag）
- 保证与现有输入法核心交互链路兼容

### Stretch Goals

- 在收敛版基础上推进到全量迁移
- 扩展更多模型兼容与性能调优预设

### Out of Scope

- 未保留回退路径就直接替换线上核心链路
- 无迁移前后对比数据的“无测量迁移”

### 验收标准（Acceptance Criteria）

- 迁移链路可运行，且在代表性硬件上有基准数据
- 回退策略经过测试并有文档
- 核心用户路径（语音输入到文本输出）无严重回归

### 落仓计划（Repo Landing Plan）

- **主落仓**：`mofa-input`
- **共享依赖**：`mofa`（项目三的推理抽象层）

#### 参考链接

* https://github.com/mofa-org/mofa-input
* https://github.com/OminiX-ai/OminiX-MLX

__所需技能__: Rust, C++/Rust 互操作, macOS 开发, Apple Silicon

__时间估计__: 90 小时（收敛版）或 175 小时（全量版）

__难度__: 中

---

## 项目六：Makepad AI 应用组件库

### 摘要

MoFA 的桌面应用（Studio、moly-ai）基于 [Makepad](https://makepad.dev/) 构建——一个 Rust 编写的 GPU 加速 UI 框架。传统“组件列表 + 人工拼装”的方式并不适合 AI 原生产品：Agent 生成代码很快，但面对通用组件库时缺少可控、可验证的任务语义契约。

本项目保留 `makepad-ai-toolkit` 名称，但核心转向**AI 生成 UI 的运行时模型**：由 Agent 生成结构化 UI 意图/补丁，toolkit 负责校验与安全渲染，Studio/MoFA 运行时负责实时管理。主价值是“可控生成 + 运行时集成”，而不是做一个大而全的通用组件清单。

__导师__: BH3GEI (Yao Li), yangrudan (CookieYang)

### 目标与想法

* **AI 原生 UI 契约**:
  - 定义 Agent 生成 UI 的结构化 schema（意图 + 增量补丁）
  - 支持面向任务语义的 UI 原语与可组合布局，而非仅低层组件调用
  - 提供校验规则、版本策略和清晰错误报告

* **生成运行时**:
  - 打通 Agent 流式 UI 补丁到 Studio 实时渲染的运行时链路
  - 增加高风险动作门禁（审批、拒绝、回滚）
  - 当生成失败时可回退到手工/静态 UI 路径，保证可用性

* **MoFA 集成（主交付）**:
  - 与 `mofa-studio` 集成，使生成 UI 可被实时观察、控制和更新
  - 与 `mofa` 运行时事件对接（agent 状态、tool 调用、trace 元数据）
  - 与项目二解耦：项目六提供“生成能力与运行时”，不承担编排产品本体

* **组件工作（有限且有目的）**:
  - 仅在 AI 生成链路确实需要时补充/完善基础组件
  - 优先复用现有 Makepad 生态能力，避免重复造轮子

### 最小验收（MVP）

- 定义并文档化 AI 生成 UI 契约（schema + patch 协议 + 校验规则）
- 交付一条端到端运行时示例：`agent output -> UI patch stream -> Studio render -> user feedback -> runtime update`
- 至少 2 条真实 MoFA 工作流支持运行时生成/更新 UI
- 门禁行为（审批/拒绝/回滚）具备测试覆盖与可复现 demo 步骤

### Stretch Goals

- 多 provider 生成适配与更细粒度策略控制
- 更好的 prompt-to-UI 模板与场景预设
- 发布 crate 并维护版本化发布说明

### Out of Scope

- 做大而全通用组件库、但不提供 AI 生成运行时价值
- 从零重写现有兄弟项目能力（例如 A2UI renderer）
- 只做组件展示页，不做产品接入

### 验收标准（Acceptance Criteria）

- 至少 2 条 MoFA 工作流在 `mofa-studio` 中支持运行时 AI 生成 UI 更新
- 非法/高风险 UI 补丁可被拦截并提供清晰错误与安全回退
- 审批/拒绝/回滚路径有测试覆盖且可复现
- toolkit 契约与运行时 API 文档完整，可被贡献者复用

### 落仓计划（Repo Landing Plan）

- **主落仓**：`makepad-ai-toolkit`（新仓）
- **必须联调落地**：`mofa-studio`
- **必须运行时对接**：`mofa`（事件/trace 接口）

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/makepad-element
* https://github.com/ZhangHanDong/makepad-component
* https://makepad.dev/

__所需技能__: Rust, UI/UX 设计, Makepad 框架

__时间估计__: 90 小时（8 周）

__难度__: 中
