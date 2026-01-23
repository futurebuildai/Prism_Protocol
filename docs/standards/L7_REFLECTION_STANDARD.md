# L7 Recursive Reflection Standard

## Purpose
This document defines the **mandatory self-reflection loop** that every agent must perform before considering a task complete. This separates "Worker" output from "Senior Staff (L7)" output.

## The Loop
Before returning `SUCCESS` or submitting work, you must pause and execute the following 3 steps:

### 1. The Pre-Mortem ("How will this fail?")
Imagine it is 6 months from now and this solution has caused a critical outage or failure.
*   **Question**: What was the root cause?
*   **Action**: Mitigate that cause *now*.
*   *Example*: "The database migration locked the users table for 20 minutes." -> *Fix*: "Use `CONCURRENTLY` index creation."

### 2. The Antagonist ("Break your own work")
Assume the role of a hostile QA engineer or hacker.
*   **Question**: How can I bypass the security? How can I crash the app with bad input?
*   **Action**: Add guards/tests for these edge cases.
*   *Example*: "I will pass a 1GB JSON payload." -> *Fix*: "Add input size limit middleware."

### 3. The Complexity Budget ("Is it too clever?")
Review your solution for over-engineering.
*   **Question**: Can this be done with 50% less code? Did I introduce a new tool/library when the standard lib would suffice?
*   **Action**: Refactor for simplicity. (YAGNI).
*   *Example*: "I added a message queue for a simple async email." -> *Fix*: "Use a background worker or cron for now."

## Checklist for Approval
- [ ] **Security**: No secrets in code, inputs validated, auth checked.
- [ ] **Observability**: Metric/Log emitted for success AND failure paths.
- [ ] **Rollback**: Is there a plan if this goes wrong?
- [ ] **Docs**: "Why" is documented, not just "How".
