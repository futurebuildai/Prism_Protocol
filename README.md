# Antigravity Prism Protocol

Welcome to **Antigravity Prism**. This repository implements a **Google L7-Quality Autonomous Software Organization**. It is not just code; it is a system of specialized agents, contracts, and workflows that function as a mature engineering team.

## Hybrid Workflow: Antigravity + Claude Code

The Prism Protocol operates in **hybrid mode**:
- **Antigravity** (Claude.ai): Planning, design, spec generation, and auditing
- **Claude Code** (Terminal): Code execution, testing, and implementation

```
/product → [TASKNAME]_PRD.md → /devteam → [TASKNAME]_specs.md → /software_engineer → TERMINAL PROMPT
```

---

## Quick Start

### 1. Start with `/product`

Every task begins by establishing a **Task Name** in the Product phase:

```
/product Add user authentication for the API
```

The agent will:
1. Establish `[TASKNAME]` (e.g., `USER_AUTH`)
2. Create an Implementation Plan
3. Generate `docs/USER_AUTH_PRD.md`
4. Provide handoff: "Invoke `/devteam USER_AUTH` to proceed."

### 2. Continue with `/devteam [TASKNAME]`

```
/devteam USER_AUTH
```

The agent will:
1. Validate `docs/USER_AUTH_PRD.md` exists
2. Create `specs/USER_AUTH_specs.md`
3. Provide handoff: "Invoke `/software_engineer USER_AUTH` to proceed."

### 3. Execute with `/software_engineer [TASKNAME]`

```
/software_engineer USER_AUTH
```

The agent will:
1. Run L7 Spec Review Gate (Pre-Mortem, Antagonist, Complexity)
2. Generate a **TERMINAL PROMPT** with L7 recursive audits
3. Include Zero-Trust Review before commit instructions

### 4. Execute in Terminal

Copy the TERMINAL PROMPT and run in Claude Code:

```bash
claude -p "[Paste TERMINAL PROMPT here]"
```

### 5. Audit and Finalize

Paste the terminal output back into Antigravity for the Audit phase. On pass, invoke `/NEXT` to finalize.

---

## The Three Departments

### 1. Product Team (`/product`)
- **Mission**: Discovery, Strategy, Definition
- **Use when**: You have an idea, problem, or business goal
- **Output**: `docs/[TASKNAME]_PRD.md`

### 2. Dev Team (`/devteam`)
- **Mission**: Architecture, Engineering, Delivery
- **Use when**: You have a PRD and need technical specs
- **Output**: `specs/[TASKNAME]_specs.md`

### 3. Software Engineer (`/software_engineer`)
- **Mission**: Context preparation, L7 review, prompt generation
- **Use when**: You have specs and need executable instructions
- **Output**: TERMINAL PROMPT for Claude Code

### 4. Ops Team (`/ops`)
- **Mission**: Reliability, Security, Support
- **Use when**: Something is broken, slow, or needs maintenance
- **Output**: Stability, Incident Resolution

---

## Task Naming Convention

All tasks use `SCREAMING_SNAKE_CASE`:

| User Request | Task Name |
|--------------|-----------|
| "Add user login" | `USER_LOGIN` |
| "Implement JWT authentication" | `JWT_AUTH` |
| "Dashboard analytics feature" | `DASHBOARD_ANALYTICS` |

---

## L7 Quality Gates

### L7 Spec Review Gate (Software Engineer)
Before generating any terminal prompt:
1. **Pre-Mortem**: "If this fails in production, what was the cause?"
2. **Antagonist**: "How would a malicious actor exploit this?"
3. **Complexity**: "Is this over-engineered?"

### Zero-Trust Antagonistic Review (Pre-Commit)
Before any commit instruction:
- Security Checklist (no secrets, input validation, auth checks)
- Quality Checklist (tests pass, no linter errors)
- Architecture Checklist (follows patterns, no breaking changes)

---

## Spec Templates

Contracts are located in `specs/templates/`:
- [PRODUCT_SPEC.md](specs/templates/PRODUCT_SPEC.md): Requirements contract
- [TECH_DESIGN_SPEC.md](specs/templates/TECH_DESIGN_SPEC.md): Architecture contract
- [OPS_READINESS_SPEC.md](specs/templates/OPS_READINESS_SPEC.md): Deployment contract

## Planning

Project management via `planning/`:
- [ROADMAP.md](planning/ROADMAP.md): Quarterly Goals
- [BACKLOG.md](planning/BACKLOG.md): Prioritized work
- [SPRINT_BOARD.md](planning/SPRINT_BOARD.md): Active execution

## Documentation

- **[User Guide](AGENT_KIT_USER_GUIDE.md)**: Detailed playbooks for common scenarios
