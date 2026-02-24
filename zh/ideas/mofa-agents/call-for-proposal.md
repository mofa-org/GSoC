# MoFA Agents：支持所有模型

> GSoC 2026 提案征集 — 模型编排方向

---

## 1. 开放问题

AI Agent 不只是聊天——它们还要听、看、说、画和推理。一个 Agent 工作流可能串联语音识别模型（ASR）、大语言模型（LLM）、文本转语音模型（TTS）和图像生成模型——全在一条管道中。然而，当今大多数工具只支持其中很窄的一部分。

MoFA 的雄心是成为一个**将所有主要用途为"推理"的模型都视为一等公民**的框架。本 CFP 请你深入思考三个难题：

### 问题 1：MoFA 应该如何支持 LLM、VLM、TTS、ASR 及所有其他推理模型？

当今的模型版图庞大且碎片化：

| 模态 | 示例 | 输入 → 输出 |
|------|------|-------------|
| **LLM**（大语言模型） | Qwen、Llama、Mistral、DeepSeek | 文本 → 文本 |
| **VLM**（视觉语言模型） | Qwen-VL、LLaVA、Gemma 3 | 图像+文本 → 文本 |
| **ASR**（自动语音识别） | Whisper、FunASR Paraformer | 音频 → 文本 |
| **TTS**（文本转语音） | GPT-SoVITS、Bark、VITS | 文本 → 音频 |
| **图像生成** | Stable Diffusion、FLUX | 文本 → 图像 |
| **嵌入模型** | BGE、E5、GTE | 文本 → 向量 |
| **重排序模型** | BGE-Reranker、Cohere | 文本对 → 分数 |
| **视频生成** | Wan、CogVideo | 文本 → 视频 |
| **多模态（Omni）** | GPT-4o、Qwen-Omni | 任意 → 任意 |

每种模态有不同的输入/输出类型、延迟特征、内存占用和执行模式（流式 vs. 批量、实时 vs. 离线）。一个声称"支持所有模型"的框架，必须拥有一个足够通用以覆盖这种多样性的抽象，同时又不能抽象到毫无用处。

**设计挑战**：MoFA 中"模型"的正确 trait/接口是什么？是一个通用的 `InferenceBackend` trait，还是一系列模态特定的 trait（`TextGenerator`、`SpeechRecognizer`、`ImageGenerator`……）？如何处理跨多种模态的模型（如 GPT-4o 同时接受文本、图像和音频）？

### 问题 2：未来新模型、新类型模型出现时，MoFA 如何快速支持？

AI 模型的创新速度令人目不暇接。2023 年，"模型"意味着 LLM。到 2024 年，视觉语言模型和语音模型已成主流。2025 年，能在单一架构中处理文本、图像、音频和视频的 Omni 模型出现了。当你读到这段话时，可能已经有我们无法预测的新模态出现。

一个为今天的模型类型硬编码支持的框架，明天就会过时。MoFA 需要一个**模型集成架构**，使得：

- 无需修改框架核心代码即可添加新模型类型
- 社区贡献者可以独立添加新模型支持
- 模型提供商可以编写自己的 MoFA 适配器
- 优雅地处理不符合现有类别的模型

**设计挑战**：如何设计一个既易于扩展又类型安全的模型集成插件/适配器系统？如何处理通用接口（易于添加新模型）和特定接口（更好的工具支持、错误提示和性能）之间的张力？

### 问题 3：为什么 MoFA 能比现有模型编排器做得更好？

这是最难的问题，需要诚实的回答。

<p align="center">
  <img src="../../../ideas/mofa-agents/images/ai-native-frameworks-ecosystem.png" alt="AI 原生框架生态系统" width="80%">
</p>

---

## 2. 格局：现有方案及其差距

### 当前模型编排生态

让我们诚实地审视现有方案——每个工具做对了什么、做错了什么。

#### Ollama —— LLM 的 Docker

