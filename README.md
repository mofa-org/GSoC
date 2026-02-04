# Google Summer of Code 2025 — MoFA

> [中文版](./README-zh.md) | English Version

Welcome to MoFA's GSoC 2025 page.

- **Project Ideas**: [ideas-list.md](./ideas-list.md) ([中文版](./ideas-list-zh.md))
- **Discord**: https://discord.gg/hKJZzDMMm9
- **Organization Contact**: dev@mofa.ai

**All contributors will be featured on mofa.ai Developer Hall of Fame**

---

## Getting Started

### 1. Clone and Build

**Current core** (Python/Dora-based):
```bash
pip install mofa-core
mofa --help
```

**Next-gen core** (Rust):
```bash
git clone https://github.com/mofa-org/mofa
cd mofa
git checkout feature/mofa-rs
cargo build
```

**Studio application** (Rust + Makepad + Dora):
```bash
git clone https://github.com/mofa-org/mofa-studio
cd mofa-studio
./run.sh
```

### 2. Explore

- Read `docs/architecture.md` in the mofa repository
- Study `examples/` in mofa-rs: `monitoring_dashboard`, `multi_agent_coordination`, `react_agent`
- Build and run Studio locally

### 3. Connect

Before applying:
- Open an issue in the relevant repository to discuss your approach
- Email mentors directly (see project listings)
- Organization contact: dev@mofa.ai

---

## Who We're Looking For

**You DON'T need:**
- To be a Rust expert (we're learning too)
- Prior experience with Makepad or Dora
- Perfect knowledge of AI/LLM internals

**You DO need:**
- Willingness to learn Rust and systems programming
- Stable time commitment throughout GSoC
- Comfort with uncertainty (we're exploring alongside you)
- Ability to communicate progress and blockers

**Bonus points:**
- Systems programming experience (any language)
- UI/UX development background
- AI/ML project experience
- Prior open source contributions

---

## Writing Your Proposal

### Technical Approach

Don't aim for perfection. Show us you:
- Understand the problem space
- Have a plausible path forward
- Can break the work into milestones
- Are prepared to adapt as requirements evolve

### Timeline

Include time for:
- Learning Rust/Makepad (Weeks 1-2)
- Understanding the codebase (Week 3)
- Core implementation (Weeks 4-9)
- Testing, documentation, demo (Weeks 10-12)

### Why This Project?

Tell us:
- Why MoFA interests you
- What you hope to learn

---

## Evaluation Criteria

1. **Communication** > Existing knowledge
2. **Thoughtfulness** > Code volume
3. **Independence** > Perfect execution
4. **Community fit** > Resume credentials

---

## Contributing Before GSoC

We strongly encourage you to make at least one contribution before submitting your proposal. This helps us assess your ability and helps you understand the codebase.

### Contribution Workflow

1. **Comment on the issue** expressing your interest. Briefly describe your approach.

2. **Wait for assignment**. To avoid duplicate work, maintainers will assign the issue. Don't start coding until assigned.

3. **Fork and create a branch**:
   ```bash
   git checkout -b your-branch-name
   ```

4. **Open a Draft PR** early. This shows your progress and lets mentors give feedback.

5. **Test your changes** locally before marking as "Ready for Review".

6. **Respond to feedback**. Code review is a conversation, not a verdict.

### Communication Channels

- **Discord**: https://discord.gg/hKJZzDMMg9 — introduce yourself in #general, GSoC discussion in #gsoc
- **Email**: dev@mofa.ai — for longer discussions or private matters
- **GitHub Issues** — technical questions, bug reports, feature requests

---

## Proposal Template

See [proposal-template.md](./proposal-template.md) for a structured template to guide your application.

---

## About MoFA

**MoFA (Modular Framework for Agents)** is an open-source framework for building AI agents.

Our journey started with a Python/Dora-based prototype that taught us what works (composition, controllable code) and what needs improvement (the difficulty of orchestrating and debugging atop an unoptimized substrate). We're now building **MoFA Studio** — a desktop application built with Rust, Makepad, and Dora for creating and running AI applications — while simultaneously exploring **mofa-rs**, a next-generation core that may one day serve as an alternative foundation.

**Website**: [mofa.ai](https://mofa.ai/)

**Key Repositories:**
- Current core (Python/Dora): [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Next-gen core (Rust): [github.com/mofa-org/mofa/tree/feature/mofa-rs](https://github.com/mofa-org/mofa/tree/feature/mofa-rs)
- Studio: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Nodes: [github.com/mofa-org/mofa-node-hub](https://github.com/mofa-org/mofa-node-hub)

---

*MoFA is an open-source project under the MIT/Apache-2.0 license.*
