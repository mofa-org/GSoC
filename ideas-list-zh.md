# MoFA GSoC 2026 项目提案

> 中文版 |  [English Version](./ideas-list.md)

本文档包含 Google Summer of Code 2026 的详细项目提案。整体框架已定，具体细节可在导师指导下根据贡献者建议进行调整。我们鼓励贡献者提出自己的方案——以下想法是起点，而非刚性规范。

## 关于 MoFA

[MoFA](https://mofa.ai/)（**Modular Framework for Agents**）是一个用于构建 AI Agent 的开源框架。我们的近期项目 **MoFA Studio** 是一个桌面应用，用于创建、运行和分享 AI 驱动的应用——基于 Rust 和 Makepad 构建，使用 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 实现 Apple Silicon 上的本地 ML 推理。

我们在系统工程、AI 基础设施和开发者工具方面指导 GSoC 贡献者解决真实世界的问题。

__官网:__ [mofa.ai](https://mofa.ai/)

__GitHub 仓库:__
- 核心运行时: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio 应用: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI 组件: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)
- 节点生态: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

__组织联系邮箱:__ dev@mofa.ai
__GSoC 贡献者指南:__ [README-zh.md](./README-zh.md)

---

## 项目一：AgentForge —— 面向协作式 AI 开发的可组合插件系统

### 摘要

在 vibe coding 时代，单个开发者可以借助 LLM 快速生成 Agent 代码。然而，**将多位 vibe coder 的产出合并为一个连贯系统仍然是最大的未解难题**——人类的 review 带宽才是瓶颈，而非代码生成速度。

**AgentForge** 通过为 mofa-rs 构建可组合插件系统来解决这个问题：每位开发者独立创建具有明确接口的自包含 Agent 插件，框架负责组合、验证和冲突检测——实现团队级 vibe coding 而无合并噩梦。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### 目标与想法

* **插件接口规范**：为 mofa-rs 插件定义清晰契约——输入类型、输出类型、状态模式和生命周期钩子。每个插件是可独立开发、测试和 vibe code 的自包含单元
* **验证工具**：构建在组合前验证插件接口兼容性的工具——类型检查、模式验证和插件间冲突检测
* **组合引擎**：根据接口声明自动将多个插件连接在一起。处理路由、数据转换和跨插件边界的错误传播
* **插件隔离**：确保一个插件的故障不会导致其他插件崩溃。沙箱化运行时状态，使插件可在开发过程中热替换
* **Studio 集成**：生成的插件组合可在 MoFA Studio 中加载和运行

贡献者也可以探索其他或互补的方案，例如：

* **语义节点搜索**：使用向量嵌入索引 [mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)（400+ 节点），辅助插件发现和组合
* **流程合成**：将自然语言描述转换为可执行的插件组合
* **Makepad UI 生成**：为插件配置和输出自动生成界面

#### 示例场景

三位开发者各自 vibe code 一个 Agent 组件：
- 开发者 A：一个网页抓取 Agent 插件
- 开发者 B：一个摘要生成 Agent 插件
- 开发者 C：一个通知推送 Agent 插件

AgentForge 验证它们的接口兼容，将其组合为流水线，并运行整个系统——三位开发者无需阅读彼此的代码。

#### 参考链接

* https://github.com/mofa-org/mofa/tree/main
* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/mofa-node-hub
* https://makepad.dev/

__所需技能__: Rust, 插件架构设计, 类型系统, LLM 集成

__时间估计__: 120 小时（10 周）

__难度__: 高

---

## 项目二：Studio 可观测性面板

### 摘要

MoFA Studio 运行涉及多个模型（ASR、LLM、TTS）和 Agent 交互的复杂 AI 流水线。目前，当出现问题或运行缓慢时，开发者对内部状况的可见性有限。本项目将构建一个**实时可观测面板**，直接嵌入 MoFA Studio，为开发者提供对模型性能、资源使用和 Agent 行为的即时洞察。

该面板将利用 MoFA Studio 现有的 [makepad-chart](https://github.com/mofa-org/makepad-chart) 和 [makepad-d3](https://github.com/mofa-org/makepad-d3) GPU 加速可视化组件。

__导师__: BH3GEI (Yao Li), Bicheng Lou

### 目标与想法

* **Dashboard 服务器开发**:
  - 构建 HTTP 服务器（使用 axum 或类似框架），暴露指标的 REST API
  - 实现 WebSocket 端点用于实时流式更新
  - 设计高效的指标聚合和缓存机制

* **API 设计与实现**:
  - `/api/agents` — 列出所有 Agent 及其状态
  - `/api/agents/{id}` — 详细的 Agent 指标
  - `/api/metrics` — 系统级指标快照（模型状态、内存、延迟）
  - WebSocket `/ws` — 实时事件流

* **模型与推理监控**:
  - 当前加载在内存中的模型及其大小
  - 每模型推理指标：tokens/s、首 token 延迟、批处理利用率
  - Apple Silicon 统一内存使用量和压力
  - 模型加载/卸载事件和耗时

* **流水线监控**:
  - 多模型流水线端到端延迟（如 ASR → LLM → TTS）
  - 分阶段延迟分解和瓶颈识别
  - 请求队列深度和吞吐量

* **Studio 集成**:
  - 使用 [makepad-chart](https://github.com/mofa-org/makepad-chart) 和 [makepad-d3](https://github.com/mofa-org/makepad-d3) 的基于 Makepad 的实时可视化面板
  - Agent 状态显示（运行中、暂停、错误状态）
  - 带时间序列图表的资源使用面板
  - 日志聚合与智能过滤

贡献者也可以探索监控基于 Dora 的数据流运行时，提供跨不同编排后端的统一监控接口。

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

## 项目三：边缘模型编排器

### 摘要

边缘设备上，多个模型（ASR、LLM、TTS、embedding）争夺有限的内存和算力。本项目实现一个内置于 mofa-rs 的智能**模型调度器**，实现 Apple Silicon 设备上的高效多模型编排。

与通过 HTTP 与模型服务器通信的传统方案（如 Ollama）不同，该编排器在 **Rust API 层面直接调用** [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 模型 crate——`load_model()`、`Generate`、`forward()`——编译期绑定，零序列化开销。这充分利用了 Apple Silicon 统一内存的关键优势：**一个模型的输出张量（如 ASR）可以作为零拷贝 MLX Array 直接传递给另一个模型（如 LLM）**，消除了基于 HTTP 或跨进程架构固有的序列化-反序列化开销。

现有原型 [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) 已通过此方案验证了单模型推理。本项目将其扩展为多模型并发调度。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

### 目标与想法

* **架构设计**:
  - 作为 mofa-rs 的核心组件实现（`mofa-foundation` 层）
  - 通过 Rust API 直接调用 OminiX-MLX crate（编译期依赖，无 HTTP 中间层）
  - 设计 `ModelPool` 管理多个并发加载的模型实例

* **生命周期管理**:
  - 按需模型加载，支持异步初始化
  - 基于空闲超时的自动卸载（LRU 淘汰）
  - Apple Silicon 统一内存压力监控
  - 带状态保存的优雅关闭

* **智能调度**:
  - 基于任务类型（ASR/LLM/TTS）和可用性将请求路由到正确的模型
  - 内存感知准入控制：内存受限时拒绝或延迟请求
  - 动态精度降级（如压力下自动从 8-bit 切换到 4-bit 量化）

* **推理流水线**:
  - 通过 MLX Array 零拷贝传递将多个模型串联为流水线（ASR → LLM → TTS）
  - LLM 流式 token 输出直接输入 TTS
  - 分阶段延迟追踪和瓶颈报告

* **降级策略**:
  - 当主模型失败或资源受限时自动回退到更小模型
  - 服务质量级别与相应的模型选择

* **集成**:
  - 向 Studio 可观测性面板暴露调度状态和指标（项目二）
  - 为 Agent 提供清晰 API，请求推理而无需管理模型生命周期

#### 示例场景

一个语音助手流水线包含：
- FunASR（ASR，~2GB）
- Qwen（LLM，~8GB）
- GPT-SoVITS（TTS，~4GB）

在 16GB MacBook 上，三者无法同时驻留。编排器将：
- 保持 LLM 常驻（核心功能）
- 语音输入时加载 ASR，空闲 30 秒后卸载
- 仅在合成期间加载 TTS，LLM 输出 token 作为 MLX Array 直接传递（零拷贝）
- 内存压力下自动将 Qwen 从 8-bit 切换到 4-bit 量化

#### 参考链接

* https://github.com/mofa-org/mofa-local-llm
* https://github.com/OminiX-ai/OminiX-MLX
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-foundation
* https://github.com/mofa-org/mofa/tree/main/crates/mofa-runtime

__所需技能__: Rust, 系统编程, 资源管理, Apple Silicon / GPU 计算

__时间估计__: 140 小时（11 周）

__难度__: 高

---

## 项目四：会话记录器与可视化调试器

### 摘要

多 Agent 系统是出了名的难调试。当 Agent 之间交换数十条消息和状态变更时，传统日志变得难以阅读。在 vibe coding 时代尤其如此——LLM 生成的 Agent 代码往往在演示中正常工作，但在生产环境中莫名失败。

本项目为 MoFA 构建一个**时间旅行调试器**——一个使开发者选择在 mofa-rs 上运行 Agent 的差异化能力。把它想象成"Agent 的 Chrome DevTools"：加载任何 Agent（手写或 vibe code 生成的），记录执行过程，检查消息流，并以修改后的状态重放。

构建此调试器同时也是对 mofa-rs 的一次**架构审计**——添加插桩钩子的过程将迫使框架为事件捕获、状态快照和消息拦截定义清晰的内部 API。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu), Bicheng Lou

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

__时间估计__: 140 小时（11 周）

__难度__: 高

---

## 项目五：MoFA Input —— 推理栈迁移至 OminiX-MLX

### 摘要

[MoFA Input](https://github.com/mofa-org/mofa-input) 是一个完全在本地运行的 macOS 全局语音输入法。目前使用 llama.cpp + GGUF 模型进行 ASR（Whisper）和 LLM（Qwen）推理。本项目将推理栈迁移至 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX)，以针对 Apple Silicon 优化的原生 Rust 推理替代 llama.cpp 后端。

为什么迁移？MLX 的 Metal GPU 加速在 Apple Silicon 上快于 llama.cpp，统一内存减少开销，且 MoFA 生态其余部分（Studio、mofa-local-llm）已使用 OminiX-MLX。

__导师__: BH3GEI (Yao Li), Xiaokuge (Zonghuan Wu)

### 目标与想法

* **ASR 迁移**：将当前基于 llama.cpp 的 Whisper ASR 替换为 OminiX-MLX 的 `funasr-mlx` 或 `funasr-nano-mlx` crate。验证准确率和延迟与当前实现的对比
* **LLM 迁移**：将 Qwen GGUF 推理替换为 OminiX-MLX 的 `qwen3-mlx` crate（safetensors 格式）。确保流式 token 输出与现有 UI 兼容
* **Swift-Rust FFI**：调整现有 Swift ↔ Rust FFI 桥接层，调用 OminiX-MLX API 而非 llama.cpp。保持当前 macOS 输入法架构（Fn 热键、悬浮球、历史窗口）
* **性能基准测试**：在代表性硬件（M1/M2/M3/M4）上对比迁移前后的延迟、内存占用和准确率
* **模型管理**：集成 `~/.mofa/models/` 模型存储，统一使用 OminiX-MLX 的 safetensors 格式

#### 参考链接

* https://github.com/mofa-org/mofa-input
* https://github.com/OminiX-ai/OminiX-MLX

__所需技能__: Rust, Swift, FFI/跨语言互操作, Apple Silicon 开发

__时间估计__: 90 小时（8 周）

__难度__: 简单

---

## 项目六：Makepad AI 应用组件库

### 摘要

MoFA 的桌面应用（Studio、moly-ai）基于 [Makepad](https://makepad.dev/) 构建——一个 Rust 编写的 GPU 加速 UI 框架。虽然组织已构建了基础 Makepad 组件（[makepad-chart](https://github.com/mofa-org/makepad-chart)、[makepad-d3](https://github.com/mofa-org/makepad-d3)、[makepad-element](https://github.com/mofa-org/makepad-element)），但目前缺少**专为 AI 应用设计的可复用组件库**。

本项目构建 `makepad-ai-toolkit`——一套为 AI 聊天界面、模型管理和推理可视化量身定制的精美可复用 Makepad 组件。这些组件可立即用于 MoFA Studio 及任何未来基于 Makepad 的 AI 应用。

__导师__: BH3GEI (Yao Li), Bicheng Lou

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

#### 参考链接

* https://github.com/mofa-org/mofa-studio
* https://github.com/mofa-org/makepad-chart
* https://github.com/mofa-org/makepad-d3
* https://github.com/mofa-org/makepad-element
* https://makepad.dev/

__所需技能__: Rust, UI/UX 设计, Makepad 框架

__时间估计__: 90 小时（8 周）

__难度__: 中