Ollama 让本地 LLM 推理变得触手可及：`ollama run llama3` 即可开始对话。它支持 100+ 个 LLM 家族和部分视觉模型，配有简洁的 OpenAI 兼容 API。但 Ollama 是**纯文本输入/文本输出**。没有原生 ASR、TTS 或图像生成。即使模型理论上支持音频功能（如 MiniCPM-o），实际上也无法工作。一次运行一个模型，没有多模型编排。

#### LM Studio —— 桌面端 LLM 体验

LM Studio 提供精美的 GUI，用于下载和运行本地 LLM，在 macOS 上同时支持 llama.cpp 和 MLX 后端。覆盖 LLM 和 VLM，但与 Ollama 类似，**没有原生音频或图像生成**。TTS 和 ASR 需要集成外部工具。闭源。单模型为主。

#### vLLM —— 生产级推理引擎

vLLM 是高吞吐量 LLM 推理服务的黄金标准，拥有 PagedAttention、连续批处理和推测解码等技术。**vLLM-Omni**（2025 年底发布）将其扩展到多模态服务——模态编码器（ViT、Whisper）、LLM 核心和模态生成器（DiT 用于图像/音频输出）。但 vLLM **仅支持 NVIDIA GPU，面向服务器部署**。不支持 Apple Silicon。不适合端侧或边缘部署。

#### HuggingFace —— 通用模型中心

HuggingFace 托管 200 万+ 模型，覆盖所有模态。`transformers` 库支持 LLM、VLM、ASR、TTS、图像生成等。但它是**纯 Python**，端侧部署开销很大。Apple Silicon 的 MPS 后端存在缺陷（许多场景无法使用 FP16，部分操作回退到 CPU）。没有内置多模型编排——需要自己组装。

#### Cherry Studio —— 通用客户端

Cherry Studio 通过统一桌面界面连接 50+ 个云端和本地 AI 提供商。但它**是客户端，不是引擎**——完全依赖外部提供商进行实际推理。没有原生 TTS、ASR 或图像生成。它聚合，但不编排。

### MoFA 的基础构件

MoFA 并非从零开始。两个现有项目构成了基础：

#### OminiX-MLX —— Apple Silicon 上的原生 Rust 推理

[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) 是一个用于 Apple Silicon 高性能 ML 推理的 Rust 生态系统，使用 Apple 的 MLX 框架进行 Metal GPU 加速。其三层架构——`mlx-rs`（MLX 的 Rust 绑定）、`mlx-rs-core`（共享推理基础设施）和模型特定 crate——已支持：

- **LLM**：Qwen2/3、GLM-4、Mixtral、Mistral、MiniCPM
- **VLM**：Moxin-7B（DINOv2 + SigLIP + Mistral）
- **ASR**：FunASR Paraformer
- **TTS**：GPT-SoVITS 语音克隆
- **图像生成**：FLUX.2-klein、Z-Image

关键优势：通过 Apple Silicon 统一内存实现**模型间零拷贝张量传递**。ASR 模型的输出张量可以直接传给 LLM，无需序列化。这在 Python 框架中从架构上就不可能实现。

#### mofa-local-llm —— HTTP 桥接层

[mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) 将 OminiX-MLX 封装在 OpenAI 兼容的 HTTP API 服务器后面。基于 Tokio 异步运行时构建，推理在专用 OS 线程上运行，通过消息传递通道与异步 HTTP 服务器通信。它从配置文件自动检测模型类型并路由到相应的推理引擎。

目前非常早期（基本的 Qwen2 LLM 推理已验证；其他模态尚未测试）。

### 差距：尚未有人构建的东西

以下是诚实的对比：

