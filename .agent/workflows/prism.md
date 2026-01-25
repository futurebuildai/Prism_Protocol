---
description: The Atomic Step Loop (Hybrid) for the Prism Protocol.
---

# Prism Protocol Workflow

## The Prism Atomic Step Loop (Hybrid)

1. **Initiate (The Architect & Product Owner)**
   - **Trigger**: User requests a task via `/devteam` or roadmap step.
   - **Architect Action**: Reviews `SPECS` and defines the technical design/constraints.
   - **Product Owner Action**: Defines the acceptance criteria.

2. **Prepare (The Software Engineer)**
   - **Action**: Consumes the Architect's design.
   - **Output**: Generates a **Context Prompt** (not code).
   - **Context Prompt Includes**:
     - The Goal (e.g., "Implement JWT Auth").
     - The Constraints (from Specs).
     - The Acceptance Criteria (Test requirements).
     - **USER ACTION REQUIRED**: "Paste this into your terminal to execute."

3. **Execute (External Executor)**
   - **Trigger**: User pastes the **Context Prompt** into the terminal.
   - **Command**: `claude "[Context Prompt]"`
   - **Agent Action (Claude)**: Edits files, runs tests, fixes bugs, and verifies strict compilation.

4. **Audit (The QA & Security Engineer)**
   - **Trigger**: User pastes the terminal output back into Antigravity.
   - **QA Action**: Verifies the test output matches the acceptance criteria.
   - **Security Action**: Reviews the changes for vulnerabilities.
   - **Outcome**: 
     - *Pass*: Agent updates `ROADMAP.md` and generates `HANDOFF.md`.
     - *Fail*: Agent generates a "Correction Prompt" for Claude Code.

5. **Finalize**
   - User triggers `/NEXT` to commit state and move to the next logical step.
