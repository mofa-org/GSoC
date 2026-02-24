# MoFA's HCI for AI Native Agent Framework

> GSoC 2026 Call for Proposal — Human-Computer Interaction Track

---

This is an intentionally open topic. We don't have all the answers — and that's the point.

As AI agents grow more powerful, the hardest unsolved problem is not "how to make agents smarter" but **"how should humans and agents work together?"** MoFA is an AI-native agent framework built in Rust. But a framework is only as useful as the experience it provides to the humans who build with it, oversee it, and ultimately depend on it.

This CFP invites you to think deeply about the HCI challenges facing AI agent frameworks — and to propose concrete ideas for how MoFA should address them.

---

## The Core Tension

AI agent frameworks sit in a unique position: they mediate between **human developers** and **increasingly capable AI**. This creates a fundamental tension:

- **Too much control** and the developer becomes a bottleneck — manually approving every agent action, painstakingly configuring every workflow step, defeating the purpose of autonomous agents.
- **Too little control** and the developer loses understanding — agents take actions the developer can't predict, debug, or explain to stakeholders. Trust erodes.

Every design decision in MoFA's interface layer is a stance on where to draw this line. We invite you to help us find the right balance.

---

## Open Questions We Want You to Explore

### 1. Human-in-the-Loop: Beyond the Approval Button

<p align="center">
  <img src="./images/ai-native-frameworks-hitl.png" alt="AI-Native Frameworks: Human-in-the-Loop and Visual Builders" width="80%">
</p>

Current approaches to human-in-the-loop are crude: pause execution, show the developer what the agent wants to do, wait for "approve" or "reject." This doesn't scale.

Questions worth investigating:
- What should human-in-the-loop look like for a 10-agent pipeline processing 1,000 requests per hour? You can't approve each one manually.
- Can we design **policy-based oversight** — where the human defines rules ("never send emails without my approval", "auto-approve database reads but flag writes") and the framework enforces them?
- How do we handle **graduated autonomy** — agents that earn more freedom as they demonstrate reliability? What does the UX for this look like?
- When an agent is uncertain, how should it ask for help? A chat message? A structured form? A diff view? How do you design an interruption that is informative without being overwhelming?

### 2. Debugging and Monitoring: Making the Invisible Visible

Multi-agent systems are opaque. Messages flow between agents, state mutates, LLMs make decisions based on context windows the developer can't see. Traditional debugging tools (breakpoints, stack traces, log files) were designed for deterministic, single-threaded programs.

Questions worth investigating:
- What does a **debugger for non-deterministic systems** look like? Agents don't follow a call stack — they follow conversations. How do you visualize that?
- Can we build **"why did this happen?"** tooling — given an agent's action, trace back through the message history, context window, and decision points to explain *why*?
- How should monitoring differ between **development** (I'm building an agent and it's broken) and **production** (I have 50 agents running and I need to know if any are misbehaving)?
- What can we learn from existing monitoring paradigms (Grafana for infrastructure, Chrome DevTools for web, Xcode Instruments for mobile) and what is fundamentally different about agent monitoring?
- How do you monitor something that is **probabilistic**? An agent might give a slightly different answer each time. When does "different" become "wrong"?

### 3. CLI, TUI, GUI, and Cross-Media Interfaces

Here's how existing frameworks approach the studio/IDE experience — each with different trade-offs:

<p align="center">
  <img src="./images/crewai-studio-no-code.png" alt="CrewAI Studio: The No Code Revolution" width="80%">
</p>

<p align="center">
  <img src="./images/autogen-studio-no-code.png" alt="AutoGen Studio: The No-Code Revolution" width="80%">
</p>

<p align="center">
  <img src="./images/langgraph-studio-response.png" alt="LangGraph's Strategic Response: LangGraph Studio" width="80%">
</p>

MoFA is a framework, not a single application. Developers will interact with it through multiple interfaces:

- **CLI** (`mofa-cli`): For scripting, automation, CI/CD pipelines, quick commands
- **TUI** (Terminal UI): For developers who live in the terminal but need richer visualization than plain text
- **GUI** (MoFA Studio): For visual workflow building, drag-and-drop agent composition, real-time dashboards
- **Cross-media**: Voice interfaces, browser extensions, IDE plugins, mobile companions

