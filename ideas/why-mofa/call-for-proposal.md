# Why MoFA

### After LangGraph, CrewAI, AutoGen, and Other Agent Frameworks

> GSoC 2026 Call for Proposal — Critical Analysis Track

---

## 1. Introduction and Challenges: Understanding the Existing Landscape

This folder contains three in-depth presentations analyzing the dominant AI agent frameworks. **We strongly encourage you to study all three before writing your proposal.** They are not marketing material — they are critical analyses of what each framework does well, what it gets wrong, and where the market is heading.

### LangGraph: The Graph-Based Production Standard

**"LangGraph: The Evolution of AI Agent Orchestration"** (`LangGraph_ The Evolution of AI Agent Orchestration.pptx`)

<p align="center">
  <img src="./images/what-is-langgraph.png" alt="What is LangGraph?" width="80%">
</p>

LangGraph is a graph-based orchestration framework for building complex, stateful multi-agent AI workflows. Part of the LangChain ecosystem with 6.17M+ monthly downloads, it uses directed graphs with nodes for actions and edges for flow control, enabling branching, looping, and persistent state management. It positions itself as the "USB-C universal connector" for AI agent interoperability.

Key observations from the presentation:
- LangGraph dominates the production-grade agent framework space, with deployments at Klarna, Replit, and Elastic
- The framework landscape has consolidated around three winners: LangGraph (production standard), CrewAI (rapid prototyping), and Microsoft Agent Framework (enterprise)
- LangGraph's strategic response to vibe coding: "Prototype with Vibe, productionize with LangGraph"
- LangGraph Studio provides visual debugging and orchestration
- The hidden cost of vibe coding — initial 3-5x velocity gains dissipate after two months, with 30% increase in static analysis warnings and 41% rise in code complexity

### CrewAI: The Multi-Agent Orchestration Platform

**"CrewAI: Orchestrating the Future of AI-Driven Development"** (`CrewAI_ Orchestrating the Future of AI-Driven Development.pptx`)

<p align="center">
  <img src="./images/what-is-crewai.png" alt="What is CrewAI?" width="80%">
</p>

CrewAI organizes AI agents into orchestrated teams with roles (Manager, Researcher, Worker), shifting from syntax-level coding to architectural thinking. With 100,000+ certified developers and no-code capabilities via CrewAI Studio, it pioneers the "vibe coding" paradigm where production-ready workflows are built in minutes using natural language.

<p align="center">
  <img src="./images/crewai-architecture.png" alt="CrewAI Architecture: Flows and Crews" width="80%">
</p>

Key observations:
- Two-layer architecture: Flows (event-driven execution, conditional logic, data persistence) and Crews (intelligence layer with role-based agents)
- The "No Code" revolution — natural language input to production agents, Python code export for customization
- The paradox of agents that write code: "CrewAI's answer lies not in replacement but in elevation — humans become architects and orchestrators while agents handle implementation"
- Training agents without programming through human feedback loops (`crewai train -n <iterations>`)
- Enterprise adoption: 70% faster legacy modernization, 75% time reduction in back-office automation

### Microsoft AutoGen: The Enterprise Multi-Agent Framework

**"Microsoft AutoGen: The AI Agent Framework Revolutionizing Software Development"** (`Microsoft AutoGen_ The AI Agent Framework Revolutionizing Software Development.pptx`)

<p align="center">
  <img src="./images/what-is-autogen.png" alt="What is AutoGen?" width="80%">
</p>

AutoGen is Microsoft's open-source framework for multi-agent AI applications and automated programming. It features a three-layer architecture (Core → AgentChat → Extensions), conversational workflows, and automatic code generation and execution in sandboxed containers.

<p align="center">
  <img src="./images/autogen-three-layer-architecture.png" alt="AutoGen Three-Layer Architecture" width="80%">
</p>

Key observations:
- Three-layer architecture provides flexibility at the cost of complexity
- AutoGen Studio offers no-code visual building, but is tightly coupled to Microsoft's ecosystem
- Automatic code generation with Docker-based sandboxed execution
- Strategic convergence: AutoGen + Semantic Kernel → Unified Microsoft Agent Framework (by 2026)
- Enterprise results: 73% increase in agent efficiency, 24% cost reduction, but heavy Microsoft lock-in
- Human-in-the-loop as a core design principle, not an afterthought

---

## 2. Why We Still Need Another Agent Framework — What the Big Three Fail to Address

After studying LangGraph, CrewAI, and AutoGen, a natural question arises: **why bother building MoFA?** The market already has well-funded, widely-adopted frameworks. Here is our honest assessment of the gaps.

<p align="center">
  <img src="./images/framework-landscape-consolidation.png" alt="Framework Landscape Consolidation" width="80%">
</p>

### Gap 1: Vendor Lock-in and the Closed Ecosystem Problem

LangGraph is inseparable from LangChain. AutoGen is converging into Microsoft's proprietary agent platform alongside Semantic Kernel. CrewAI, while more independent, still designs primarily around OpenAI-compatible APIs. **None of them are truly model-agnostic or infrastructure-agnostic at the systems level.** When your agent framework is a product of a company whose business model is selling you an API, the framework will always optimize for that API — not for your use case.

MoFA's position: an open-source, community-governed framework with no commercial API to sell. The framework should serve the developer, not a business model.

<p align="center">
  <img src="./images/microsoft-strategic-convergence.png" alt="Microsoft's Strategic Vision: The Convergence" width="80%">
</p>

### Gap 2: The Edge and On-Device Blind Spot

All three major frameworks assume cloud-first deployment. LangGraph's production story is LangSmith (cloud). AutoGen's execution sandbox is Docker containers. CrewAI's scaling story is cloud orchestration. **None of them take on-device, edge-first inference seriously.**

