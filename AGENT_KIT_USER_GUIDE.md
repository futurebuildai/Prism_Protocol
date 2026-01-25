# Antigravity Prism Protocol: User Guide

This guide explains how to use the **Antigravity Prism Protocol** to achieve L7-quality results using the hybrid workflow between **Antigravity** (Claude.ai) and **Claude Code** (terminal).

---

## The Inter-Thread Protocol

Every task flows through three threads with explicit handoffs:

```
┌─────────────────────────────────────────────────────────────────────────┐
│  /product                                                                │
│  ─────────                                                              │
│  Input: User request (idea, problem, goal)                              │
│  Output: docs/[TASKNAME]_PRD.md                                         │
│  Handoff: "Invoke /devteam [TASKNAME] to proceed."                      │
└─────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│  /devteam [TASKNAME]                                                    │
│  ───────────────────                                                    │
│  Input: docs/[TASKNAME]_PRD.md                                          │
│  Output: specs/[TASKNAME]_specs.md                                      │
│  Handoff: "Invoke /software_engineer [TASKNAME] to proceed."            │
└─────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│  /software_engineer [TASKNAME]                                          │
│  ─────────────────────────────                                          │
│  Input: specs/[TASKNAME]_specs.md                                       │
│  L7 Gate: Pre-Mortem, Antagonist, Complexity                           │
│  Output: TERMINAL PROMPT with Zero-Trust Review                         │
│  Handoff: "Paste into Claude Code terminal."                            │
└─────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────┐
│  Claude Code (Terminal)                                                  │
│  ──────────────────────                                                 │
│  Execute: claude -p "[TERMINAL PROMPT]"                                 │
│  Output: Code changes, test results                                     │
│  Return: Paste output back to Antigravity for Audit                     │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Setup

### Prerequisites

1. **Antigravity Account**: Access to Claude.ai with Projects enabled
2. **Claude Code CLI**: Install via `npm install -g @anthropic-ai/claude-code`
3. **Authentication**: Run `claude login` in your terminal

### Project Configuration

1. Add this repository to an Antigravity Project
2. Ensure the `.agent/workflows/` directory is accessible
3. Create a `CLAUDE.md` in your project root for Claude Code context

---

## Scenario 1: New Feature (Complete Flow)

**Goal**: Add JWT authentication to the API

### Step 1: Product Phase

In Antigravity:
```
/product Add JWT authentication for the API
```

**Agent Response:**
1. Establishes task name: `JWT_AUTH`
2. Confirms: "This task will be tracked as `JWT_AUTH`. Confirm to proceed."
3. Outputs Implementation Plan
4. Creates `docs/JWT_AUTH_PRD.md`
5. Handoff: "Invoke `/devteam JWT_AUTH` to proceed."

### Step 2: DevTeam Phase

In Antigravity:
```
/devteam JWT_AUTH
```

**Agent Response:**
1. Validates `docs/JWT_AUTH_PRD.md` exists
2. Assigns Architect and Security Engineer
3. Creates `specs/JWT_AUTH_specs.md`
4. Handoff: "Invoke `/software_engineer JWT_AUTH` to proceed."

### Step 3: Software Engineer Phase

In Antigravity:
```
/software_engineer JWT_AUTH
```

**Agent Response:**
1. Runs L7 Spec Review Gate:
   - Pre-Mortem: Checks for failure scenarios
   - Antagonist: Checks for security vulnerabilities
   - Complexity: Validates simplicity
2. Generates TERMINAL PROMPT with:
   - Objective and constraints
   - Implementation steps
   - L7 recursive audit instructions
   - Verification commands
   - Zero-Trust pre-commit checklist

### Step 4: Execute in Terminal

Copy the TERMINAL PROMPT and run:
```bash
claude -p "## Task: JWT_AUTH - Implement JWT middleware

### Objective
Implement JWT authentication middleware for the API...

### L7 Recursive Audit Instructions
For EACH sub-task, you MUST:
1. Pre-Mortem: Before writing code, ask 'What could cause this to fail?'
2. Antagonist: Before committing, ask 'How could this be exploited?'
3. Complexity: After implementation, ask 'Is this the simplest solution?'

