---
description: Execute the full software development lifecycle from requirements to deployment.
---

# Full Development Cycle Workflow

This workflow orchestrates the entire software development lifecycle using the specialized skills.

## Prerequisites
- Ensure the project workspace is set up.
- Have a clear, high-level description of what you want to build.

## Context Management (Avoiding Token Bloat)
After each major phase, create a summary to compress context:
1.  **After Requirements**: Summarize key decisions into the top of `PROJECT_SCOPE.txt`.
2.  **After Planning**: Note total sprints and dependencies in a `PLANNING_SUMMARY.md`.
3.  **After Each Sprint**: The `SPRINT-N-README.md` serves as the summary for subsequent sprints.

For very long projects, advise the user to **start a new Antigravity thread** for each phase, loading only the relevant artifacts.

## Model Recommendations
*   **Gemini 3 Pro / Opus 4.5**: Requirement Gathering, Product Owner Reviews.
*   **Gemini 3 Flash**: Planning, Code Generation, Testing.

## Steps

### Phase 1: Requirement Gathering
// turbo
1. Read the `skills/requirement_gathering/SKILL.md` skill instructions.
2. Follow the Requirement Gathering skill to elicit requirements from the user.
3. **Output**: `PROJECT_SCOPE.txt` should be created in the project root.
4. **Checkpoint**: Ask the user to approve the scope before proceeding.

---

### Phase 2: Project Planning
// turbo
5. Read the `skills/project_planning/SKILL.md` skill instructions.
6. Follow the Project Planning skill to break down the scope into sprints.
7. **Output**: `sprints/SPRINT-N.txt` files should be created.
8. **Checkpoint**: Inform the user of the number of sprints and ask if they want to proceed.

---

### Phase 3: Sprint Execution (Loop)
For each Sprint N (from 1 to Total Sprints):
9. Execute the `/develop-sprint` workflow with Sprint N.
10. **Checkpoint**: After the Product Owner approves, ask the user if they want to proceed to the next sprint.

---

### Phase 4: Final Delivery
11. Once all sprints are complete, consolidate the `sprints/SPRINT-N-README.md` files into a final project README.
12. Notify the user that the project is complete.
