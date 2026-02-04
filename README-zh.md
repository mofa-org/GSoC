# Google Summer of Code 2025 — MoFA

> 中文版 | [English Version](./README.md)

欢迎访问 MoFA 的 GSoC 2025 页面。

- **项目提案**: [ideas-list-zh.md](./ideas-list-zh.md) ([English](./ideas-list.md))
- **Discord**: https://discord.gg/hKJZzDMMm9
- **组织联系邮箱**: dev@mofa.ai

**All contributors will be featured on mofa.ai Developer Hall of Fame**

---

## 入门指南

### 1. 克隆并构建

**当前核心** (Python/Dora):
```bash
pip install mofa-core
mofa --help
```

**下一代核心** (Rust):
```bash
git clone https://github.com/mofa-org/mofa
cd mofa
git checkout feature/mofa-rs
cargo build
```

**Studio 应用** (Rust + Makepad + Dora):
```bash
git clone https://github.com/mofa-org/mofa-studio
cd mofa-studio
./run.sh
```

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

## 评审标准

1. **沟通能力** > 已有知识
2. **思考深度** > 代码量
3. **独立能力** > 完美执行
4. **社区契合度** > 简历资历

---

## 在 GSoC 之前贡献

我们强烈建议你在提交提案前至少做一次贡献。这有助于我们评估你的能力，也有助于你理解代码库。

### 贡献流程

1. **在 issue 下评论** 表达你的兴趣。简要描述你的思路。

2. **等待分配**。为避免重复劳动，维护者会进行分配。在分配前不要开始编码。

3. **Fork 并创建分支**：
   ```bash
   git checkout -b your-branch-name
   ```

4. **尽早开启 Draft PR**。这能展示你的进展，让导师提供反馈。

5. **在标记为"Ready for Review"前** 在本地测试你的更改。

6. **回应反馈**。代码审查是对话，而非判决。

### 沟通渠道

- **Discord**: https://discord.gg/hKJZzDMMg9 — 在 #general 自我介绍，在 #gsoc 讨论 GSoC
- **邮件**: dev@mofa.ai — 用于较长讨论或私人事务
- **GitHub Issues** — 技术问题、bug 报告、功能请求

---

## 提案模板

参见 [proposal-template-zh.md](./proposal-template-zh.md) 获取结构化的申请模板。

---

## 关于 MoFA

**MoFA（Modular Framework for Agents）** 是一个用于构建 AI Agent 的开源框架。

我们的旅程始于一个基于 Python/Dora 的原型，它让我们明白了什么有效（组合、代码可控性）和什么需要改进（比如未针对优化过的基底框架调度和调试的不便）。我们现在正在构建 **MoFA Studio** —— 一个基于 Rust、Makepad 和 Dora 的桌面应用，用于创建和运行 AI 应用——同时也在探索 **mofa-rs**，一个下一代核心，未来可能成为替代基础。

**官网**: [mofa.ai](https://mofa.ai/)

**关键仓库：**
- 当前核心 (Python/Dora): [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- 下一代核心 (Rust): [github.com/mofa-org/mofa/tree/feature/mofa-rs](https://github.com/mofa-org/mofa/tree/feature/mofa-rs)
- Studio: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- 节点: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

---

*MoFA 是一个在 MIT/Apache-2.0 许可证下的开源项目。*
