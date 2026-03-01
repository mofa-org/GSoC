# MoFA GSoC 2026 项目提案

> 中文版 |  [English Version](../ideas-list.md)

本文档包含 Google Summer of Code 2026 的详细项目提案。整体框架已定，具体细节可在导师指导下根据贡献者建议进行调整。我们鼓励贡献者提出自己的方案——以下想法是起点，而非刚性规范。

> **开始之前**：请先在相关 GitHub issue 下留言表达兴趣，并简要描述你的思路。**等待维护者分配后再开始编码。** 这可以避免重复劳动。详见[贡献流程](./README.md#在-gsoc-之前贡献)。
>
> **Proposal 基线要求**：你的 proposal 必须包含架构蓝图（组件边界、接口契约、数据流、故障/恢复策略、测试计划）。评估基于质量与深度，而非数量。

## 速查：Idea 提案与对应仓库

当前 ideas 统一按编号放在一张表里（不再区分主线/社区）。

| Idea | 技能标签 | 主仓库 | 相关仓库 |
|------|---------|--------|---------|
| 1. Cognitive Gateway | `Rust` `网关系统` `系统设计` | [mofa](https://github.com/mofa-org/mofa)（`mofa-kernel`、`mofa-foundation`） | [mofa-studio](https://github.com/mofa-org/mofa-studio) |
| 2. Cognitive Observatory | `Rust` `可观测性` `评估体系` | [mofa-studio](https://github.com/mofa-org/mofa-studio) | [mofa](https://github.com/mofa-org/mofa)（`mofa-monitoring`）、[makepad-chart](https://github.com/mofa-org/makepad-chart)、[makepad-d3](https://github.com/mofa-org/makepad-d3) |
| 3. 认知计算网格（Cognitive Compute Mesh） | `Rust` `系统编程` `本地 + 云端推理` | [mofa](https://github.com/mofa-org/mofa)（`mofa-foundation`、`mofa-runtime`） | [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm)、[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) |
| 4. Cognitive Swarm Orchestrator | `Rust` `多智能体编排` `人机协同治理` | [mofa](https://github.com/mofa-org/mofa)（`mofa-foundation`、`mofa-runtime`） | [mofa-studio](https://github.com/mofa-org/mofa-studio)、[mofa-sdk](https://github.com/mofa-org/mofa/tree/main/crates/mofa-sdk) |
| 5. Cognitive Workflow Engine | `Rust` `工作流编排` `可视化` | [mofa](https://github.com/mofa-org/mofa)（`mofa-kernel`、`mofa-foundation`） | [mofa-studio](https://github.com/mofa-org/mofa-studio) |
| 6. Cognitive Agent Testing & Evaluation Platform | `Rust` `测试框架` `质量评估` | [mofa](https://github.com/mofa-org/mofa) | [mofa-studio](https://github.com/mofa-org/mofa-studio) |

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
## 项目 1: Cognitive Gateway — AI Agent 与物理-数字世界的神经接口 + 缓存与插件注册生态

### 参考平台

**AgentGateway** — Linux 基金会的 AI Agent 网关平台，提供 LLM/MCP/A2A 协议支持、智能路由、安全和可观测性。

**Plano** — AI 原生代理服务器，提供代理编排、模型路由、过滤器链和提示目标管理。

** crates.io** — Rust 官方包注册表，支持版本管理、依赖解析和发布工作流。

本项目综合参考上述平台，并扩展 IoT 能力抽象层、分布式缓存系统和插件注册生态以实现物理世界交互与生态扩展。

### 简要描述

构建一个 Rust 原生的高性能网关，将 AI Agent 连接到数字世界（LLM、MCP 工具、A2A 通信）和物理世界（IoT 设备、传感器、执行器），使 Agent 能够通过语义能力 API 感知和交互现实世界。同时提供**分布式缓存层**减少后端调用，以及**插件注册基础设施**支持能力适配器的发现与安装。

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

**分布式缓存层**（新增）：
- **多级缓存**：L1（内存）→ L2（Redis）→ L3（PostgreSQL）
- **缓存失效**：基于 TTL、事件驱动、手动失效
- **跨节点同步**：分布式节点间的缓存一致性
- **缓存预热**：预加载常用 LLM 响应和 IoT 状态
- **智能缓存键**：基于语义相似度的缓存命中

**插件注册基础设施**（新增）：
- **插件注册 API**：发布、搜索、下载插件的 REST API
- **签名验证**：Ed25519 加密签名验证插件真实性
- **CLI 工具**：`mofa plugin install/publish/search/verify`
- **能力发现**：基于 Schema 的插件能力匹配

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

**Phase 5: 缓存与插件生态（第 21-24 周）**
- L1/L2/L3 多级缓存实现
- 跨节点缓存同步机制
- 插件注册 API 与签名验证
- CLI 工具：`mofa plugin install/publish/search/verify`
- 缓存命中率监控与优化

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的网关服务，支持 HTTP 请求路由
- 至少 1 个 LLM 提供商（OpenAI）的路由支持
- 至少 1 个 IoT 适配器（Home Assistant 或 MQTT）
- 基本的认证（API Key）和限流功能
- L1 内存缓存基础实现
- 简单的插件注册 API（CRUD 操作）
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
- [ ] 缓存层减少后端调用 ≥ 50%（基于基准测试）
- [ ] 插件安装时间 < 10 秒（含签名验证）
- [ ] 跨节点缓存一致性延迟 < 100ms

### 所需技能

- **必需**：扎实的 Rust 编程能力（async/await、trait 设计、错误处理）
- **必需**：理解 API 网关模式和反向代理原理
- **必需**：熟悉 HTTP/WebSocket 协议
- **优先**：IoT 协议经验（MQTT、Home Assistant）
- **优先**：事件驱动架构和消息队列经验
- **优先**：LLM API 集成经验（OpenAI、Anthropic）

### 难度

**高**（350 小时）

### 入门指南

1. **审阅现有代码**：
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel - 微内核核心
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation - 基础层实现

2. **学习参考平台**：
   - https://github.com/agentgateway/agentgateway - AgentGateway（Linux 基金会）
   - https://github.com/plano-ai/plano - Plano AI 原生代理服务器

3. **完成微任务**：
   - 实现一个基础的 HTTP 反向代理（`axum`）
   - 设计 3 种常见 IoT 设备的能力 trait（Speaker、Camera、Sensor）
   - 构建 MQTT 客户端原型：连接 → 订阅 → 接收消息

4. **准备提案**：
   - 描述你对项目架构的理解
   - 提出你计划实现的具体技术方案
   - 估算各阶段时间并制定里程碑

### 导师

待定

---

## 项目 2: Cognitive Observatory — AI Agent 系统的全景监控台 + 记忆与知识图谱生态

### 参考平台

**LangSmith** — LangChain 提供的统一 LLM 应用开发平台，涵盖可观测性、评估、提示工程和部署管理。本项目实现完整的 LangSmith 功能集，包括分布式追踪、实时监控、洞察分析、评估框架、提示版本控制和监控仪表板。

**LangChain** — 全面的 LLM 应用框架。本项目实现 LangChain 的记忆系统。

**LlamaIndex** — LLM 应用的数据框架，支持知识图谱、高级索引和检索策略。

### 简要描述

构建一个 LangSmith 级别的可观测性与评估平台，为 AI Agent 生命周期的各个阶段提供全景式可见性——从开发调试、质量评估到生产监控和持续改进。同时整合**三层记忆系统**支持 Agent 知识积累，以及**知识图谱引擎**支持基于结构化信息的推理与调试。

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

**三层记忆系统**（新增）：
- **情景记忆**：对话历史、交互日志、事件序列，支持时间索引
- **语义记忆**：向量编码的事实、概念、知识，支持实体链接
- **程序记忆**：学到的技能、策略、工作流模板，支持执行指标
- **记忆巩固引擎**：LLM 驱动的自动知识提取
- **记忆衰减**：基于重要性的保留策略
- **跨会话持久化**：长期记忆与高效检索

**知识图谱引擎**（新增）：
- **实体抽取**：NER + LLM 驱动的实体识别（用于追踪数据实体）
- **关系推理**：从非结构化文本提取关系（用于决策链分析）
- **图存储**：Neo4j 或原生图数据库集成
- **图检索**：子图匹配、路径查询、邻居扩展
- **图 + 向量融合**：结合结构化和语义检索
- **Schema 推断**：从数据自动构建本体

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

**Phase 5: 记忆系统与知识图谱（第 21-26 周）**
- 三层记忆系统与独立存储
- 记忆巩固引擎与 LLM 总结
- 记忆衰减与重要性评分
- NER + LLM 实体抽取
- 从非结构化文本推理关系
- 图存储集成（Neo4j 或原生）
- 图检索：子图、路径、邻居查询
- 记忆与追踪数据的整合（时间旅行调试支持）

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的追踪服务，支持 HTTP/gRPC 数据摄入
- 至少 1 种评估器（LLM-as-judge 或代码评估）
- 基础 Web 仪表板，显示追踪列表和详情
- 简单的离线评估流程（数据集 → 评估 → 结果）
- 命令行工具提交追踪数据
- 情景和语义记忆与巩固基础实现
- 基础实体抽取管路

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
- [ ] 三层记忆系统与巩固和衰减完整实现
- [ ] 记忆检索延迟 < 100ms
- [ ] 知识图谱支持实体抽取、关系推理和图检索
- [ ] 图查询延迟 < 200ms

### 所需技能

- **必需**：扎实的 Rust 编程能力（async/await、trait 设计、错误处理）
- **必需**：理解 OpenTelemetry 和分布式追踪原理
- **必需**：熟悉 SQL 数据库（PostgreSQL）和数据建模
- **优先**：可观测性工具经验（Jaeger、Grafana、Prometheus）
- **优先**：前端经验（TypeScript/React）
- **优先**：LLM 评估方法（LLM-as-judge、RAGAS 等）

### 难度

**高**（350 小时）

### 入门指南

1. **审阅现有代码**：
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-monitoring - 监控模块
   - https://github.com/mofa-org/mofa/tree/main/examples/monitoring_dashboard - 监控示例

2. **学习参考平台**：
   - https://github.com/langchain-ai/langsmith-sdk - LangSmith SDK
   - https://github.com/open-telemetry/opentelemetry-rust - OpenTelemetry Rust SDK

3. **完成微任务**：
   - 实现一个基础的 tracing subscriber，记录函数调用
   - 设计评估器 trait，支持自定义评分逻辑
   - 构建简单的追踪可视化原型（命令行或 Web）

4. **准备提案**：
   - 描述你对 LangSmith 各模块功能的理解
   - 提出你计划实现的具体技术方案
   - 估算各阶段时间并制定里程碑

### 导师

待定

---

## 项目 3: 认知计算网格 — 构建AI推理的”HTTP时刻” + RAG 与向量存储生态

### 参考平台

**LiteLLM** — 统一API网关，支持100+ LLM提供商，提供一致接口、自动故障转移和成本追踪。

**vLLM** — 高吞吐推理引擎，PagedAttention、连续批处理、生产级服务。

**Ollama** — 本地LLM运行时，模型管理、GPU加速、REST API兼容。

**Ray Serve** — 通用模型服务框架，自动扩缩、多模型编排、跨集群部署。

**Kubernetes** — 容器编排标准，证明”统一抽象 + 可插拔后端”模式可以统治一个领域。

**LlamaIndex** — LLM 应用的数据框架，支持高级索引和检索策略。

本项目不只是构建一个推理网关——而是建立**AI推理的开放协议标准**，让”推理即服务”像HTTP一样无处不在、即插即用，同时整合**生产级 RAG 管道**和**多后端向量存储**生态。

### 摘要

**愿景**：正如HTTP统一了信息传输、SQL统一了数据查询，认知计算网格将为AI推理建立**开放协议标准**——任何Agent、任何模型、任何硬件、任何位置，一次编写，处处运行。

**核心命题**：今天的AI推理被割裂成孤岛——OpenAI、Anthropic、本地Ollama、云端vLLM、边缘设备——每个都是独立世界。认知计算网格构建**统一推理联邦**，消除供应商锁定，建立开放生态。

**导师**: BH3GEI (Yao Li), lijingrs (AmosLi)

### 问题与机遇

**当前困境**：
- **供应商锁定**：从OpenAI迁移到Anthropic需要重写代码
- **世界割裂**：本地推理（Ollama）与云端推理（OpenAI）是两套体系
- **成本黑箱**：推理成本不可预测、不可优化、不可归属
- **创新壁垒**：新推理服务需要逐个集成，无标准可循
- **资源浪费**：GPU集群、边缘设备、本地算力无法协同

**历史启示**：
- HTTP之前：每种信息传输都需要专用协议
- SQL之前：每种数据库都需要学习新语言
- Kubernetes之前：每种部署都需要定制脚本
- **推理协议之前（现在）**：每种推理服务都需要重新集成

### 解决方案：认知计算网格

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     Cognitive Compute Mesh (认知计算网格)                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    开放协议层 (Open Protocol Layer)                  │   │
│  │  “一次定义，处处兼容” — 推理界的HTTP                                 │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ 推理请求    │ │ 流式响应    │ │ 工具调用/多模态/嵌入        │   │   │
│  │  │ 标准格式    │ │ 标准格式    │ │ 统一抽象                    │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    智能路由层 (Intelligent Routing)                  │   │
│  │  “最优路径，自动选择” — 推理界的BGP                                  │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ 成本优化    │ │ 延迟优化    │ │ 地理路由/合规路由            │   │   │
│  │  │ 路由策略    │ │ 路由策略    │ │ 智能故障转移                │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    联邦计算层 (Federated Compute)                    │   │
│  │  “算力无界，协同无感” — 推理界的Kubernetes                           │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ 本地推理    │ │ 云端推理    │ │ 边缘推理/专用硬件            │   │   │
│  │  │ OminiX-MLX  │ │ OpenAI等    │ │ Groq/Cerebras/自定义        │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                    ↓                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    生态扩展层 (Ecosystem Extension)                  │   │
│  │  “人人可贡献，价值可流转” — 推理界的crates.io                        │   │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────────────────────┐   │   │
│  │  │ 后端SDK     │ │ 模型适配器  │ │ 协议扩展/社区贡献            │   │   │
│  │  │ 开发框架    │ │ 注册中心    │ │ 治理与信任体系               │   │   │
│  │  └─────────────┘ └─────────────┘ └─────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### 核心模块

**1. 开放协议层 (Open Protocol Layer)**

建立推理服务的通用语言：

- **推理请求协议 (IRP)**：标准化的推理请求格式，支持文本、多模态、工具调用
- **流式响应协议 (SRP)**：统一的流式响应格式，支持增量输出、心跳、取消
- **能力发现协议 (CDP)**：自动发现后端支持的能力（模型、模态、工具）
- **健康检查协议 (HCP)**：标准化的健康状态报告和监控
- **协议版本协商**：向后兼容的协议演进机制

**2. 智能路由层 (Intelligent Routing Layer)**

实现推理请求的最优调度：

- **多目标优化**：成本、延迟、质量、合规的多维权衡
- **策略引擎**：可编程的路由策略（DSL或Rhai脚本）
- **负载感知**：基于队列深度、GPU利用率、内存压力的动态调度
- **故障自愈**：自动故障检测、熔断、降级、恢复
- **容量预测**：基于历史数据的负载预测和预热

**3. 联邦计算层 (Federated Compute Layer)**

整合全球推理算力：

- **本地推理后端**：
  - OminiX-MLX（macOS统一内存优化）
  - llama.cpp（跨平台CPU/GPU）
  - vLLM（高性能服务化）
- **云端推理后端**：
  - OpenAI、Anthropic、Google、AWS Bedrock
  - Azure OpenAI、阿里云、百度智能云
- **专用硬件后端**：
  - Groq（LPU推理）
  - Cerebras（晶圆级计算）
  - 边缘TPU/NPU
- **混合流水线**：本地ASR + 云端LLM + 本地TTS的无缝编排

**4. 生态扩展层 (Ecosystem Extension Layer)**

构建开放的贡献机制：

- **后端SDK**：标准化框架，2小时内实现新后端集成
- **模型适配器**：新模型格式的即插即用支持
- **协议扩展**：自定义能力的标准扩展点
- **贡献者激励**：使用统计、质量评分、社区认可
- **信任体系**：代码签名、安全审计、漏洞报告

**5. 生产级 RAG 管道（新增）**

整合推理与检索增强生成：

- **嵌入提供商**：OpenAI、Cohere、Voyage、本地 ONNX/Candle 模型
- **嵌入缓存**：LRU 缓存，可配置 TTL 和批处理
- **混合检索**：稠密向量 + BM25 稀疏 + ColBERT 后期交互
- **倒数排名融合**：组合多个检索信号
- **查询扩展**：LLM 驱动的查询转换和多查询
- **重排序**：Cross-encoder、LLM 驱动、MMR 多样性、新鲜度提升
- **推理上下文组装**：为推理请求自动注入检索到的上下文

**6. 多后端向量存储（新增）**

统一向量存储抽象：

- **统一接口**：`VectorStore` trait 一致 API
- **Qdrant**：生产云部署
- **pgvector**：PostgreSQL 原生向量存储
- **Milvus**：大规模向量数据库
- **内存 HNSW**：开发和测试
- **语义路由**：基于向量相似度的后端选择

### 生态价值主张

| 利益相关者 | 获得价值 |
|-----------|---------|
| **Agent开发者** | 一次编写，处处运行——零供应商锁定 |
| **企业组织** | 成本优化50%+、风险分散、合规可控 |
| **推理提供商** | 一键接入MoFA生态，触达全球开发者 |
| **开源社区** | 开放标准、公平竞争、创新无壁垒 |
| **硬件厂商** | 标准接口，无需逐个适配软件生态 |

### 预期成果

**Phase 1: 协议奠基（第1-5周）**
- 推理请求协议(IRP)设计与实现
- OpenAI兼容协议适配器
- Anthropic兼容协议适配器
- 流式响应协议(SRP)实现
- 协议兼容性测试套件

**Phase 2: 联邦计算（第6-12周）**
- OminiX-MLX本地后端集成（macOS优先）
- OpenAI云端后端集成
- 至少1个额外云提供商（Anthropic/Google）
- 本地/云端混合流水线
- 零拷贝推理链路验证

**Phase 3: 智能路由（第13-18周）**
- 多目标路由策略引擎
- 成本优化路由算法
- 延迟优化路由算法
- 自动故障转移系统
- 容量预测与预热

**Phase 4: 生态开放（第19-22周）**
- 后端SDK框架发布
- 模型适配器接口
- 能力发现协议(CDP)
- 完整文档与迁移指南
- 社区贡献流程

**Phase 5: RAG 管道与向量存储（第23-28周）**
- OpenAI 和 Cohere 嵌入提供商
- 嵌入缓存与 LRU 淘汰
- BM25 稀疏检索实现
- ColBERT 后期交互（token 级匹配）
- 倒数排名融合算法
- Cross-encoder 和 LLM 重排序
- MMR 多样性和新鲜度提升
- Qdrant 和 pgvector 后端集成
- 内存 HNSW 向量存储
- 端到端 RAG 管道集成

### 最小可行产品（MVP）

绑定期结束前需交付：
- 统一推理协议(IRP)的MVP实现
- 至少1个本地后端（OminiX-MLX或llama.cpp）
- 至少1个云端后端（OpenAI）
- 基础路由策略（可用性优先）
- 端到端演示：同一Agent代码在本地和云端运行
- OpenAI 嵌入提供商与缓存
- 基础 BM25 + 稠密混合检索
- 至少1个向量存储后端（Qdrant 或 pgvector）

### 扩展目标（Stretch Goals）

- **多区域部署**：跨地理区域的推理联邦
- **成本归属系统**：精确到Agent、会话、请求的成本追踪
- **推理市场原型**：供需匹配的推理资源交易
- **协议标准化推动**：向行业标准组织提交草案
- **更多后端**：Groq、Cerebras、边缘设备

### 验收标准

- [ ] 统一协议支持OpenAI和Anthropic两种API风格的无缝转换
- [ ] 本地后端实现零拷贝推理流水线（ASR→LLM→TTS）
- [ ] 云端后端支持自动故障转移，恢复时间<1秒
- [ ] 路由策略可配置，支持成本/延迟/质量的权衡
- [ ] 后端SDK允许新后端在<4小时内完成集成
- [ ] 同一Agent代码无需修改即可在本地、云端、混合模式运行
- [ ] 基准测试：延迟、吞吐、成本对比单提供商优化≥30%
- [ ] 单元测试覆盖率≥80%，协议兼容性测试100%通过
- [ ] 文档：协议规范、后端开发指南、迁移教程
- [ ] 至少 3 个嵌入提供商（OpenAI、Cohere、Local）可用
- [ ] 混合检索（Dense + BM25 + Graph）比纯稠密检索准确率提升 ≥20%
- [ ] 重排序提升 precision@10 ≥25%
- [ ] 至少 3 种向量存储后端（Qdrant、pgvector、内存HNSW）可用
- [ ] 100 文本批处理嵌入 < 5s，混合检索 < 200ms

### 技术要求

- **主落仓**：`mofa`主仓库（`mofa-foundation`/`mofa-runtime`）
- **原型验证**：`mofa-local-llm`作为快速迭代实验场
- **跨平台**：必须支持macOS和Linux，Windows为加分项
- **硬件适配**：优先Apple Silicon，同时支持NVIDIA GPU

### 参考资源

* https://github.com/mofa-org/mofa-local-llm - 本地推理原型
* https://github.com/OminiX-ai/OminiX-MLX - macOS推理引擎
* https://github.com/BerriAI/litellm - LiteLLM统一网关
* https://github.com/vllm-project/vllm - vLLM推理引擎
* https://github.com/ray-project/ray - Ray分布式计算

### 所需技能

- **必需**：扎实的Rust编程（async/await、trait设计、系统编程）
- **必需**：理解LLM推理原理和API设计
- **必需**：分布式系统经验（路由、负载均衡、故障恢复）
- **优先**：Apple Silicon或GPU编程经验
- **优先**：协议设计和标准化经验
- **优先**：开源项目贡献经验

### 难度

**高**（350小时）

---

## 项目 4: Cognitive Swarm Orchestrator — 认知集群编排与人机协同治理 + 插件市场与语义发现生态

### 参考平台

**OpenClaw** — 7×24 小时任务自动化平台，强调单 Agent 执行能力。本项目**不复制** OpenClaw 的自动化路线，而是构建 **Swarm 编排层**。

**ZeroClaw** — 轻量级 Rust Agent 运行时，强调性能。本项目**不竞争**运行时，而是构建**协作治理层**。

**crates.io** — Rust 官方包注册表，支持版本管理、依赖解析和发布工作流。

**差异化定位**：2026 是"编排时代"——从单个超级 Agent 到专业化 Agent **Swarm 协作**。本项目构建 MoFA 生态系统的**核心编排与治理引擎**，整合**插件市场核心**（依赖解析、信任评分）和**语义 Agent 发现**能力。

### 简要描述

构建一个 **Swarm 编排引擎**，协调多个专业化 Agent 协作完成复杂任务，结合 MoFA 的 Gateway（能力接入）、Smith（可观测性）、SDK（多语言）形成完整生态闭环，并通过人机协同（HITL）机制确保关键决策受人类监督。同时整合**插件市场核心**（依赖解析、信任评分、签名验证）和**语义 Agent 发现**（基于嵌入的能力匹配）构建开放生态。

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

**6. 插件市场核心**
- **依赖解析**：SemVer 兼容的依赖图求解器，支持冲突检测
- **版本管理**：多版本、弃用、最新版本解析
- **信任评分**：社区评分、下载量、安全审计
- **签名验证**：Ed25519 加密签名验证插件真实性
- **能力组合**：多插件协同能力分析

**7. 语义 Agent 发现**
- **嵌入匹配**：基于嵌入向量的 Agent 能力匹配
- **查询扩展**：LLM 驱动的任务查询转换和多查询
- **混合检索**：稠密向量 + BM25 稀疏检索
- **能力注册 API**：Agent 能力发布、搜索、发现端点

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
- Swarm 状态、审批队列、审计日志的 REST API（与 Observatory 集成实现可视化）
- CLI 工具：`mofa swarm deploy`、`mofa swarm status`
- Docker Compose 部署方案
- 文档：编排指南、最佳实践、集成示例

**Phase 5: 插件市场与语义发现（第 21-26 周）**
- 带冲突检测的 SemVer 依赖解析器
- Ed25519 签名验证系统
- 信任评分和安全审计框架
- Agent 能力注册 API 与语义搜索
- 嵌入匹配与查询扩展
- 混合检索（Dense + BM25）集成

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 可运行的编排服务，支持任务分解和子任务调度
- 至少 2 种协作模式（Sequential + Parallel）的完整实现
- 基础 HITL 流程：人工审批 API（通过 Observatory 集成实现可视化）
- 与 Gateway 的集成演示（通过能力 API 调用设备）
- 简单的命令行演示：`mofa swarm run examples/swarm_demo.yaml`
- 基础依赖解析（SemVer）
- Agent 能力注册与简单搜索

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
- [ ] 依赖解析支持 SemVer，冲突检测准确率 100%
- [ ] 签名验证防止插件篡改
- [ ] 语义搜索精度 ≥ 80%（基于基准测试）
- [ ] 信任评分系统完整实现

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

### 入门指南

1. **审阅现有代码**：
   - https://github.com/mofa-org/mofa/tree/main/examples/secretary_agent - Secretary Agent 实现
   - https://github.com/mofa-org/mofa/tree/main/examples/multi_agent_coordination - 多 Agent 协作示例

2. **学习参考平台**：
   - https://github.com/OpenClaw/OpenClaw - OpenClaw 自动化模式
   - https://github.com/ZeroClaw/zeroclaw - ZeroClaw 轻量运行时

3. **完成微任务**：
   - 实现一个简单的任务分解器（LLM 驱动）
   - 设计 2 种协作模式的调度器（Sequential、Parallel）
   - 构建基础审批工作流原型

4. **准备提案**：
   - 描述你对 Swarm 编排的理解
   - 提出与 Gateway/Smith 集成的技术方案
   - 估算各阶段时间并制定里程碑

### 导师

待定

---

## 项目 5: Cognitive Workflow Engine — 声明式工作流编排与可视化平台

### 参考平台

**Temporal** — 分布式工作流引擎，支持持久执行、重试、补偿事务。

**n8n** — 开源工作流自动化平台，可视化节点编辑器，支持 400+ 集成。

**Airflow** — 数据工程工作流编排，DAG 定义、调度、监控。

本项目构建一个 **AI 原生工作流引擎**，结合声明式 DSL、可视化编辑器和 MoFA 生态系统集成。

### 简要描述

构建一个 **声明式工作流编排引擎**，让用户通过 YAML/JSON DSL 或可视化编辑器定义复杂的 AI Agent 工作流，支持条件分支、循环、错误处理、人工审批、并行执行等高级控制流，并与 MoFA 的 Gateway、Observatory、Orchestrator 深度集成。

### 详细描述

当今 AI 应用的复杂性要求灵活的工作流编排能力——从简单的线性处理到复杂的多 Agent 协作。现有解决方案要么过于通用（Temporal、Airflow），要么缺乏 AI 原生支持（n8n）。本项目构建 **Cognitive Workflow Engine**，一个专为 AI Agent 设计的工作流引擎。

**架构设计**：

```
┌─────────────────────────────────────────────────────────────────┐
│                    Cognitive Workflow Engine                     │
├─────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Visual Workflow Editor                     ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ 拖拽式   │ │ 节点库  │ │ 实时预览 │ │ AI 辅助设计     │   ││
│  │  │ 编辑器   │ │ (Agent) │ │ 与调试   │ │ (推荐节点)     │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   DSL & Schema Layer                         ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ YAML/   │ │ JSON    │ │ Schema  │ │ 版本控制与      │   ││
│  │  │ JSON DSL│ │ Schema  │ │ 验证器  │ │ 迁移工具       │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Execution Engine                           ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ DAG     │ │ 状态    │ │ 错误    │ │ 持久化与       │   ││
│  │  │ 执行器  │ │ 机管理  │ │ 处理器  │ │ 恢复机制       │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
│                              ↓                                   │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                   Node Library                               ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ Agent   │ │ 条件    │ │ 循环    │ │ 人工审批       │   ││
│  │  │ 调用    │ │ 分支    │ │ 迭代    │ │ (HITL)         │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────────────┐   ││
│  │  │ LLM     │ │ 工具    │ │ 数据    │ │ 子工作流       │   ││
│  │  │ 推理    │ │ 调用    │ │ 转换    │ │ 嵌套调用       │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────────────┘   ││
│  └─────────────────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────────┘
```

**核心模块**：

**1. 声明式 DSL**
- **YAML/JSON 工作流定义**：人类可读的工作流描述
- **强类型 Schema**：节点输入/输出的类型安全
- **表达式语言**：JMESPath/CEL 表达式支持动态计算
- **模板系统**：参数化工作流、环境变量替换
- **版本控制友好**：Git diff 友好的 DSL 设计

**2. 可视化编辑器**
- **拖拽式节点编辑**：React Flow 或类似库实现
- **实时预览**：编辑时即时验证和预览
- **AI 辅助设计**：根据自然语言描述推荐工作流
- **调试面板**：断点、变量查看、单步执行
- **导入/导出**：DSL 与可视化双向转换

**3. 执行引擎**
- **DAG 执行器**：拓扑排序、并行调度、依赖解析
- **状态机管理**：运行、暂停、恢复、取消、重试
- **错误处理**：重试策略、补偿事务、死信队列
- **持久化**：PostgreSQL 存储执行状态，支持崩溃恢复
- **超时控制**：节点级和工作流级超时

**4. 节点库**
- **Agent 节点**：调用 MoFA Agent（通过 Orchestrator）
- **LLM 节点**：直接调用 LLM 推理（通过 Compute Mesh）
- **工具节点**：调用 MCP 工具（通过 Gateway）
- **控制流节点**：条件分支、循环、并行、等待
- **数据节点**：转换、过滤、聚合、合并
- **HITL 节点**：人工审批、表单输入、选择

**5. 生态集成**
- **Gateway 集成**：工作流可访问 IoT 设备和外部 API
- **Observatory 集成**：工作流执行追踪、性能分析
- **Orchestrator 集成**：复杂多 Agent 协作作为工作流节点

### 预期成果（Deliverables）

**Phase 1: DSL 与执行引擎（第 1-5 周）**
- `mofa-workflow` crate 基础架构
- YAML/JSON DSL 设计与解析器
- Schema 验证系统
- DAG 执行器：顺序、并行执行
- 基础节点：Agent 调用、LLM 推理、条件分支

**Phase 2: 状态管理与持久化（第 6-10 周）**
- 状态机实现：运行/暂停/恢复/取消
- PostgreSQL 持久化层
- 错误处理：重试策略、补偿事务
- 崩溃恢复机制
- 工作流版本管理

**Phase 3: 可视化编辑器（第 11-16 周）**
- React 前端基础架构
- 拖拽式节点编辑器
- DSL 与可视化双向转换
- 实时验证与错误提示
- 基础调试功能

**Phase 4: 高级节点与集成（第 17-22 周）**
- 循环迭代节点
- 子工作流嵌套
- HITL 审批节点
- Gateway/Orchestrator 集成
- AI 辅助工作流设计
- 完整文档与示例

**Phase 5: 生产就绪（第 23-26 周）**
- 表达式语言（JMESPath/CEL）
- 工作流模板库
- 性能优化与基准测试
- CLI 工具：`mofa workflow run/validate/export`
- Docker Compose 部署

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- YAML DSL 解析器与验证器
- 基础 DAG 执行器（顺序 + 并行）
- 至少 3 种节点类型（Agent 调用、条件分支、LLM 推理）
- PostgreSQL 持久化
- 简单的命令行运行器：`mofa workflow run example.yaml`

### 扩展目标（Stretch Goals）

- **分布式执行**：跨节点工作流调度
- **工作流市场**：共享和发现工作流模板
- **实时协作**：多人同时编辑工作流
- **性能分析**：工作流瓶颈识别与优化建议
- **自然语言转工作流**：LLM 驱动的工作流生成

### 验收标准（Acceptance Criteria）

- [ ] DSL 支持 YAML 和 JSON 两种格式，Schema 验证 100% 覆盖
- [ ] 执行器支持至少 8 种节点类型
- [ ] 状态机支持运行/暂停/恢复/取消/重试
- [ ] 崩溃后可从持久化状态恢复执行
- [ ] 可视化编辑器支持拖拽、连接、删除节点
- [ ] DSL 与可视化双向转换无信息丢失
- [ ] 与 Orchestrator 集成：工作流可调用 Swarm 编排
- [ ] 与 Gateway 集成：工作流可访问 IoT 设备
- [ ] 单元测试覆盖率 ≥ 80%，集成测试覆盖核心场景
- [ ] 文档：DSL 参考、节点库、API 文档

### 所需技能

- **必需**：扎实的 Rust 编程（async/await、serde、sqlx）
- **必需**：理解 DAG 和工作流引擎原理
- **必需**：前端开发经验（React、TypeScript）
- **优先**：工作流引擎开发经验（Temporal、Airflow、n8n）
- **优先**：DSL/解析器设计经验
- **优先**：可视化图形编辑器经验（React Flow、X6）

### 难度

**高**（350 小时）

### 入门指南

1. **审阅现有代码**：
   - https://github.com/mofa-org/mofa/tree/main/examples/workflow_dsl - 工作流 DSL 示例
   - https://github.com/mofa-org/mofa/tree/main/examples/workflow_orchestration - 工作流编排

2. **学习参考平台**：
   - https://github.com/temporalio/temporal - Temporal 工作流引擎
   - https://github.com/n8n-io/n8n - n8n 自动化平台
   - https://github.com/apache/airflow - Airflow 工作流编排

3. **完成微任务**：
   - 设计一个简单的 YAML 工作流 DSL
   - 实现 DAG 拓扑排序和并行执行
   - 构建基础的工作流状态机

4. **准备提案**：
   - 描述你对工作流 DSL 的设计思路
   - 提出可视化编辑器的技术方案
   - 估算各阶段时间并制定里程碑

### 导师

待定

---

## 项目 6: Cognitive Agent Testing & Evaluation Platform — AI Agent 的测试、评估与质量保障平台

### 参考平台

**LangSmith** — LangChain 的可观测性与评估平台，但缺乏系统化的 Agent 测试框架。

**TruLens** — LLM 应用的评估工具，专注于 RAG 评估，Agent 能力有限。

**Promptfoo** — 提示词测试工具，但不支持 Agent 行为测试。

**AgentBench** — Agent 基准测试框架，但只提供评测数据集，不是测试框架。

**DeepEval** — LLM 评估框架，缺乏 Agent 特有的测试能力。

本项目构建一个 **Rust 原生 Agent 测试与评估平台**，填补所有 Agent 框架在质量保障方面的空白——就像软件测试（JUnit/pytest）之于软件工程，Agent 测试框架之于 Agent 开发同样重要。

### 简要描述

构建一个 **Agent 测试与评估平台**，实现：Agent 行为单元测试框架、回归测试系统、性能基准测试、安全与对抗测试、对齐评估、A/B 测试框架、金丝雀部署、评估指标库，并与 MoFA 的 Memory System、Orchestrator、Observatory 深度集成，让 Agent 开发像软件工程一样可测试、可验证、可信赖。

### 详细描述

**Agent 开发正面临软件工程 50 年前同样的困境**——没有测试框架，只能"跑一下看看"。LangChain 有 LangSmith，但它主要是可观测性工具而非测试框架；其他框架更是缺乏系统化的测试能力。本项目构建 **Cognitive Agent Testing & Evaluation Platform**，让 MoFA 成为第一个拥有完整质量保障体系的 Agent 框架。

**架构设计**：

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

**核心模块**：

**1. 测试定义层（Test Definition Layer）**
- **Agent Test DSL**：声明式测试用例定义，类似 Jest/pytest 风格
- **场景构建器**：构建复杂多轮对话场景、工具调用场景、多 Agent 协作场景
- **Mock 框架**：Mock LLM 响应、Mock 工具执行、Mock 外部 API
- **测试数据生成器**：自动生成变体测试用例、边界条件、对抗样本
- **断言库**：Agent 行为断言（响应包含、工具调用正确、状态变更符合预期）
- **期望匹配器**：语义匹配、模糊匹配、结构化匹配
- **Golden Responses**：录制和回放期望响应
- **参数化测试**：同一测试用例支持多组输入参数

**2. 测试执行引擎（Test Execution Engine）**
- **异步测试运行器**：支持并发执行大量测试
- **并行执行**：多线程/多进程测试执行
- **确定性控制**：固定随机种子、Mock 时间、Mock LLM 输出
- **状态隔离**：每个测试用例独立环境
- **LLM Mock Server**：模拟 LLM API，支持预设响应和规则响应
- **Tool Mock Server**：模拟工具执行，支持预设结果
- **时间旅行**：回放 Memory System 的历史状态
- **录制/回放系统**：录制真实交互，回放用于测试

**3. 评估与指标层（Evaluation & Metrics Layer）**
- **准确性指标**：任务完成率、工具调用准确率、信息提取准确率
- **一致性指标**：相同输入的响应一致性、行为稳定性
- **安全性指标**：拒绝有害请求率、不泄露敏感信息率
- **对齐指标**：遵循指令程度、价值观一致性
- **性能基准**：吞吐量、延迟分布、资源消耗
- **成本分析**：Token 消耗、API 调用次数、成本估算
- **延迟百分位**：P50/P90/P99 延迟统计
- **质量评分**：LLM-as-Judge、人工评估接口

**4. 部署与 CI/CD 集成（Deployment & CI/CD）**
- **A/B 测试框架**：流量分割、指标对比、统计显著性检验
- **金丝雀部署**：小流量验证、自动回滚机制
- **回滚机制**：基于指标自动回滚到稳定版本
- **门禁执行**：测试不通过禁止部署
- **报告生成器**：HTML/JSON/JUnit 格式报告
- **告警系统**：指标异常告警、回归告警
- **趋势分析**：历史指标趋势、性能退化检测
- **GitHub/GitLab 集成**：PR 检查、CI 流水线集成

**5. 高级测试能力**
- **对抗测试**：自动生成对抗样本、越狱攻击测试、提示注入测试
- **边界测试**：极端输入、超长上下文、并发压力
- **回归测试**：自动检测行为回归、Golden Response 对比
- **探索性测试**：随机探索 Agent 行为空间
- **故障注入**：模拟 LLM 失败、网络故障、工具失败

**6. MoFA 生态集成**
- **Memory System 集成**：测试记忆持久化、记忆检索准确性
- **Orchestrator 集成**：测试多 Agent 协作、任务分解
- **Observatory 集成**：测试结果与可观测性关联
- **Gateway 集成**：测试 IoT 场景、物理世界交互

### 预期成果（Deliverables）

**Phase 1: 测试框架基础（第 1-5 周）**
- `mofa-testing` crate 基础架构
- 测试用例定义 DSL
- 基础断言库
- 测试运行器（同步）
- 简单的报告生成

**Phase 2: Mock 系统（第 6-10 周）**
- LLM Mock Server 实现
- Tool Mock 框架
- 确定性控制（种子、时间 Mock）
- 测试隔离机制
- 录制/回放系统基础

**Phase 3: 评估指标库（第 11-16 周）**
- 准确性、一致性、安全性指标
- 性能基准测试框架
- LLM-as-Judge 集成
- 指标聚合与统计
- 与 Observatory 集成

**Phase 4: 高级测试能力（第 17-22 周）**
- 对抗测试生成器
- 边界条件测试
- 回归测试系统
- 故障注入框架
- 参数化测试支持

**Phase 5: CI/CD 集成（第 23-28 周）**
- A/B 测试框架
- 金丝雀部署支持
- GitHub/GitLab CI 集成
- 门禁系统
- 告警与通知

**Phase 6: 生态集成与优化（第 29-35 周）**
- Memory System 测试支持
- Orchestrator 测试支持
- Gateway 测试支持（IoT Mock）
- 性能优化（大规模测试）
- 完整文档与示例

### 最小可行产品（MVP）

参与者需在绑定期结束前交付以下 MVP 以证明能力：
- 基础的测试用例定义 DSL
- 至少 10 个常用断言
- 简单的 LLM Mock（预设响应）
- 测试运行器 + 基础报告
- 演示：为一个简单 Agent 编写 5+ 测试用例

### 扩展目标（Stretch Goals）

- **可视化测试编辑器**：Web UI 编辑和运行测试
- **测试用例推荐**：基于 Agent 行为自动推荐测试用例
- **跨框架兼容**：支持测试 LangChain/CrewAI Agent
- **Fuzzing 测试**：自动发现 Agent 边界条件
- **评估数据集**：构建开源 Agent 评估数据集

### 验收标准（Acceptance Criteria）

- [ ] 支持至少 50 种断言类型
- [ ] LLM Mock 支持 OpenAI/Anthropic/Gemini 协议
- [ ] 测试执行支持 1000+ 并发测试
- [ ] 单次测试执行延迟 < 100ms（不含 LLM 调用）
- [ ] 确定性测试：相同输入 100% 相同输出
- [ ] 评估指标库包含至少 30 种指标
- [ ] 支持至少 5 种报告格式（HTML/JSON/JUnit/Allure/Markdown）
- [ ] GitHub Actions 集成可用
- [ ] 对抗测试覆盖 OWASP LLM Top 10
- [ ] A/B 测试支持统计显著性检验
- [ ] 与 Memory System 集成测试可用
- [ ] 与 Orchestrator 集成测试可用
- [ ] 单元测试覆盖率 ≥ 90%
- [ ] 文档：测试指南、断言参考、CI/CD 集成指南

### 所需技能

- **必需**：扎实的 Rust 编程（trait、宏、async/await）
- **必需**：理解软件测试原则（单元测试、集成测试、Mock）
- **必需**：熟悉 CI/CD 流程（GitHub Actions、GitLab CI）
- **优先**：LLM 评估经验（LLM-as-Judge、基准测试）
- **优先**：安全测试经验（对抗攻击、越狱测试）
- **优先**：A/B 测试和统计分析经验

### 难度

**高**（350 小时）

### 入门指南

1. **审阅现有代码**：
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-kernel/src/agent - Agent 核心
   - https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation - 基础实现

2. **学习参考平台**：
   - https://github.com/traceloop/openllmetry - OpenTelemetry for LLM
   - https://github.com/promptfoo/promptfoo - Prompt 测试工具
   - https://github.com/confident-ai/deepeval - LLM 评估框架
   - https://github.com/EvalStore/EvalStore - 评估存储

3. **完成微任务**：
   - 实现一个简单的 Agent 测试断言库（至少 5 种断言）
   - 实现基础的 LLM Mock Server（预设响应）
   - 编写一个简单 Agent 的测试用例
   - 实现测试报告生成（JSON 格式）

4. **准备提案**：
   - 描述你对 Agent 测试挑战的理解
   - 分析现有工具的不足
   - 提出你认为可行的架构设计
   - 估算各阶段时间并制定里程碑

### 导师

待定

---