| 能力 | Ollama | LM Studio | vLLM | HuggingFace | Cherry Studio | MoFA（当前） |
|------|--------|-----------|------|-------------|---------------|--------------|
| LLM | 是 | 是 | 是 | 是 | 通过提供商 | 是 |
| VLM | 是 | 是 | 是 | 是 | 预览中 | 有限 |
| ASR | 否 | 否 | RC 阶段 | 是 | 否 | 未测试 |
| TTS | 否 | 否 | RC 阶段 | 是 | 否 | 未测试 |
| 图像生成 | 否 | 否 | RC 阶段 | 是 | 否 | 未测试 |
| 多模型编排 | 否 | 否 | 是（Omni） | 手动 | 聚合器 | 否 |
| 端侧 Apple Silicon | Metal/llama.cpp | Metal+MLX | 否 | MPS（部分） | 否 | 原生 Rust+Metal |
| 模型间零拷贝 | 否 | 否 | 否 | 否 | 否 | 架构上可行 |
| Rust 原生 | 否 | 否 | 否 | 否 | 否 | 是 |

**差距所在**：目前没有任何工具能提供一个统一的、端侧的、多模态推理平台——通过单一框架编排 LLM + VLM + ASR + TTS + 图像生成，配合智能资源管理和零拷贝数据传递。

OminiX-MLX 在 Apple Silicon 上的模态覆盖最广，但缺乏编排。vLLM-Omni 拥有最成熟的编排架构，但仅支持 NVIDIA 且面向服务器。HuggingFace 模型覆盖最广，但仅限 Python 且没有内置编排。

<p align="center">
  <img src="../../../ideas/mofa-agents/images/ai-transforming-frameworks.jpeg" alt="AI 如何改变框架：新机遇" width="80%">
</p>

### 为什么 MoFA 能做得更好——诚实的论证

MoFA 的结构优势是真实的，但目前是*潜力*，而非*已验证*：

1. **Rust 原生加零拷贝语义。** 当 ASR 输出在 Apple Silicon 统一内存中传递给 LLM 时，Python 框架必须序列化和反序列化张量。MoFA（通过 OminiX-MLX）可以直接传递 MLX Array——零拷贝、零开销。这一优势在多模型管道中会累积放大。

2. **框架级编排，而非后期拼凑。** vLLM-Omni 在 LLM 推理引擎之上添加多模态支持。MoFA 可以从头设计多模型编排——调度、内存管理和管道构建作为框架的一等公民概念。

3. **可插拔的后端抽象。** MoFA 的 `InferenceBackend` trait（参见 [Idea 3](../../ideas-list.md)）设计为后端无关。OminiX-MLX 是默认的 macOS 后端，但相同的 Agent 代码应该能在 Linux 的 CUDA 后端或未来其他硬件的 NPU 后端上运行——无需修改。

4. **端侧优先，云端兼容。** 大多数编排器要么是云优先（vLLM、HuggingFace Endpoints），要么是纯桌面（Ollama、LM Studio）。MoFA 的目标是端侧优先、云端作为回退——同一个 Agent 运行在 MacBook、树莓派或云 GPU 上，由框架处理差异。

5. **Agent 原生，而非模型服务。** Ollama、vLLM 和 LM Studio 是*模型服务器*——它们提供推理服务。MoFA 是一个*Agent 框架*——模型是 Agent 使用的工具。这意味着 MoFA 可以提供 Agent 级别的抽象："使用当前最佳可用模型完成此任务"、"内存压力下回退到更小的模型"、"如果本地推理太慢则路由到云端"。

但这些都是架构上的押注，而非已交付的功能。验证它们正是本 CFP 的意义所在。

---

## 3. 提案征集——给我们一份可行的行动计划

我们已经提出了问题并展示了行业格局。现在我们想看到**你的计划**——MoFA 应该如何真正解决这个问题。

### 你的提案应该包含什么

#### A. 模型抽象设计

为 MoFA 如何表示模型提出具体的抽象方案：

- 核心 trait/接口长什么样？给我们看 Rust 签名，不是纯文字描述。
- 如何处理各模态输入/输出类型的多样性？
- 如何处理跨多种模态的模型（如 Omni 模型）？
- 如何在通用性（易于添加新模型类型）和特异性（常见模型类型的良好开发体验）之间取得平衡？

