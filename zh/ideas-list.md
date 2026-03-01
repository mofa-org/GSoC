# MoFA GSoC 2026 项目提案

> 中文版 |  [English Version](../ideas-list.md)

本文档包含 Google Summer of Code 2026 的详细项目提案。整体框架已定，具体细节可在导师指导下根据贡献者建议进行调整。我们鼓励贡献者提出自己的方案——以下想法是起点，而非刚性规范。

> **开始之前**：请先在相关 GitHub issue 下留言表达兴趣，并简要描述你的思路。**等待维护者分配后再开始编码。** 这可以避免重复劳动。详见[贡献流程](./README.md#在-gsoc-之前贡献)。
>
> **Proposal 基线要求**：你的 proposal 必须包含架构蓝图（组件边界、接口契约、数据流、故障/恢复策略、测试计划）。评估基于质量与深度，而非数量。

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
## 项目 1: Cognitive Gateway — AI Agent 与物理-数字世界的神经接口

### 参考平台

**AgentGateway** — Linux 基金会的 AI Agent 网关平台，提供 LLM/MCP/A2A 协议支持、智能路由、安全和可观测性。

**Plano** — AI 原生代理服务器，提供代理编排、模型路由、过滤器链和提示目标管理。

本项目综合参考上述平台，并扩展 IoT 能力抽象层以实现物理世界交互。

### 简要描述

构建一个 Rust 原生的高性能网关，将 AI Agent 连接到数字世界（LLM、MCP 工具、A2A 通信）和物理世界（IoT 设备、传感器、执行器），使 Agent 能够通过语义能力 API 感知和交互现实世界。

### 详细描述

当今的 AI Agent 被困在数字世界中——它们可以处理文本、生成图像、调用 API，但无法感知或交互周围的物理世界。同时，传统 API 网关在处理有状态的 AI 协议（如 MCP、A2A）时面临根本性挑战。本项目构建 **Cognitive Gateway**，一个从第一性原理出发、专为 AI Agent 通信设计的统一神经系统。

**架构设计**：

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
│  │  (路由引擎)   │  │  Chain       │  │  Registry            │  │
│  └──────────────┘  └──────────────┘  └──────────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  │
│  │  Auth/RBAC   │  │  Rate        │  │  Event Bus           │  │
│  │  (安全层)    │  │  Limiter     │  │  (事件总线)          │  │
│  └──────────────┘  └──────────────┘  └──────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                              │
                    Southbound Adapters
                              ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│ LLM API     │  │ MCP Server  │  │ IoT Hub     │  │ Agent-to-   │
│ (OpenAI等)  │  │ (工具联邦)  │  │ (HA/MQTT)   │  │ Agent (A2A) │
└─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘
```

**数字世界接口**（对标 AgentGateway + Plano）：
- **LLM 网关**：多提供商统一接口（OpenAI、Anthropic、Gemini）、推理感知路由、token 计数与成本归属
- **MCP 网关**：工具联邦、OpenAPI 到 MCP 转换、工具发现与注册
- **A2A 网关**：Agent 到 Agent 安全通信、能力发现、协作协议
- **智能路由**：负载均衡、熔断、故障转移、基于模型队列的调度
- **过滤器链**：请求/响应预处理、内容审核、提示注入防护
- **安全层**：认证（JWT、API Key、OAuth 2.0）、授权（RBAC + CEL 表达式）、审计日志

**物理世界接口**（IoT 能力抽象）：
- **能力抽象层**：语义 API（`speaker.tts()`、`camera.capture()`、`sensor.subscribe()`、`light.setBrightness()`）
- **适配器插件**：Home Assistant、MQTT Broker、RTSP、厂商云 API
- **事件流**：设备在线/离线、状态变更、运动检测、语音唤醒
- **数字孪生**：设备模拟、场景回放、离线测试

### 预期成果（Deliverables）

**Phase 1: 核心框架（第 1-4 周）**
- `mofa-gateway` crate 基础架构
- 路由引擎：基于 trie 的路径匹配、负载均衡策略
- 过滤器链框架：可插拔的请求/响应处理管道
- 配置系统：YAML 配置 + 热更新支持

**Phase 2: 数字世界接口（第 5-10 周）**
- LLM 网关：OpenAI 兼容 API、多提供商路由、token 遥测
- MCP 网关：工具注册、调用代理、OpenAPI 转换
- A2A 网关基础：Agent 发现、安全通信
- 认证授权：JWT 验证、RBAC 策略引擎

**Phase 3: 物理世界接口（第 11-16 周）**
- 能力抽象层：`Capability` trait、`CapabilityRegistry`、schema 版本管理
- Home Assistant 适配器：REST/WebSocket API 集成
- MQTT 适配器：订阅/发布、设备发现
- 事件总线：发布/订阅、事件过滤、持久化

**Phase 4: 集成与部署（第 17-20 周）**
- 控制平面：REST API（`GET /capabilities`、`POST /invoke`）、WebSocket 事件流
- 端到端演示：3 个场景（纯数字、纯物理、混合协作）
- Docker Compose 部署方案
- 文档：架构设计、API 参考、适配器开发指南

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的网关服务，支持 HTTP 请求路由
- 至少 1 个 LLM 提供商（OpenAI）的路由支持
- 至少 1 个 IoT 适配器（Home Assistant 或 MQTT）
- 基本的认证（API Key）和限流功能
- 简单的命令行演示脚本

### 扩展目标（Stretch Goals）

- **高级路由**：推理感知路由（GPU 队列深度、KV cache 利用率）
- **完整语音链路**：流式音频、连续对话、打断控制
- **可观测性集成**：OpenTelemetry 追踪、Prometheus 指标、Grafana 仪表板
- **更多适配器**：Zigbee、Socket.IO、厂商云 API（如小米、涂鸦）
- **数字孪生框架**：设备模拟、场景回放

### 验收标准（Acceptance Criteria）

- [ ] Agent 侧代码不包含具体协议细节，仅通过能力 API 访问服务
- [ ] 网关可持续运行 24 小时无崩溃，支持配置热更新
- [ ] 至少 2 类异构后端（LLM + IoT）在同一能力层下可工作
- [ ] 事件/能力 schema 有版本策略，文档中说明兼容规则
- [ ] 单元测试覆盖率 ≥ 70%，集成测试覆盖核心场景
- [ ] 提供可复现的部署文档和演示脚本

### 所需技能

- **必需**：扎实的 Rust 编程能力（async/await、trait 设计、错误处理）
- **必需**：理解 API 网关模式和反向代理原理
- **必需**：熟悉 HTTP/WebSocket 协议
- **优先**：IoT 协议经验（MQTT、Home Assistant）
- **优先**：事件驱动架构和消息队列经验
- **优先**：LLM API 集成经验（OpenAI、Anthropic）

### 难度

**高**（350 小时）

### 导师

待定

## 项目 2: Cognitive Observatory — AI Agent 系统的全景监控台

### 参考平台

**LangSmith** — LangChain 提供的统一 LLM 应用开发平台，涵盖可观测性、评估、提示工程和部署管理。本项目实现完整的 LangSmith 功能集，包括分布式追踪、实时监控、洞察分析、评估框架、提示版本控制和监控仪表板。

### 简要描述

构建一个 LangSmith 级别的可观测性与评估平台，为 AI Agent 生命周期的各个阶段提供全景式可见性——从开发调试、质量评估到生产监控和持续改进。

### 详细描述

当多 Agent 系统做出错误决策时，问题不是"哪里出错了？"——而是"我该从哪里开始找？"传统调试工具对 AI 系统的独特挑战视而不见：非确定性 LLM 输出、分布式 Agent 决策、复杂的工作流拓扑。

本项目构建 **Cognitive Observatory**，实现 LangSmith 的完整功能矩阵：

**可观测性（Observability）**：
- **请求追踪（Tracing）**：详细调用链路、错误与延迟定位、非侵入式集成、OpenTelemetry 兼容
- **实时监控（Monitoring）**：预构建仪表板（请求数、错误率、P50/P99 延迟、Token 使用量、成本）、自定义图表、Webhook 警报
- **洞察分析（Insights）**：对话聚类、问题定位、模式发现

**评估（Evaluation）**：
- **离线评估**：数据集管理、基准测试、回归检测、单元测试、回测
- **在线评估**：实时质量监控、异常检测、生产反馈收集
- **评估器**：人工评审、代码评估、LLM-as-judge、成对比较
- **持续改进**：评估结果关联追踪、问题转测试用例

**提示工程（Prompt Engineering）**：
- **提示中心**：提示模板存储、变量机制、Playground 即时测试
- **版本控制**：提交记录、标签标记、分支与合并
- **性能评估**：提示与数据集关联、自动评分、多版本对比

**部署与协作**：
- **多工作区**：组织/工作区层级管理、环境隔离
- **权限控制**：RBAC 角色（管理员/编辑/观察者）、自定义角色
- **数据管理**：加密存储、数据驻留、敏感数据屏蔽

### 预期成果（Deliverables）

**Phase 1: 核心追踪与可观测性（第 1-4 周）**
- `mofa-observability` crate 基础架构
- OpenTelemetry 兼容的分布式追踪系统
- LLM 遥测：提示/响应日志、Token 计数、成本归属
- 基础监控仪表板：请求统计、错误率、延迟分布
- 追踪数据存储：内存 + PostgreSQL 后端

**Phase 2: 评估框架（第 5-10 周）**
- 离线评估系统：数据集管理、测试用例组织
- 评估器框架：`Evaluator` trait、LLM-as-judge、代码评估
- 在线评估：实时质量监控、异常检测规则
- 评估结果存储与查询 API
- 回归检测与基准测试工具

**Phase 3: 提示工程与时间旅行（第 11-16 周）**
- 提示中心：模板存储、变量系统、版本控制
- 提示 Playground：即时测试、多轮对话模拟
- 时间旅行调试：状态快照、对话回放、反事实探索
- 洞察分析：对话聚类、模式发现算法
- 人类反馈集成：标注队列、评分系统

**Phase 4: 仪表板与集成（第 17-20 周）**
- Web 仪表板增强：React 前端、实时 WebSocket 推送
- 警报系统：阈值配置、Webhook 通知（Slack/邮件）
- Grafana 集成：Prometheus 指标导出
- RBAC 权限控制：角色管理、API 密钥
- Docker Compose 部署方案
- 文档：API 参考、用户指南、集成示例

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的追踪服务，支持 HTTP/gRPC 数据摄入
- 至少 1 种评估器（LLM-as-judge 或代码评估）
- 基础 Web 仪表板，显示追踪列表和详情
- 简单的离线评估流程（数据集 → 评估 → 结果）
- 命令行工具提交追踪数据

### 扩展目标（Stretch Goals）

- **高级洞察**：AI 驱动的自动问题诊断、根因分析
- **多租户支持**：完整的工作区隔离、组织管理
- **SSO 集成**：OAuth 2.0、SAML 企业认证
- **性能优化**：追踪数据压缩、冷热分层存储
- **SDK 支持**：Python/TypeScript SDK 便于应用集成
- **Agent 部署**：集成 LangSmith 风格的 Agent Server

### 验收标准（Acceptance Criteria）

- [ ] 追踪系统可捕获完整的 Agent 执行链路（输入、输出、工具调用、LLM 请求）
- [ ] 支持 OpenTelemetry 标准导入导出，与 Jaeger/Grafana 兼容
- [ ] 评估框架支持至少 3 种评估器类型
- [ ] 离线评估可对数据集执行并生成评分报告
- [ ] 在线评估可实时检测生产异常并触发警报
- [ ] 提示版本控制支持提交历史、标签、回滚
- [ ] 时间旅行调试可回放任意历史会话
- [ ] Web 仪表板响应时间 < 500ms，支持实时更新
- [ ] 单元测试覆盖率 ≥ 70%，集成测试覆盖核心场景
- [ ] 提供可复现的部署文档和演示脚本

### 所需技能

- **必需**：扎实的 Rust 编程能力（async/await、trait 设计、错误处理）
- **必需**：理解 OpenTelemetry 和分布式追踪原理
- **必需**：熟悉 SQL 数据库（PostgreSQL）和数据建模
- **优先**：可观测性工具经验（Jaeger、Grafana、Prometheus）
- **优先**：前端经验（TypeScript/React）
- **优先**：LLM 评估方法（LLM-as-judge、RAGAS 等）

### 难度

**高**（350 小时）

### 导师

待定

## 项目 3: Neural Workflow Engine — 带时间持久化和响应式流的状态图

### 参考平台

**LangGraph** — 一个用于构建有状态、多参与者 LLM 应用的库，构建在 LangChain 之上。本项目实现完整的 LangGraph 功能，包括 StateGraph、检查点、流式处理、人机协同和持久化。

### 简要描述

构建一个 LangGraph 风格的工作流引擎，具备自动检查点、崩溃恢复和响应式流，使复杂的 AI 工作流像数据库事务一样可靠。

### 详细描述

复杂的 AI 工作流不是线性的——它们分支、循环、并行化，有时还会失败。**Neural Workflow Engine** 提供类似大脑的架构来编排这些复杂模式，并内置时间持久化。

**StateGraph 架构**：
- 动态拓扑：循环、条件边、运行时路由
- 状态管理：带差异更新的不可变快照
- 并行执行，含 fork/join 模式
- 错误处理，含补偿事务

**时间持久化**：
- 自动检查点（基于时间、步骤、谓词）
- 多后端存储：内存、PostgreSQL、SQLite、S3、Redis
- 带增量压缩的高效序列化
- 崩溃恢复，自动状态恢复

**响应式流**：
- 流式优先设计，含背压
- 流控制策略：缓冲、丢弃、节流、取最新
- 并发管理，含优先队列
- 流组合：合并、拆分、过滤、转换

### 预期成果

- `CheckpointManager` trait，支持可插拔后端
- 可配置背压的 `StreamingExecutor`
- 高效二进制编码的 `StateSerializer`
- 含故障注入测试的恢复模块
- 动态拓扑修改 API
- 工作流版本控制
- 基准测试套件
- LangGraph 迁移指南

### 所需技能

- **必需**：扎实的 Rust（异步、序列化、数据库）
- **必需**：理解图算法和状态机
- **优先**：流式系统经验
- **优先**：时序数据库经验

### 难度

**高**（350 小时）

### 导师

待定

---

## 项目 四: Cognitive Swarm Orchestrator — 认知集群编排与人机协同治理

### 参考平台

**OpenClaw** — 7×24 小时任务自动化平台，强调单 Agent 执行能力。本项目**不复制** OpenClaw 的自动化路线，而是构建 **Swarm 编排层**。

**ZeroClaw** — 轻量级 Rust Agent 运行时，强调性能。本项目**不竞争**运行时，而是构建**协作治理层**。

**差异化定位**：2026 是"编排时代"——从单个超级 Agent 到专业化 Agent **Swarm 协作**。本项目构建 MoFA 生态系统的**核心编排与治理引擎**。

### 简要描述

构建一个 **Swarm 编排引擎**，协调多个专业化 Agent 协作完成复杂任务，结合 MoFA 的 Gateway（能力接入）、Smith（可观测性）、SDK（多语言）形成完整生态闭环，并通过人机协同（HITL）机制确保关键决策受人类监督。

### 详细描述

**问题**：OpenClaw 证明了单 Agent 自动化的价值，但复杂任务需要**多 Agent 协作**——就像公司依赖不同角色的团队而非一个全能员工。2026 的趋势是从"寒武纪大爆发"（模型多样性）到"物种收敛"（**编排与集成**）。

**解决方案**：**Cognitive Swarm Orchestrator** 是 MoFA 生态系统的"大脑中枢"，它不直接执行任务，而是：
1. **理解任务** → 分解为子任务
2. **组建团队** → 动态匹配 Agent 能力
3. **编排协作** → 选择最优协作模式
4. **监督执行** → 通过 Smith 可观测
5. **治理决策** → 关键节点人类审批

```
┌─────────────────────────────────────────────────────────────────┐
│                     MoFA Ecosystem Integration                   │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────┐   ┌─────────────────────────────────────────┐  │
│  │   Gateway   │←→│         Cognitive Swarm Orchestrator      │  │
│  │ (能力接入)   │   │  ┌─────────┐ ┌─────────┐ ┌──────────┐   │  │
│  └─────────────┘   │  │ Task    │ │ Swarm   │ │  HITL    │   │  │
│                    │  │ Analyzer│ │ Composer│ │ Governor │   │  │
│  ┌─────────────┐   │  └─────────┘ └─────────┘ └──────────┘   │  │
│  │    SDK     │←→│       ↓            ↓            ↓         │  │
│  │ (多语言)    │   │  ┌─────────────────────────────────────┐ │  │
│  └─────────────┘   │  │     Coordination Patterns Engine     │ │  │
│                    │  │  Sequential │ Parallel │ Debate │ ... │ │  │
│  ┌─────────────┐   │  └─────────────────────────────────────┘ │  │
│  │   Smith    │←→└─────────────────────────────────────────┘  │
│  │ (可观测性)  │                                               │
│  └─────────────┘                                               │
└─────────────────────────────────────────────────────────────────┘
```

**核心模块**：

**1. Task Analyzer（任务分析器）**
- LLM 驱动的任务分解：复杂任务 → 子任务 DAG
- 依赖分析与关键路径识别
- 子任务难度与风险评级（用于 HITL 决策）
- 输出结构化执行计划

**2. Swarm Composer（集群编排器）**
- **动态团队组建**：基于 Agent 能力注册表自动匹配
- **7 种协作模式**：Sequential、Parallel、Debate、Consensus、MapReduce、Supervision、Routing
- **LLM 模式推荐**：根据任务特征自动选择最优模式
- **负载均衡**：考虑 Agent 繁忙度、成功率、专业领域

**3. HITL Governor（人机协同治理器）**
- **5 阶段 Secretary 模式**：Receive → Clarify → Schedule → Monitor → Report
- **智能审批路由**：基于风险等级路由到合适的审批人
- **上下文组装**：人类审核前自动汇总关键信息
- **AI 辅助决策**：生成决策建议与风险分析
- **升级机制**：超时/争议自动升级

**4. Governance Layer（治理层）**
- **SLA 管理**：截止日期追踪、延迟预警
- **审计追踪**：完整决策链路记录（满足合规要求）
- **多通道通知**：WebSocket、Email、Slack、Telegram、钉钉
- **RBAC 权限**：角色定义、能力授权

**5. Ecosystem Integration（生态集成）**
- **Gateway 集成**：通过能力 API 访问物理/数字世界（Speaker、Camera、Sensor 等）
- **Smith 集成**：追踪数据自动上报、评估结果反馈优化
- **SDK 集成**：Python/Go/Kotlin/Swift 编排 API

### 预期成果（Deliverables）

**Phase 1: 核心编排引擎（第 1-4 周）**
- `mofa-orchestrator` crate 基础架构
- `TaskAnalyzer`：任务分解、DAG 生成
- `SwarmComposer`：动态团队组建、能力匹配
- 基础协调模式：Sequential、Parallel

**Phase 2: 协作模式与 HITL（第 5-10 周）**
- 完整 7 种协作模式实现
- `HITLGovernor`：5 阶段 Secretary 生命周期
- 审批工作流引擎：角色路由、升级机制
- AI 辅助决策：上下文组装、建议生成

**Phase 3: 治理与生态集成（第 11-16 周）**
- `GovernanceLayer`：SLA 管理、审计追踪
- 多通道通知适配器（Slack、Telegram、Email、钉钉）
- Gateway 集成：能力 API 调用
- Smith 集成：追踪数据上报、评估反馈

**Phase 4: SDK 与生产就绪（第 17-20 周）**
- 编排 API 多语言绑定（Python/Go/Kotlin/Swift）
- Web Dashboard：Swarm 状态、审批队列、审计日志
- CLI 工具：`mofa swarm deploy`、`mofa swarm status`
- Docker Compose 部署方案
- 文档：编排指南、最佳实践、集成示例

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的编排服务，支持任务分解和子任务调度
- 至少 2 种协作模式（Sequential + Parallel）的完整实现
- 基础 HITL 流程：人工审批 API + 简单 Web 界面
- 与 Gateway 的集成演示（通过能力 API 调用设备）
- 简单的命令行演示：`mofa swarm run examples/swarm_demo.yaml`

### 扩展目标（Stretch Goals）

- **高级模式**：Debate、Consensus 模式的 LLM 驱动优化
- **自适应调度**：基于历史数据的学习型任务分配
- **跨集群编排**：多租户、多区域 Swarm 协作
- **Smith 深度集成**：编排质量评估、自动模式推荐
- **声明式 DSL**：YAML 定义 Swarm 编排规则

### 验收标准（Acceptance Criteria）

- [ ] 支持至少 5 种协作模式，可通过 API 动态选择
- [ ] 任务分解生成有效的 DAG，支持依赖并行执行
- [ ] HITL 流程完整：审批请求 → 人工响应 → 执行继续
- [ ] 审计追踪覆盖所有关键决策节点
- [ ] 与 Gateway 集成：Agent 可通过能力 API 访问设备
- [ ] 与 Smith 集成：追踪数据自动上报
- [ ] 单元测试覆盖率 ≥ 70%，集成测试覆盖核心场景
- [ ] 提供可复现的部署文档和演示脚本

### 与竞品对比

| 特性 | OpenClaw | ZeroClaw | **本项目 (Swarm Orchestrator)** |
|------|----------|----------|-------------------------------|
| **定位** | 单 Agent 自动化 | 轻量运行时 | **多 Agent 编排** |
| **执行模式** | 独立执行 | 独立执行 | **协作编排** |
| **HITL** | 基础 | 无 | **完整治理流程** |
| **可观测** | 基础日志 | 无 | **Smith 集成** |
| **能力接入** | 有限 | 无 | **Gateway 集成** |
| **多语言** | 无 | 无 | **SDK 集成** |

### 所需技能

- **必需**：扎实的 Rust 编程（async/await、trait 设计）
- **必需**：理解分布式系统和协作模式
- **必需**：理解 DAG 和任务调度原理
- **优先**：LLM 应用开发经验（提示工程、Agent 模式）
- **优先**：工作流引擎或编排系统经验
- **优先**：通知系统和消息队列经验

### 难度

**高**（350 小时）

### 导师

待定

---

## 项目 五: Cognitive Mesh Platform — 认知网格：共享记忆、可扩展智能与多语言生态

### 参考平台

**LangChain** — 全面的 LLM 应用框架。本项目实现 LangChain 的记忆系统、RAG 基础设施。

**UniFFI + Plugin Ecosystems** — Mozilla 的多语言绑定 + 现代插件架构。本项目构建完整的可扩展生态。

**设计理念**：将"集体智能"与"可扩展性"深度融合——**知识通过插件扩展，能力通过多语言传播**。

### 简要描述

构建一个**认知网格平台**，通过多层记忆和 RAG 基础设施实现知识共享，通过双运行时插件系统实现能力扩展，通过多语言 SDK 实现生态普及——让 Agent 的智能可积累、可扩展、可普及。

### 详细描述

**问题**：单个 Agent 受限于训练数据和上下文窗口。更严重的是，每个开发者都在重复构建相似的记忆系统、向量存储、嵌入流水线——**智能无法积累，能力无法复用**。

**解决方案**：**Cognitive Mesh Platform** 构建一个知识共享与能力扩展的统一平台：

```
┌─────────────────────────────────────────────────────────────────┐
│                     Cognitive Mesh Platform                      │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────────────┐│
│  │              Polyglot SDK Layer (UniFFI)                    ││
│  │   Python │ Go │ Kotlin │ Swift │ Rust Native               ││
│  │   PyPI   │ Go Modules │ Maven │ SPM │ crates.io            ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │              Collective Intelligence Core                   ││
│  │  ┌────────────┐ ┌────────────┐ ┌────────────────────────┐  ││
│  │  │  Memory    │ │    RAG     │ │  Embedding Pipeline    │  ││
│  │  │  System    │ │  Engine    │ │  (Multi-Provider)      │  ││
│  │  │ (3-Layer)  │ │ (Hybrid)   │ │                        │  ││
│  │  └────────────┘ └────────────┘ └────────────────────────┘  ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │              Extensibility Layer                            ││
│  │  ┌────────────┐ ┌────────────┐ ┌────────────────────────┐  ││
│  │  │  Plugin    │ │  WASM +    │ │  Plugin Marketplace    │  ││
│  │  │  System    │ │  Rhai      │ │  (Registry + Sandbox)  │  ││
│  │  │ (Dual)     │ │  Runtime   │ │                        │  ││
│  │  └────────────┘ └────────────┘ └────────────────────────┘  ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │              Storage Backends (Pluggable)                   ││
│  │  Qdrant │ pgvector │ Milvus │ Redis │ S3 │ PostgreSQL      ││
│  └─────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────┘
```

**核心模块**：

**1. Multi-Layer Memory System（多层记忆系统）**
- **情景记忆 (Episodic)**：对话历史、交互日志、事件序列
- **语义记忆 (Semantic)**：向量编码的事实、知识、概念
- **程序记忆 (Procedural)**：学到的技能、策略、工作流
- **巩固引擎 (Consolidation)**：LLM 驱动的自动知识提取
- **记忆衰减**：基于重要性和访问频率的自动清理

**2. RAG Infrastructure（RAG 基础设施）**
- **向量存储抽象**：统一的 `VectorStore` trait
- **多后端支持**：Qdrant、pgvector、Milvus、内存 HNSW
- **混合搜索**：稠密向量 + BM25 稀疏检索
- **智能分块**：语义分块、滑动窗口、递归分割
- **重排序**：Cross-encoder 精排

**3. Embedding Pipeline（嵌入流水线）**
- **多提供商**：OpenAI、Cohere、本地模型 (ONNX)
- **批处理**：高效批量嵌入
- **缓存层**：嵌入结果缓存
- **维度归一化**：不同模型的统一接口

**4. Dual-Runtime Plugin System（双运行时插件系统）**
- **编译时层**：Rust 原生插件 + WebAssembly (WASM)
- **运行时层**：Rhai 脚本，支持热重载
- **跨运行时桥接**：WASM ↔ Rhai 互操作
- **安全沙箱**：资源限制、能力授权
- **插件市场**：签名验证、依赖解析、版本管理

**5. Polyglot SDK Suite（多语言 SDK 套件）**
- **Python SDK**：asyncio、类型提示、PyPI、Jupyter 集成
- **Go SDK**：Goroutine 友好、上下文传播、Go modules
- **Kotlin SDK**：协程、DSL 风格构建器、Maven Central
- **Swift SDK**：Swift async/await、SwiftUI 集成、SPM
- **跨语言一致性测试**：确保行为一致

### 预期成果（Deliverables）

**Phase 1: 核心记忆与 RAG（第 1-5 周）**
- `mofa-memory` crate：三层记忆系统
- `MemoryConsolidator`：LLM 驱动的知识提取
- `VectorStore` trait + Qdrant 实现
- `HybridSearcher`：稠密 + 稀疏检索
- 基础嵌入流水线

**Phase 2: 插件系统（第 6-10 周）**
- `mofa-plugins` 增强：WASM + Rhai 双运行时
- `PluginBridge`：跨运行时互操作
- `PluginSandbox`：安全沙箱
- 热重载机制
- 基础插件市场原型

**Phase 3: 多语言 SDK（第 11-16 周）**
- UniFFI 接口定义
- Python SDK（PyPI 发布）
- Go SDK（Go modules）
- Kotlin SDK（Maven Central）
- Swift SDK（SPM）
- 跨语言测试套件

**Phase 4: 存储后端与生态（第 17-22 周）**
- pgvector、Milvus、Redis 后端
- 插件市场完整功能（签名、依赖、版本）
- CLI 工具：`mofa plugin install/publish`
- 文档门户：快速入门、API 参考、示例库
- 性能基准测试

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 三层记忆系统基本实现（Episodic + Semantic）
- 至少 1 个向量存储后端（Qdrant 或 pgvector）
- 基础 RAG 流程：文档 → 分块 → 嵌入 → 检索 → 生成
- 至少 2 种语言 SDK（Python + Go 或 Kotlin）
- 简单的插件加载演示（Rhai 脚本）

### 扩展目标（Stretch Goals）

- **知识图谱**：实体抽取、关系推理、图检索
- **高级巩固**：多轮对话自动总结、关键信息提取
- **插件 IDE 集成**：VS Code 插件、调试工具
- **分布式记忆**：跨节点记忆同步、联邦学习
- **性能优化**：向量索引优化、缓存策略、批处理

### 验收标准（Acceptance Criteria）

- [ ] 三层记忆系统完整实现，支持持久化
- [ ] 至少 3 种向量存储后端可用（Qdrant、pgvector、内存）
- [ ] 混合搜索准确率 ≥ 85%（在标准数据集上）
- [ ] 插件系统支持 WASM 和 Rhai 双运行时
- [ ] 4 种语言 SDK 行为一致性测试通过
- [ ] 插件市场支持签名验证和依赖解析
- [ ] 单元测试覆盖率 ≥ 70%，集成测试覆盖核心场景
- [ ] 提供可复现的部署文档和演示脚本

### 生态价值

| 层级 | 价值 |
|------|------|
| **知识共享** | Agent 智能可积累，避免重复构建 |
| **能力扩展** | 社区可贡献新的记忆后端、嵌入提供商 |
| **生态普及** | 任何语言开发者都能访问 MoFA 能力 |
| **插件生态** | 形成良性循环：用户越多 → 插件越多 → 价值越大 |

### 所需技能

- **必需**：扎实的 Rust 编程（async/await、trait 设计、FFI）
- **必需**：理解向量数据库和嵌入
- **必需**：至少精通 2 种目标语言（Python/Go/Kotlin/Swift）
- **优先**：RAG 系统经验
- **优先**：WebAssembly 运行时经验
- **优先**：包分发和发布经验

### 难度

**高**（350 小时）

### 导师

待定

---

## 项目六：统一推理编排器（本地 + 云端）

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

## 项目七：会话记录器与可视化调试器

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

## 项目八：Makepad AI 应用组件库

### 摘要

MoFA 的桌面应用（Studio、moly-ai）基于 [Makepad](https://makepad.dev/) 构建——一个 Rust 编写的 GPU 加速 UI 框架。虽然组织已构建了基础 Makepad 组件（[makepad-chart](https://github.com/mofa-org/makepad-chart)、[makepad-d3](https://github.com/mofa-org/makepad-d3)、[makepad-element](https://github.com/mofa-org/makepad-element)），但目前缺少**专为 AI 应用设计的可复用组件库**。

本项目构建 `makepad-ai-toolkit`——一套为 AI 聊天界面、模型管理和推理可视化量身定制的精美可复用 Makepad 组件。这些组件可立即用于 MoFA Studio 及任何未来基于 Makepad 的 AI 应用。

__导师__: BH3GEI (Yao Li), yangrudan (CookieYang)

### 目标与想法

* **聊天界面组件**:
  - 支持 user/assistant/system 角色的聊天气泡组件
  - 流式文本渲染器（token 实时出现）
  - 聊天消息内的 Markdown 渲染（代码块、列表、标题）
  - 代码语法高亮

* **音频与语音组件**:
  - 音频波形可视化器（用于 ASR 输入 / TTS 输出）
  - 带实时振幅显示的录音指示器
  - 带进度条的音频播放控件

* **模型管理 UI**:
  - 带模型元数据（大小、类型、量化）的模型选择下拉框
  - 下载进度指示器
  - 模型状态徽章（已加载、卸载中、错误）

* **推理可视化**:
  - Token/秒计数器和延迟显示
  - 内存使用仪表盘（Apple Silicon 统一内存）
  - 推理进度指示器（prefill 与 decode 阶段）

* **集成**:
  - 打包为独立 Makepad crate（`makepad-ai-toolkit`），可发布到 crates.io
  - 提供示例应用展示每个组件
  - 文档与常见 AI 应用布局的使用模式

### 最小验收（MVP）

- 交付可复用组件包，并附文档与示例
- 至少 2 个组件接入 `mofa-studio` 的真实产品流程
- 提供组件级测试与 demo 验证步骤

### Stretch Goals

- 发布 crate 并维护版本化发布说明
- 增强主题与交互模式，提升通用性

### Out of Scope

- 只做组件展示页，不做产品接入
- 只做视觉重绘，不提供可复用 API 契约

### 验收标准（Acceptance Criteria）

- 至少 2 个组件在 `mofa-studio` 中接入并用于已发布工作流
- 组件 API 文档完整，可被外部贡献者复用
- 示例可运行且行为与文档一致

### 落仓计划（Repo Landing Plan）

- **主落仓**：`makepad-ai-toolkit`（新仓）
- **必须联调落地**：`mofa-studio`

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/makepad-element
* https://makepad.dev/

__所需技能__: Rust, UI/UX 设计, Makepad 框架

__时间估计__: 90 小时（8 周）

__难度__: 中
