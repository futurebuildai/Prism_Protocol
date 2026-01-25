---
description: The Atomic Step Loop (Hybrid) for the Prism Protocol with Inter-Thread Protocol.
---

# Prism Protocol Workflow

## Task Naming Convention

All tasks MUST have a `[TASKNAME]` identifier established in the Product phase.
- **Format**: `SCREAMING_SNAKE_CASE`
- **Examples**: `JWT_AUTH`, `USER_DASHBOARD`, `PAYMENT_INTEGRATION`
- The task name propagates through ALL artifacts and thread transitions.

## Inter-Thread Protocol (Handoff Chain)

```
/product → docs/[TASKNAME]_PRD.md → /devteam → specs/[TASKNAME]_specs.md → /software_engineer → TERMINAL PROMPT
```

---

## The Prism Atomic Step Loop (Hybrid)

### 1. Initiate (The Product Thread)

- **Trigger**: User invokes `/product` with a task request.
- **First Action**: Establish `[TASKNAME]` from user's request.
- **Product Owner Action**: Defines acceptance criteria.
- **Output**: `docs/[TASKNAME]_PRD.md`
- **Thread Transition**:
  > "PRD complete. To proceed with technical design, invoke `/devteam [TASKNAME]`."
  > "Input Artifact: `docs/[TASKNAME]_PRD.md`"

### 2. Prepare (The DevTeam Thread)

- **Trigger**: User invokes `/devteam [TASKNAME]` with PRD reference.
- **Input Validation**: Verify `docs/[TASKNAME]_PRD.md` exists.
- **Architect Action**: Reviews specs and defines technical constraints.
- **Output**: `specs/[TASKNAME]_specs.md`
- **Thread Transition**:
  > "Specs complete. To generate implementation prompts, invoke `/software_engineer [TASKNAME]`."
  > "Input Artifact: `specs/[TASKNAME]_specs.md`"

### 3. Execute (The Software Engineer Thread)

- **Trigger**: User invokes `/software_engineer [TASKNAME]`.
- **Input Validation**: Verify `specs/[TASKNAME]_specs.md` exists.
- **L7 Spec Review Gate**: MANDATORY before context generation.
- **Output**: **TERMINAL PROMPT** with L7 recursive audit instructions.
- **Zero-Trust Gate**: MANDATORY before commit/push instructions.
- **USER ACTION REQUIRED**: "Paste this into your terminal to execute."

### 4. Audit (The QA & Security Engineer)

- **Trigger**: User pastes the terminal output back into Antigravity.
- **QA Action**: Verifies test output matches acceptance criteria.
- **Security Action**: Reviews changes for vulnerabilities.
- **Zero-Trust Antagonistic Review**: MANDATORY before approval.
- **Outcome**:
  - *Pass*: Agent updates `ROADMAP.md` and generates `HANDOFF.md`.
  - *Fail*: Agent generates a "Correction Prompt" for Claude Code.

### 5. Finalize

- User triggers `/NEXT` to commit state and move to the next logical step.