#### B. 模型集成架构

提出新模型如何被添加到 MoFA：

- 模型适配器/插件长什么样？请走一遍为新模型家族添加支持的流程。
- 模型适配器在运行时如何被发现、加载和管理？
- 不同后端（macOS 上的 OminiX-MLX、Linux 上的 CUDA、作为回退的云端 API）下如何工作？
- MoFA 如何处理不同的模型格式（safetensors、GGUF、PyTorch checkpoints）？

#### C. 多模型管道设计

提出多个模型如何在单个 Agent 管道中协同工作：

- Agent 如何表达"我需要 ASR，然后 LLM，然后 TTS"的管道？
- 框架如何处理模型间的数据传递（特别是统一内存上的零拷贝）？
- 当多个模型争夺有限内存时，调度如何工作？
- 管道中某个模型失败或不可用时，会发生什么？

#### D. 可行性验证

证明你的计划是基于现实的：

- 选择一个具体的管道（如 ASR → LLM → TTS），概述它在 MoFA 中如何端到端工作。
- 找出你计划中最大的技术风险，并提出缓解方案。
- 提出分阶段时间线：第 1-4 周、5-8 周、9-12 周分别能构建什么？
- 你会在哪些现有 MoFA 代码（[mofa](https://github.com/mofa-org/mofa)、[mofa-local-llm](https://github.com/mofa-org/mofa-local-llm)、[OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX)）之上构建，哪些需要从头编写？

### 我们看重什么

- **具体胜于抽象。** 给我们看代码草图、API 设计、架构图——而不只是功能要点列表。
- **诚实的范围界定。** 一份承认"多后端支持是延伸目标；核心交付物是 Apple Silicon 上可工作的 ASR→LLM→TTS 管道"的提案，胜过一份承诺一切的提案。
- **与现有工作的深度互动。** 我们希望看到你已经克隆了 mofa-local-llm、尝试了 OminiX-MLX，并在提出下一步构建计划之前理解了现有成果。
- **面向未来的可扩展性。** 你的设计应该让*下一个*贡献者能轻松添加对尚不存在的模型类型的支持。

### 如何开始

1. **克隆并构建技术栈。**
   - [mofa](https://github.com/mofa-org/mofa) — 核心框架
   - [mofa-local-llm](https://github.com/mofa-org/mofa-local-llm) — HTTP 推理桥接层
   - [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) — 推理引擎（仅 macOS）
2. **运行推理。** 通过 mofa-local-llm 运行 Qwen 模型。如果你有 Apple Silicon，尝试在 OminiX-MLX 中加载不同类型的模型。
3. **研究竞品。** 安装 Ollama 和/或 LM Studio。如果你有 NVIDIA GPU，尝试 vLLM。了解当前的开发者体验是什么样的。
4. **阅读 [Idea 3: 边缘模型调度器](../../ideas-list.md)** — 它涵盖了多模型编排的调度和内存管理方面。
5. **设计你的抽象。** 在写代码之前，先勾画 trait 层次结构。思考边界情况。在 [Discord](https://discord.gg/hKJZzDMMm9) 上讨论你的设计。
6. **撰写一份包含可行分阶段行动计划的提案。** 参见[提案模板](../../proposal-template.md)。

### 关于范围的说明

这是一个庞大的问题空间。我们不指望单个 GSoC 项目解决所有问题。一份优秀的提案会**大胆缩小范围**——选择最有影响力的切片，高质量交付，并设计好抽象使未来的贡献者可以扩展。"一条可工作的 ASR→LLM→TTS 管道，配合一个他人可实现的清晰模型 trait"是比"每种模态半成品支持"更好的成果。

---

*MoFA 是 MIT/Apache-2.0 许可证下的开源项目。*
*组织联系方式：dev@mofa.ai | Discord：https://discord.gg/hKJZzDMMm9*
