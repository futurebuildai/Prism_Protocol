---
description: Invoke the Product Team to define requirements, strategy, and specs.
---

1. **Analyze Request**: Read the user's input to understand the idea or business goal.
2. **Establish Task Name**: Extract `[TASKNAME]` from the request (SCREAMING_SNAKE_CASE).
   - Example: "Add user authentication" → `USER_AUTH`
3. **Invoke Skill**: Use the `view_file` tool to read `skills/product/SKILL.md`.
4. **Execute**: Assume the role of the **Product Orchestrator** and follow the instructions in the SKILL file.
   - Create/Update `planning/ROADMAP.md` if strategic.
   - Create `docs/[TASKNAME]_PRD.md` for feature requests.
5. **Handoff**: Provide inter-thread transition instruction:
   > "PRD complete. Invoke `/devteam [TASKNAME]` to proceed."
   > "Input Artifact: `docs/[TASKNAME]_PRD.md`"
