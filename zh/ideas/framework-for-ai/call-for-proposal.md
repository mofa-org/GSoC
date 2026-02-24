# MoFA：面向 Agent 的 AI 原生框架

> GSoC 2026 提案征集 — 框架与基础设施方向

---

## 1. 引言与挑战：AI 时代的软件框架

在深入了解 MoFA 之前，我们建议你先阅读本文件夹中的演示文稿：**"Software Frameworks in the AI Era: Foundations, Transformations, and Future Opportunities"**（`Software Frameworks in the AI Era.pptx`）。

### 什么是软件框架？

<p align="center">
  <img src="../../../ideas/framework-for-ai/images/what-is-a-framework.png" alt="什么是软件框架？" width="80%">
</p>

软件框架不仅仅是一个库——它控制着程序的执行流程。通过控制反转（IoC），框架提供了一个由预构建组件和规则组成的结构化平台，减少样板代码，让开发者专注于业务逻辑。框架历来都是软件工程的基石：标准化、加速开发、内置安全性、可扩展性和跨平台兼容性。

### AI 带来的变革

<p align="center">
  <img src="../../../ideas/framework-for-ai/images/ai-transforming-frameworks.jpeg" alt="AI 编码如何改变框架" width="80%">
</p>

我们正在见证一场根本性的变革。AI 编码助手（GitHub Copilot、Cursor、Claude Code）已被 76% 的开发者使用，带来 3-4 倍的初始开发加速和 75% 的代码产出提升。这引出了一个关键问题：

**AI 会取代框架，还是与框架互补？**

新兴的共识是**混合模式**——AI 生成符合框架规范的代码，而框架提供 AI 生成代码本身无法保证的防护栏、架构纪律和生产级可靠性。这一转变是从*依赖框架的开发*走向*在框架边界内使用 AI 辅助生成自定义代码*。

### 关键挑战

<p align="center">
  <img src="../../../ideas/framework-for-ai/images/critical-challenges.png" alt="AI 框架领域的关键挑战" width="80%">
</p>

演示文稿强调了 AI-框架领域中几个紧迫的挑战：

- **安全与质量**：AI 生成的代码包含的漏洞是人工编写代码的 2.74 倍。62% 的设计缺陷是已知的漏洞模式。45% 的关键安全问题来自 AI 辅助工具。
- **架构债务**：在成熟框架中，86% 的主要跨站脚本攻击模式源于 AI 生成的代码。设计缺陷的修复成本是实现 bug 的 3-100 倍。
- **监管缺口**：随着 AI 能力的增强，人类监管变得更加紧迫，而不是更不重要。

### AI 原生框架的崛起

<p align="center">
  <img src="../../../ideas/framework-for-ai/images/rise-of-ai-native-frameworks.png" alt="新机遇：AI 原生框架的崛起" width="80%">
</p>

一个新的类别正在形成：**AI 原生框架**——从头开始为 AI Agent 时代设计的框架，而不是从前 AI 时代改造而来。演示文稿指出了几个关键构建模块：

- **AI Agent 框架**（LangChain、CrewAI、AutoGPT）用于自治系统
- **Agent 编排**用于 AI 增强的集成
- **人在回路（Human-in-the-Loop）**设计用于关键监管
- **可视化构建器**（如 Flowise、LangFlow）用于快速原型开发
- **记忆与规划**作为框架的一等公民概念
- **工具使用**作为原生能力

未来属于**混合开发模式**——将传统框架基础与 AI 辅助相结合以获得最优结果。正如演示文稿的结论：**"利用 AI，保持纪律。"**

<p align="center">
  <img src="../../../ideas/framework-for-ai/images/future-frameworks-ai-partnership.png" alt="未来：框架与 AI 的伙伴关系" width="80%">
</p>

---

## 2. MoFA 应该做什么？几个探索方向

MoFA（Modular Framework for Agents，模块化 Agent 框架）正处于这些挑战的交汇点。我们正在用 Rust 构建一个 AI 原生框架——不是又一个 LLM API 封装器，而是一个面向可组合、可调试、生产级 AI Agent 的系统级基础。

以下是几个值得探索的方向。这些是**引导方向，不是任务指派**——我们期望你对其进行批判性思考，并提出自己的方案。

### 方向 A：为 Agent 重新定义"框架"