On a 16GB MacBook with Apple Silicon unified memory, you don't need HTTP calls to Ollama or OpenAI. You need direct Rust-level inference calls with zero-copy tensor passing between models. This is a fundamentally different architectural assumption — and it's one that MoFA is uniquely positioned to explore (see [Idea 3: Edge Model Orchestrator](../../ideas-list.md)).

### Gap 3: The Debugging and Observability Desert

LangGraph has LangSmith for tracing. AutoGen has AutoGen Studio for visual building. CrewAI has basic logging. But **none of them provide true time-travel debugging for multi-agent systems.** When a 5-agent pipeline fails intermittently, developers are left reading log files. There is no equivalent of Chrome DevTools for agents — no ability to pause, step through, inspect state, and replay with modifications.

This is not just a nice-to-have; it's a prerequisite for production adoption. MoFA's [Session Recorder & Visual Debugger (Idea 4)](../../ideas-list.md) aims to make this a first-class capability.

### Gap 4: The Composition Problem

<p align="center">
  <img src="./images/crewai-agents-paradox.png" alt="Agents That Write Code: The Paradox" width="80%">
</p>

CrewAI's team metaphor (Manager, Researcher, Worker) is intuitive but rigid. LangGraph's graph model is flexible but requires deep expertise. AutoGen's conversational approach is natural but hard to control at scale. **None of them solve the fundamental problem: how do you compose agents built by different developers, with different assumptions, into a reliable system?**

In the vibe coding era, this becomes critical. Three developers each vibe-code a component. Who ensures they work together? Current frameworks punt this to the developer. MoFA aims to make composition a framework responsibility.

### Gap 5: Performance and Systems-Level Thinking

LangGraph, CrewAI, and AutoGen are all Python frameworks. They inherit Python's performance characteristics: GIL limitations, high memory overhead, and slow startup. For a CLI tool, a desktop application, or an edge device, **Python is the wrong substrate.** MoFA's bet on Rust is not about language tribalism — it's about building a framework that can run everywhere, from a MacBook to a Raspberry Pi, with predictable performance.

### Gap 6: Framework Philosophy vs. API Wrapper

<p align="center">
  <img src="./images/langgraph-vibe-vs-production.png" alt="Vibe Coding (Prototyping) vs. LangGraph (Production)" width="80%">
</p>

Most "agent frameworks" are really **API wrapper libraries** — they make it convenient to call LLMs and chain outputs together. A true framework provides Inversion of Control: the framework calls your code, not the other way around. It manages lifecycle, enforces contracts, handles errors, and provides guarantees. **The agent framework space is dominated by libraries pretending to be frameworks.** MoFA aims to be a real framework — with opinions about how agents should be built, composed, and run.

---

## 3. Call for Proposal — We Want Your Critical Thinking

We are not asking you to accept the arguments above uncritically. In fact, we hope you'll challenge them.

### What We're Looking For

- **Genuine analysis, not cheerleading.** If you think LangGraph already solves the composition problem well enough, argue for it. If you think MoFA's Rust bet is wrong, tell us why. We want proposals that reflect real thinking.
- **Experimentation.** Build something small with LangGraph, CrewAI, or AutoGen. Then try to build the same thing with MoFA. Document what was easy, what was hard, what was impossible. First-hand experience beats secondhand opinions.
- **Identify a real gap.** The six gaps above are our perspective. You might find different ones. You might find that some of our claimed gaps don't actually matter in practice. Your proposal should stake a position.
- **Propose a concrete contribution.** After your analysis, what should MoFA do about it? This could be a design document, a prototype, a benchmark, a new architecture — or an argument that MoFA should change direction entirely.

### Suggested Approaches

1. **Comparative deep dive**: Pick one gap (e.g., debugging, composition, edge deployment). Build the same agent system on two or three frameworks. Document the developer experience, performance, and failure modes.
2. **Architecture critique**: Study MoFA's current codebase ([mofa](https://github.com/mofa-org/mofa)). Identify where the architecture supports or contradicts the claims made above. Propose concrete changes.
3. **Gap validation**: Take one of the six gaps and try to disprove it. Can you build a production-quality debugging experience in LangGraph? Can you run CrewAI efficiently on edge devices? Show your work.
4. **New gap discovery**: Through your own experience with agent frameworks, identify a problem we haven't listed. Propose how MoFA should address it.

### How to Get Started

1. **Study the presentations** in this folder. Take notes. Form opinions.
2. **Try the frameworks.** Install LangGraph, CrewAI, and/or AutoGen. Build something real. Don't stop at the tutorial.
3. **Clone and build MoFA** ([mofa](https://github.com/mofa-org/mofa)). Run examples. See where it stands today.
4. **Read the [ideas list](../../ideas-list.md)** and the [framework-for-ai CFP](../framework-for-ai/call-for-proposal.md). Understand the full picture.
5. **Join the conversation** on [Discord](https://discord.gg/hKJZzDMMm9). Ask hard questions. Challenge assumptions.
6. **Write a proposal** that we'll learn from, whether or not you're selected.

### A Note on Honesty

MoFA is early. Our Rust codebase is young. We don't have LangGraph's 6M monthly downloads or Microsoft's enterprise backing. We are a small team with a thesis about what agent frameworks should be. If you join us, you'll be building something from closer to the ground up — and that means your ideas will have outsized impact. But it also means you'll face real uncertainty.

We think that's exciting. We hope you do too.

---

*MoFA is an open-source project under the MIT/Apache-2.0 license.*
*Organization contact: dev@mofa.ai | Discord: https://discord.gg/hKJZzDMMm9*
