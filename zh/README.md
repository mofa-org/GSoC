<p align="center">
  <img src="../gsoc_mofa_banner.png" alt="Google Summer of Code 2026 — MoFA" width="100%">
</p>

# Google Summer of Code 2026 — MoFA

> 中文版 |  [English Version](../README.md)

欢迎访问 MoFA 的 GSoC 2026 页面。

- **GSoC 2026 组织页面**: https://summerofcode.withgoogle.com/programs/2026/organizations/mofa-org
- **项目提案**: [ideas-list.md](./ideas-list.md) ([English](../ideas-list.md))
- **Discord**: https://discord.gg/hKJZzDMMm9
- **组织联系邮箱**: dev@mofa.ai

**所有贡献者将被展示在 mofa.ai 开发者名人堂**

> **现在可以开始做 ideas 吗？** 可以。不需要等 GSoC 正式申请期。现在就可以探索代码库、认领[开放任务](./ideas-list.md#开放任务--从这里开始贡献)、与导师讨论你的思路。尽早贡献对你和我们都有帮助。

## GSoC 2026 关键时间（官方）

以下时间均为 UTC：

- **2026-03-16 18:00 UTC**：贡献者申请开启
- **2026-03-31 18:00 UTC**：贡献者申请截止
- **2026-04-30 18:00 UTC**：录取结果公布
- **2026-05-25**：正式编码开始

完整时间线：https://developers.google.com/open-source/gsoc/timeline

## 选拔机制（简版）

简要流程：

1. 导师和组织管理员先在组织内部评审并排序 proposal。
2. 组织管理员向 Google 提交名额申请与排序结果。
3. Google 给每个组织分配 slots（名额）。
4. 如果 MoFA 拿到 `N` 个名额，组织内排名 `#1` 到 `#N` 的 proposal 会被录取。
5. 若同一位申请者被多个组织同时选中，Google 管理员会做最终匹配协调。

---

## 入门指南

### 1. 克隆并构建

**核心框架** (Rust):
```bash
git clone https://github.com/mofa-org/mofa
cd mofa
cargo build
```

**Studio 应用** (Rust + Makepad):
```bash
git clone https://github.com/mofa-org/mofa-studio
cd mofa-studio
./run.sh
```

> 旧版 Python/Dora 核心（`pip install mofa-core`）仍可使用，但已不再是开发重点。GSoC 项目均基于 Rust 代码库。

### 2. 探索

- 阅读 mofa 仓库中的 `docs/architecture.md`
- 学习 mofa-rs 中的 `examples/`: `monitoring_dashboard`, `multi_agent_coordination`, `react_agent`
- 本地构建并运行 Studio

### 3. 联系

申请前：
- 在相关仓库中开启 issue 讨论你的思路
- 直接邮件联系导师（见项目列表）
- 组织联系邮箱: dev@mofa.ai

---

## 我们寻找什么样的朋友

**你不需要：**
- 是 Rust 专家（我们自己也在学习）
- 有 Makepad 或 Dora 经验
- 精通 AI/LLM 内部原理

**你需要：**
- 愿意学习 Rust 和系统编程
- GSoC 期间能稳定投入时间
- 能适应不确定性（我们在与你一起探索）
- 能够沟通进展和遇到的阻碍

**加分项：**
- 系统编程经验（任何语言）
- UI/UX 开发背景
- AI/ML 项目经验
- 开源贡献经历

---

## 如何撰写提案

### 技术方案

不必追求完美。向我们展示你：
- 理解问题领域
- 有可行的前进路径
- 能将工作分解为里程碑
- 准备好随着需求演进进行调整

### 时间规划

预留时间给：
- 学习 Rust/Makepad（第 1-2 周）
- 理解代码库（第 3 周）
- 核心实现（第 4-9 周）
- 测试、文档、演示（第 10-12 周）

### 为什么选择这个项目？

告诉我们：
- MoFA 为什么吸引你
- 你希望学到什么

---

## 我们如何选人

MoFA 是一个转型中的项目。我们正在用 Rust 重写核心、探索新的 UI 框架，架构也在不断演进。我们找的是愿意**一起学习、一起构建**的人，而非什么都已经会了的人。

**我们真正在意的：**
- **能不能沟通？** 卡住了会不会说？我们解释不清楚你会不会问？这比简历重要。
- **能不能坚持？** 暑假期间稳定投入，比一开始惊艳然后消失强得多。
- **能不能边学边干？** 我们团队自己开始的时候也不是 Rust 专家。愿意搞明白的态度，比已经知道什么更重要。

**Issue 认领规则：**
- 默认分配给**第一个留言**表达兴趣的人。
- 若你想认领他人发布或已被分配的 issue，请留言说明理由——维护者会酌情重新分配。
- 若被分配者 7 天内无可见进展且无沟通，维护者可收回重新分配。

**多人想做同一个 GSoC 项目怎么办？**

同一个项目允许多人提交 proposal。我们会跟你们分别沟通，尽量想办法——也许重新划分项目范围，也许建议替代方案。比起拒绝人，我们更愿意一起想办法。

**申请前必须有贡献吗？**

有帮助，但不是硬性要求。一个小 PR 或一条有深度的 issue 评论，能让我们看到你能跑通代码库、能沟通——这才是重点，不是为了设门槛。

---

## 在 GSoC 之前贡献

我们强烈建议你在提交提案前至少做一次贡献。这有助于我们评估你的能力，也有助于你理解代码库。

### 贡献流程

1. **在 issue 下评论** 表达你的兴趣。简要描述你的思路。

2. **等待分配**。默认分配给第一个留言的人。在分配前不要开始编码。若 issue 已被分配，你认为有充分理由，可留言说明——维护者会酌情重新分配。

3. **Fork 并创建分支**：
   ```bash
   git checkout -b your-branch-name
   ```

4. **尽早开启 Draft PR**。这能展示你的进展，让导师提供反馈。

5. **在标记为"Ready for Review"前** 在本地测试你的更改。

6. **回应反馈**。代码审查是对话，而非判决。

### PR 质量要求

- **尽量避免纯骨架 PR。** 必须附带可运行的 example 和测试，证明功能可用。如果改动较大，请确保你清楚代码细节以便后续维护。
- **持续迭代，非一次性提交。** 你需要能够持续维护此 PR 相关功能直至其相对完善。
- **鼓励使用 AI 工具**，但须理解所提交之代码，避免不可维护代码的提交。

### 沟通渠道

- **Discord**: https://discord.gg/hKJZzDMMm9 — 在 #general 自我介绍，在 #gsoc 讨论 GSoC
- **邮件**: dev@mofa.ai — 用于较长讨论或私人事务
- **GitHub Issues** — 技术问题、bug 报告、功能请求

---

## 提案模板

参见 [proposal-template.md](./proposal-template.md) 获取结构化的申请模板。

---

## GSoC 贡献者使用 AI 工具的指引

MoFA 拥抱 AI 工具，并鼓励贡献者使用 AI 工具来提升生产力和代码质量。但贡献者必须避免不负责任和不道德的做法。你需要对 AI 生成的所有输出负最终责任——请审查、理解并确保其符合项目标准。

详细指引请参阅 Google 官方文档：[Guidance for GSoC Contributors using AI tooling in GSoC 2026](https://developers.google.com/open-source/gsoc/resources/ai_guidance)。

---

## 关于 MoFA

**MoFA（Modular Framework for Agents）** 是一个用于构建 AI Agent 的开源框架。

我们的旅程始于一个基于 Python/Dora 的原型，它让我们明白了什么有效（组合、代码可控性）和什么需要改进（比如未针对优化过的基底框架调度和调试的不便）。我们现在正在构建 **MoFA Studio** —— 一个基于 Rust 和 Makepad 的桌面应用，用于创建和运行 AI 应用，使用 [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 实现 Apple Silicon 上的本地推理——同时也在探索 **mofa-rs**，一个下一代核心，未来可能成为替代基础。

**官网**: [mofa.ai](https://mofa.ai/)

**关键仓库：**
- 核心运行时: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio 应用: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI 组件: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)

---

*MoFA 是一个在 MIT/Apache-2.0 许可证下的开源项目。*
