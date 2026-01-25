---
description: Invoke the Dev Team to execute engineering work, build features, and write code.
---

1. **Validate Input**:
   - Verify `[TASKNAME]` is provided in the invocation.
   - Verify `docs/[TASKNAME]_PRD.md` exists.
   - If validation fails: "Cannot proceed. Please complete `/product` first."
2. **Invoke Skill**: Use the `view_file` tool to read `skills/devteam/SKILL.md`.
3. **Execute**: Assume the role of the **DevTeam Orchestrator** and follow the instructions in the SKILL file.
   - If no PRD exists for a large feature, **REJECT** and tell user to use `/product`.
   - If valid, create `specs/[TASKNAME]_specs.md` and start the sprint.
4. **Handoff**: Provide inter-thread transition instruction:
   > "Specs complete. Invoke `/software_engineer [TASKNAME]` to proceed."
   > "Input Artifact: `specs/[TASKNAME]_specs.md`"
