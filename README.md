<p align="center">
  <img src="./gsoc_mofa_banner.png" alt="Google Summer of Code 2026 — MoFA" width="100%">
</p>

# Google Summer of Code 2026 — MoFA

> English Version

Welcome to MoFA's GSoC 2026 page.

- **GSoC 2026 Organization Page**: https://summerofcode.withgoogle.com/programs/2026/organizations/mofa-org
- **Project Ideas**: [ideas-list.md](./ideas-list.md)
- **Contributor Docs (mdBook)**: https://mofa.ai/mofa/
- **Discord**: https://discord.gg/hKJZzDMMm9
- **Organization Contact**: dev@mofa.ai

**All contributors will be featured on mofa.ai Developer Hall of Fame**

> **Can I start working on ideas now?** Yes. You do not need to wait for the official GSoC application period. Start exploring the codebase, pick up [open tasks](./ideas-list.md#open-tasks--start-contributing-here), and discuss your approach with mentors. Early contributions help both you and us.

["Disclaimer"  for GSoC applicants](disclaimer.md)

## GSoC 2026 Key Dates (Official)

All times below are in UTC:

- **March 16, 2026 (18:00 UTC)**: Contributor application period opens
- **March 31, 2026 (18:00 UTC)**: Contributor application deadline
- **April 30, 2026 (18:00 UTC)**: Accepted contributor projects announced
- **May 25, 2026**: Coding officially begins

Full timeline: https://developers.google.com/open-source/gsoc/timeline

## How Selection Works

Short version:

1. Mentors and Org Admins review proposals and rank them inside the organization.
2. Org Admin submits slot requests and proposal rankings to Google.
3. Google allocates slots to each org.
4. If MoFA receives `N` slots, the proposals ranked `#1` to `#N` are accepted.
5. If a contributor is selected by multiple orgs, Google admins coordinate the final matching.

---

## Getting Started

### 1. Clone and Build

**Core framework** (Rust):

```bash
git clone https://github.com/mofa-org/mofa
cd mofa
cargo build
```

**Studio application** (Rust + Makepad):
```bash
git clone https://github.com/mofa-org/mofa-studio
cd mofa-studio
./run.sh
```

> The legacy Python/Dora-based core (`pip install mofa-core`) is still available but is no longer the focus of active development. GSoC projects target the Rust codebase.

### 2. Explore

- Read the MoFA mdBook docs: https://mofa.ai/mofa/
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

### Architecture Blueprint (Required)

Your proposal must include an architecture blueprint, not only a feature list. At minimum, include:
- Component boundaries and responsibilities
- Interface contracts and data flow
- Failure handling, rollback, and recovery strategy
- Test plan and validation approach
- Delivery milestones for mainline integration

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

## How We Select Contributors

MoFA is a project in transition. We are rewriting our core in Rust, exploring new UI frameworks, and evolving our architecture as we learn. We are looking for people who want to **learn and build together with us**, not applicants who already know everything.

**What we actually care about:**
- **Can we communicate?** If you get stuck, will you tell us? If we explain something poorly, will you ask? That matters more than your resume.
- **Will you show up?** Consistent effort over the summer beats a brilliant start followed by silence.
- **Can you learn on the fly?** Nobody on our team was a Rust expert when we started either. We care about your willingness to figure things out, not what you already know.

**Issue assignment rules:**
- Issues are assigned to the **first person who comments** expressing interest, by default.
- If you want an issue created or already assigned by someone else, comment with your reason — maintainers will reassign if there is a compelling case.
- If an assignee has no visible progress and no communication for 7 days, maintainers may reassign the issue.

**What happens if multiple people want the same GSoC idea?**

Multiple people may submit proposals for the same idea. We will talk to each of you and try to find a way — maybe scoping the project differently, maybe suggesting an alternative. We would rather work something out than turn people away.

**Do I need a pre-GSoC contribution to apply?**

It helps, but it is not a hard requirement. A small PR or a thoughtful issue comment shows us you can navigate the codebase and communicate — that is the point, not gatekeeping.

---

## Contributing Before GSoC

We strongly encourage you to make at least one contribution before submitting your proposal. This helps us assess your ability and helps you understand the codebase.

We encourage you to transcend the perspective of individual features and take a holistic architectural view. The goal is to organically integrate various capabilities to establish a cohesive and comprehensive system.

### Contribution Workflow

1. **Comment on the issue** expressing your interest. Briefly describe your approach.

2. **Wait for assignment**. The issue is assigned to the first person who comments, by default. Don't start coding until assigned. If the issue is already assigned and you believe you have a compelling reason, comment to explain — maintainers will reassign if appropriate.

3. **Fork and create a branch**:
   ```bash
   git checkout -b your-branch-name
   ```

4. **Open a Draft PR** early. This shows your progress and lets mentors give feedback.

5. **Test your changes** locally before marking as "Ready for Review".

6. **Respond to feedback**. Code review is a conversation, not a verdict.

### PR Quality Expectations

- **Evaluation is based on quality and depth, not quantity.** We care about architectural coherence, testability, and maintainability.
- **Avoid skeleton-only PRs.** Include runnable examples and tests that demonstrate the feature works. If the change is large, make sure you understand the code well enough to maintain it going forward.
- **Iterate continuously.** Do not treat a PR as a one-time submission. You are expected to maintain and improve the feature until it is reasonably complete.
- **We encourage AI tooling**, but you must understand the code you submit. Avoid submitting code you cannot explain or maintain.

### Communication Channels

- **Discord**: https://discord.gg/hKJZzDMMm9 — introduce yourself in #general, GSoC discussion in #gsoc
- **Email**: dev@mofa.ai — for longer discussions or private matters
- **GitHub Issues** — technical questions, bug reports, feature requests

---

## Proposal Template

See [proposal-template.md](./proposal-template.md) for a structured template to guide your application.

---

## Guidance for GSoC Contributors Using AI Tooling

MoFA embraces AI tooling and encourages contributors to use it to improve productivity and quality. However, contributors must avoid irresponsible and unethical practices. You are ultimately responsible for all output generated with the help of AI — review it, understand it, and make sure it meets the project's standards.

For detailed guidance, please refer to Google's official document: [Guidance for GSoC Contributors using AI tooling in GSoC 2026](https://developers.google.com/open-source/gsoc/resources/ai_guidance).

---

## About MoFA

**MoFA (Modular Framework for Agents)** is an open-source framework for building AI agents.

Our journey started with a Python/Dora-based prototype that taught us what works (composition, controllable code) and what needs improvement (the difficulty of orchestrating and debugging atop an unoptimized substrate). We're now building **MoFA Studio** — a desktop application built with Rust and Makepad for creating and running AI applications, with [OminiX-MLX](https://github.com/OminiX-ai/OminiX-MLX) for on-device ML inference on Apple Silicon — while simultaneously exploring **mofa-rs**, a next-generation core that may one day serve as an alternative foundation.

**Website**: [mofa.ai](https://mofa.ai/)

**Key Repositories:**
- Core runtime: [github.com/mofa-org/mofa](https://github.com/mofa-org/mofa)
- Studio application: [github.com/mofa-org/mofa-studio](https://github.com/mofa-org/mofa-studio)
- Makepad UI components: [makepad-chart](https://github.com/mofa-org/makepad-chart), [makepad-d3](https://github.com/mofa-org/makepad-d3), [makepad-flow](https://github.com/mofa-org/makepad-flow), [makepad-element](https://github.com/mofa-org/makepad-element)

## Optional Chinese Translation

- README: [zh/README.md](./zh/README.md)
- Project ideas: [zh/ideas-list.md](./zh/ideas-list.md)
- Proposal template: [zh/proposal-template.md](./zh/proposal-template.md)

## Directory Notes

- English CFP sources and images: [ideas/README.md](./ideas/README.md)
- Chinese mirrored CFP docs: [zh/ideas/](./zh/ideas/)

---

*MoFA is an open-source project under the MIT/Apache-2.0 license.*
