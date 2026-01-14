# User Guide: fbstudio Agent Spec Kit

This guide is for **Product Managers and Project Managers** who will operate this autonomous development system. No coding experience required.

---

## Quick Start

### Starting a New Project
Say to the agent:
> "Run the full development cycle to build [Your Idea]."

**Be prepared to answer:**
1.  **Scale**: How many users? (100? 10,000? 100,000?)
2.  **Platforms**: Web only? Mobile? Both?
3.  **Compliance**: Any regulations (GDPR, HIPAA)?

### Working on an Existing Project
1.  Ensure the codebase is in the workspace.
2.  Point the agent to existing docs (`PROJECT_SCOPE.txt`, `TECH_STACK.md`).
3.  Say: "Add [Feature X] to the existing project" or "Fix [Bug Y]."

---

## Quality Checkpoints

| After Phase | Review This | Look For |
|-------------|-------------|----------|
| **Requirements** | `PROJECT_SCOPE.txt` | Are NFRs (scale, security) captured? |
| **Planning** | `sprints/SPRINT-N.txt` | Does sequencing make sense? |
| **Each Sprint** | `sprints/SPRINT-N-README.md` | Is the output complete? Tests passing? |
| **Each Sprint** | Code + Docs | Does it meet `docs/DOCUMENTATION_STANDARDS.md`? |

---

## When to Escalate to a Human Engineer
*   Agent fails the same sprint 3+ times.
*   Integrating with undocumented third-party APIs.
*   Security or compliance is mission-critical (e.g., payments).
*   Performance issues require low-level profiling.

---

## Model Selection Guide
For optimal results, switch models in Antigravity settings:

| Task | Recommended Model |
|------|-------------------|
| Requirements & PO Review | Gemini 3 Pro or Opus 4.5 (Deep Reasoning) |
| Planning & Testing | Gemini 3 Flash (Fast & Efficient) |
| Code Generation | Gemini 3 Flash (Routine), Pro for complex logic |

---

## Managing Long Projects (Context Limits)
For projects spanning many sprints:
1.  Start a **new Antigravity thread** for each major phase.
2.  Load only the relevant artifacts (`PROJECT_SCOPE.txt`, latest `SPRINT-N-README.md`).
3.  The agent will read context from files, not conversation history.
