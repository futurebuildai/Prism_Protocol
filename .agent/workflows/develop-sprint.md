---
description: Execute a single development sprint (Dev -> Test -> Review loop).
---

# Develop Sprint Workflow

This workflow executes a single sprint through the development, testing, and review cycle.

## Input
- **Sprint Number**: The sprint to execute (e.g., 1, 2, 3...).

## Steps

### Step 1: Read Sprint Requirements
// turbo
1. Read `sprints/SPRINT-<N>.txt` to understand the goals for this sprint.
2. If Sprint N > 1, also read `sprints/SPRINT-<N-1>-README.md` to understand prior progress.

---

### Step 2: Software Development
// turbo
3. Read `skills/software_engineer/SKILL.md` for instructions.
4. Develop the code as per the sprint requirements.
5. Create `test_app.sh` and execute it to validate the code.
6. **Output**: Code files created, `test_app.sh` passes.

---

### Step 3: Software Testing
// turbo
7. Read `skills/software_tester/SKILL.md` for instructions.
8. Create comprehensive test cases in `app_test.sh`.
9. Execute the test suite.
10. **Output**: Test results (SUCCESS/FAILURE for each test).

---

### Step 4: Product Owner Review
// turbo
11. Read `skills/product_owner/SKILL.md` for instructions.
12. Review the sprint output against requirements.
13. **Decision**:
    - If `APPROVED`: Create `sprints/SPRINT-<N>-README.md` and proceed.
    - If `REJECTED`: Return to Step 2 with the feedback.

---

### Step 5: Completion
14. Inform the user that Sprint N is complete.
15. Return control to the `full-development-cycle` workflow.
