# Agent Kit User Guide: Playbooks for the Autonomous Org

This guide explains how to drive the **FutureBuild Studio** organization to achieve L7-quality results in various scenarios.

---

## 🟢 Scenario 1: Greenfield Project (Start from Scratch)
**Goal**: Build a new product (e.g., "A Crypto Trading Bot") from zero.

1.  **Vision (Product)**:
    *   Command: *"Use the **Product** skill to discover and plan a new Crypto Trading Bot."*
    *   *Result*: Agent creates `planning/ROADMAP.md` and a high-level `PRODUCT_SPEC.md` for the MVP.
2.  **Architecture (Dev)**:
    *   Command: *"Use the **DevTeam** skill to create the Architecture for the Crypto Bot MVP based on the PRD."*
    *   *Result*: Agent (Architect) creates `TECH_DESIGN_SPEC.md` (C4 diagrams, Stack selection).
3.  **Bootstrapping (Dev)**:
    *   Command: *"Use the **DevTeam** skill to scaffold the repo."*
    *   *Result*: `npx create-app`, folder structure, CI/CD setup.

---

## ✨ Scenario 2: New Feature (The "Happy Path")
**Goal**: Add "Social Login" to the existing app.

1.  **Spec (Product)**:
    *   Command: *"Use the **Product** skill. I want to add Google/GitHub login. Create a Spec."*
    *   *Result*: Agent updates `BACKLOG.md` and generates `specs/templates/PRODUCT_SPEC.md` (Auth flows, DB changes).
2.  **Plan (Dev)**:
    *   Command: *"Use the **DevTeam** skill. Plan the implementation of Social Login from the Backlog."*
    *   *Result*: Agent creates `TECH_DESIGN_SPEC.md` (OAuth flow, Security Threat Model).
3.  **Build (Dev)**:
    *   Command: *"Use the **DevTeam** skill. Execute the Social Login spec."*
    *   *Result*: Code is written, tests are passed, `SPRINT_BOARD.md` is updated.

---

## 🐛 Scenario 3: Bug Fixing (Reactive)
**Goal**: "The checkout page is crashing on mobile."

1.  **Triage (Ops)**:
    *   Command: *"Use the **Ops** skill. Users are reporting crashes on checkout mobile."*
    *   *Result*: `Support Engineer` tries to reproduce. Creates an `ADHOC_Request_SPEC.md` with repro steps.
2.  **Fix (Dev)**:
    *   Command: *"Use the **DevTeam** skill to fix the checkout crash bug (See AdHoc Spec)."*
    *   *Result*: Engineer fixes bug, adds regression test. Code Reviewer verifies.

---

## 🔒 Scenario 4: Security Hardening (Proactive)
**Goal**: Ensure we are safe for enterprise users.

1.  **Audit (Ops)**:
    *   Command: *"Use the **Ops** skill. Run a Security Audit on the auth module."*
    *   *Result*: `Security Engineer` runs simple audit/simulations. Produces a Report.
2.  **Harden (Ops/Dev)**:
    *   Command: *"Use the **Ops** skill to patch the vulnerabilities found."*
    *   *Result*: Secrets rotated, dependencies updated, headers fixed.

---

## 🔌 Scenario 5: Third-Party Integration
**Goal**: Integrate "Stripe" for payments.

1.  **Feasibility (Product/Research)**:
    *   Command: *"Use the **Product** skill. Investigate Stripe integration feasibility."*
    *   *Result*: `Research Engineer` prototypes. `Integration Engineer` checks API docs.
2.  **Bridge Building (Dev)**:
    *   Command: *"Use the **DevTeam** skill. Implement the Stripe wrapper."*
    *   *Result*: `Integration Engineer` builds the Anti-Corruption Layer (Adapter) so core code doesn't depend on Stripe explicitly.

---

## 🧠 Best Practices for the User (You)
1.  **Trust the Contracts**: Don't skip the Spec. If you tell DevTeam to "just build it" without a Spec, they will REJECT it (L7 standard).
2.  **Use the Planning Layer**: If you have 5 tasks, put them in the `BACKLOG.md` first. Don't spam commands.
3.  **Respect the Handoff**: Let Product finish the PRD before waking up the Developers.