传统框架假设代码是确定性的。Agent 框架必须处理**非确定性的、对话式的、多步推理**。当"用户代码"是一个 LLM 在决定下一步动作时，控制反转意味着什么？当 Agent 的记忆是向量数据库加对话历史时，框架应该如何管理状态？MoFA 需要对这些问题给出一个连贯的答案——不仅仅是一个 API，而是一套关于 Agent 组合的*哲学*。

### 方向 B：Vibe Coding 时代的组合问题

当三个开发者各自用 vibe coding 方式编写一个 Agent 组件时，谁来确保它们能协同工作？这是 [Idea 1: AgentForge](../../ideas-list.md) 背后的核心问题。但问题更深层次：AI Agent 的*插件接口*应该是什么样的？是类型化的消息模式？能力声明？还是完全不同的东西？我们还没有答案。

### 方向 C：AI 生成 Agent 的安全与质量门禁

演示文稿中的数据令人警醒——AI 生成的代码漏洞显著更多。对于 Agent 框架而言，风险更高：Agent 在现实世界中执行操作（API 调用、代码执行、数据访问）。MoFA 需要框架级别的安全保障，超越任何单个开发者（无论是人类还是 AI）所能提供的。面向 Agent 组合的安全模型应该是什么样的？

### 方向 D：从框架到运行时

大多数 Agent 框架本质上是库——它们提供构建模块，但将执行交给开发者。MoFA 正在探索一条不同的路径：一个管理 Agent 生命周期、资源分配、调度和监控的**运行时**。[边缘模型调度器（Idea 3）](../../ideas-list.md)和[会话记录器（Idea 4）](../../ideas-list.md)是这一愿景的具体实例。但更广泛的问题依然存在：一个 Agent 运行时应该提供什么？

### 方向 E：开发者体验的鸿沟

当前构建 Agent 的体验很痛苦。用 printf 调试多 Agent 交互几乎不可能。理解一个 Agent 为什么做出特定决策，需要追踪不透明的 LLM 调用。MoFA 应该让 Agent 开发像使用 React DevTools 进行 Web 开发一样高效。具体来说，那会是什么样子？

---

## 3. 提案征集

我们寻找的是愿意深入思考这些问题的 GSoC 贡献者——而不仅仅是编写代码。

### 我们看重什么

- **研究与批判性思维。** 阅读论文。研究其他框架（LangGraph、CrewAI、AutoGen）如何解决这些问题。找出什么有效、什么无效。形成自己的观点。
- **实验精神。** 构建原型。尝试可能失败的方案。一个记录详实的失败实验比一个浮于表面的成功更有价值。
- **诚实评估。** 如果你认为 MoFA 目前的方向是错误的，请直说。我们更愿意听到有理有据的批评，而不是礼貌性的赞同。
- **第一性原理思维。** 不要假设当前架构是正确的。在问"怎么做"之前先问"为什么"。

### 我们不想看到的

- 仅仅是一份 PR 提交清单的提案。代码很重要，但它应该源于理解，而不是先于理解。
- 浮于表面的对比（"MoFA 比 X 好是因为……"）。我们要的是深度。
- 回避表态的提案。我们想看到你的思考，即使它还不完整。

### 如何开始

1. **阅读演示文稿**——本文件夹和 `why-mofa/` 文件夹中的。理解行业全貌。
2. **克隆并构建 MoFA**（[mofa](https://github.com/mofa-org/mofa) 和 [mofa-studio](https://github.com/mofa-org/mofa-studio)）。运行示例。形成初步印象。
3. **选择一个方向**（第 2 节中的，或自定义）。做深入研究——阅读相关工作、构建原型、撰写发现。
4. **参与社区。** 加入 [Discord](https://discord.gg/hKJZzDMMm9)，提出 issue，问尖锐的问题。
5. **撰写一份体现你思考的提案。** 参见[提案模板](../../proposal-template.md)了解结构要求。

### 请记住

GSoC 是一次学习经历。我们是一个正在转型中的项目——正在用 Rust 重写核心、探索新架构，并与贡献者一起摸索。最好的提案将来自那些对 AI Agent 框架中的难题真正感到好奇的人，而不是那些只想在简历上添一行的人。

我们期待阅读你的想法。

---

*MoFA 是 MIT/Apache-2.0 许可证下的开源项目。*
*组织联系方式：dev@mofa.ai | Discord：https://discord.gg/hKJZzDMMm9*