Questions worth investigating:
- How should information be distributed across these interfaces? Should the CLI be a simplified version of the GUI, or should each interface have a fundamentally different interaction model?
- What is the **right level of abstraction** for each interface? A CLI user thinks in commands and pipelines. A GUI user thinks in visual flows. An IDE user thinks in code with visual assists. How does the same underlying framework serve all three?
- How do we ensure **consistency** across interfaces without forcing the lowest-common-denominator experience?
- What can we learn from tools that do this well? (e.g., Docker CLI + Docker Desktop, kubectl + Lens, git CLI + GitKraken)
- Is there a role for **conversational interfaces** — interacting with MoFA itself through natural language? What would `mofa chat "build me an agent that monitors my email"` look like?

### 4. The Role of the Framework Between Human and AI

<p align="center">
  <img src="./images/strategic-recommendations.jpeg" alt="Strategic Recommendations for Developers: Hybrid Approach" width="80%">
</p>

This is the meta-question underlying all of the above.

Agent frameworks like LangGraph, CrewAI, and AutoGen have largely focused on the **AI side** — how to make agents more capable, how to orchestrate complex workflows, how to integrate more tools. The human side of the interface has been an afterthought: a YAML config file, a Python script, maybe a basic web UI.

MoFA has a chance to do this differently. Questions worth investigating:
- Should the framework be **transparent** (show everything the agent is doing) or **intentional** (show only what the developer needs to see, when they need to see it)?
- How should the framework communicate **uncertainty**? When an agent is 60% confident, how does the human interface reflect that — and what actions does it enable?
- What does **progressive disclosure** look like for agent frameworks? A beginner should be able to run a simple agent without understanding the internals. An expert should be able to inspect every message, every state transition, every LLM call.
- How do we design for **trust calibration** — helping developers develop accurate mental models of what their agents can and cannot do?

---

## What We're Looking For in Proposals

This is a research-flavored track. We value:

- **Literature review**: What does HCI research say about human-AI collaboration? What existing work on mixed-initiative interfaces, explainable AI, or human-robot interaction is relevant?
- **User research**: Talk to developers who build agents. What are their pain points? What do they wish existed? Even a few informal interviews are valuable.
- **Prototypes over specifications**: A rough working prototype of one idea is worth more than a polished document describing ten ideas. Build something in MoFA Studio (Makepad), or a TUI prototype, or even paper mockups — show us what you mean.
- **Concrete proposals**: After exploring the space, pick one or two ideas and go deep. How would you implement them in MoFA? What would the architecture look like? What are the trade-offs?

### Relevant MoFA Ideas

Several existing GSoC ideas intersect with this topic:

- [Idea 2: Studio Observability Dashboard](../../ideas-list.md) — real-time monitoring and visualization
- [Idea 4: Session Recorder & Visual Debugger](../../ideas-list.md) — time-travel debugging for agents
- [Idea 6: Makepad AI Application Toolkit](../../ideas-list.md) — UI components for AI applications
- [Open Task 17](../../ideas-list.md): Human-in-the-loop — pause at any node for manual review
- [Open Task 18](../../ideas-list.md): Support visual debugging

You can build on any of these, combine them, or propose something entirely different.

### How to Get Started

1. **Use agent frameworks.** Build something non-trivial with LangGraph, CrewAI, or AutoGen. Pay attention to the *developer experience* — not just whether it works, but how it *feels* to build, debug, and monitor.
2. **Clone and run MoFA Studio** ([mofa-studio](https://github.com/mofa-org/mofa-studio)). Understand what exists today.
3. **Read HCI literature.** Look into mixed-initiative interfaces, human-AI teaming, explainable AI. The ACM CHI and IUI conference proceedings are good starting points.
4. **Sketch ideas.** Paper prototypes, wireframes, TUI mockups — anything that makes your thinking concrete.
5. **Join [Discord](https://discord.gg/hKJZzDMMm9)** and share your thinking. We want to discuss these questions openly.

---

## A Final Thought

The most important interface in an AI agent framework is not the one between code and LLM. It's the one between human and system. Get that wrong, and it doesn't matter how sophisticated your agents are — nobody will trust them enough to use them in production.

We think this is one of the most important open problems in the agent framework space. If you do too, we'd love to hear from you.

---

*MoFA is an open-source project under the MIT/Apache-2.0 license.*
*Organization contact: dev@mofa.ai | Discord: https://discord.gg/hKJZzDMMm9*
