# fbstudio Agent Spec Kit (Antigravity Edition)

This repository contains an **Enterprise-Grade Agentic Software Development Team** configuration for Antigravity. It is designed to autonomously plan, build, test, and deploy software with **"Top 1% FAANG" quality standards**.

## Structure

*   **`.agent/workflows/`**: Orchestration logic.
    *   `full-development-cycle.md`: The end-to-end pipeline (Requirements -> Plan -> Code -> Deploy).
    *   `develop-sprint.md`: The iterative development loop.
*   **`skills/`**: The specialized agent personas.
    *   **Requirement Gathering**: Principal PM focused on NFRs.
    *   **Project Planning**: TPM focused on architecture & critical paths.
    *   **Software Engineer**: Staff Engineer (L6) who writes Design Docs & Defensive Go/Lit code.
    *   **Software Tester**: SDET Architect who builds Rigorous Test Matrices.
    *   **Product Owner**: The "Bar Raiser" who rejects sub-par work.
    *   **Policy Enforcer**: Safety guardrail.
*   **`TECH_STACK.md`**: The source of truth for the mandatory tech stack (Go, Lit/TS, Flutter, Google AI).

## Design Philosophy
1.  **Staff-Level Quality**: Agents must write design docs before code.
2.  **Defensive Coding**: Zero tolerance for ignored errors or assumptions.
3.  **Strict Guardrails**: Frameworks are mandated; deviations are rejected.

## Usage
In Antigravity, simply say:
> "Run the full development cycle to build [Your Idea]"