### Zero-Trust Antagonistic Review (Pre-Commit Gate)
STOP. Before committing, verify:
- [ ] No secrets in code
- [ ] All inputs validated
..."
```

### Step 5: Audit Phase

Paste the terminal output back into Antigravity:
```
[Paste terminal output here]
```

**Agent Response:**
- QA validates test results against acceptance criteria
- Security reviews changes
- On Pass: Updates ROADMAP.md, generates HANDOFF.md
- On Fail: Generates Correction Prompt

### Step 6: Finalize

```
/NEXT
```

Commits state and moves to next step.

---

## Scenario 2: Bug Fix (Expedited Flow)

**Goal**: Fix checkout page crash on mobile

### Quick Path (Ops → Dev)

```
/ops Users reporting checkout crash on mobile
```

Agent creates `ADHOC_JWT_AUTH_SPEC.md` with repro steps, then:

```
/devteam CHECKOUT_CRASH_FIX
```

Continue with normal flow from DevTeam phase.

---

## Scenario 3: Greenfield Project

**Goal**: Build a new crypto trading bot from scratch

### Phase 1: Vision
```
/product Design a crypto trading bot MVP
```

Creates `ROADMAP.md` and `docs/CRYPTO_BOT_PRD.md`

### Phase 2: Architecture
```
/devteam CRYPTO_BOT
```

Creates `specs/CRYPTO_BOT_specs.md` with architecture, stack selection, C4 diagrams

### Phase 3: Bootstrap
```
/software_engineer CRYPTO_BOT
```

Generates scaffolding TERMINAL PROMPT

---

## L7 Quality Gates Reference

### L7 Spec Review Gate (Before Prompt Generation)

| Check | Question | Action |
|-------|----------|--------|
| Pre-Mortem | "If this fails in production, what was the cause?" | Document failure scenarios as constraints |
| Antagonist | "How would a malicious actor exploit this?" | Add security verification steps |
| Complexity | "Is this over-engineered?" | Flag for simplification |

### Zero-Trust Antagonistic Review (Before Commit)

**Security Checklist:**
- [ ] No secrets or credentials in code
- [ ] No hardcoded URLs/IPs
- [ ] All user inputs validated
- [ ] Auth/authz checks present
- [ ] Error messages don't leak info

**Quality Checklist:**
- [ ] All tests pass
- [ ] No linter errors
- [ ] No TODO/FIXME on critical paths

**Architecture Checklist:**
- [ ] Follows codebase patterns
- [ ] No circular dependencies
- [ ] No breaking API changes

---

## Best Practices

### 1. Always Start with /product
Even for "simple" tasks, establish the task name and PRD first. This ensures:
- Consistent artifact naming
- Proper handoff chain
- L7 audit trail

### 2. Trust the Handoffs
When an agent says "Invoke `/devteam [TASKNAME]`", do exactly that. Don't skip phases or the validation will fail.

### 3. Use the Task Name Consistently
The `[TASKNAME]` (e.g., `JWT_AUTH`) is your tracking ID. Use it in:
- All thread invocations
- Commit messages
- Documentation references

### 4. Don't Skip the Zero-Trust Review
Before any commit, the checklist exists for a reason. If you find yourself wanting to skip it, that's a signal something is wrong.

### 5. Paste Full Terminal Output
When returning to Antigravity for the Audit phase, paste the complete terminal output. The QA and Security agents need full context.

---

## Command Reference

| Command | Description | Input Required |
|---------|-------------|----------------|
| `/product [description]` | Start new task, create PRD | Task description |
| `/devteam [TASKNAME]` | Create technical specs | Task name from /product |
| `/software_engineer [TASKNAME]` | Generate terminal prompt | Task name from /devteam |
| `/ops [description]` | Handle incidents, bugs | Issue description |
| `/NEXT` | Finalize and proceed | After successful audit |
| `/kit` | Meta-engineering, workflows | Workflow description |

---

## Troubleshooting

### "Cannot proceed. Required input not found."

The artifact from the previous phase doesn't exist. Go back to the previous phase:
- Missing PRD → Run `/product` first
- Missing specs → Run `/devteam [TASKNAME]` first

### "Task name not provided"

Include the `[TASKNAME]` in your command:
- Wrong: `/devteam`
- Right: `/devteam JWT_AUTH`

### Claude Code Not Executing

1. Verify Claude Code is installed: `claude --version`
2. Verify authentication: `claude login`
3. Try interactive mode: `claude` (without `-p`)

### L7 Gate Failure

If the Software Engineer returns a FAIL status:
1. Note the specific gaps identified
2. Return to `/devteam [TASKNAME]` to address them
3. Re-run `/software_engineer [TASKNAME]`
