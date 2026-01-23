# Antigravity Prism: The Autonomous Software Org

Welcome to **Antigravity Prism**. This repository is structured as a **Google L7-Quality Autonomous Organization**. It is not just a collection of code; it is a system of "Brains", "Contracts", and "Planning" that allows AI Agents to function as a mature engineering team.

## 🧠 The Three Brains (Entry Points)
Instead of one generic assistant, this project has three specialized departments. **Always start your request with one of these skills:**

### 1. 🚀 Product Team (`product`)
*   **Mission**: Discovery, Strategy, Definition.
*   **Use when**: You have an idea, a problem, or a business goal.
*   **Trigger**: "Use the Product skill to define [Feature X]."
*   **Output**: A finalized [PRD](specs/templates/PRODUCT_SPEC.md).

### 2. 🛠️ Dev Team (`devteam`)
*   **Mission**: Execution, Engineering, Delivery.
*   **Use when**: You have a Spec/PRD and want code.
*   **Trigger**: "Use the DevTeam skill to build [Feature from PRD]."
*   **Output**: Shipped, tested Code.

### 3. 🛡️ Ops Team (`ops`)
*   **Mission**: Reliability, Security, Support.
*   **Use when**: something is broken, slow, or needs maintenance.
*   **Trigger**: "Use the Ops skill to handle [Incident/Alert]."
*   **Output**: Stability.

### 4. 🧰 Kit Expert (`/kit`)
*   **Mission**: Meta-Engineering, Workflows, Methodology.
*   **Use when**: You want to automate a repetitive task or improve the system itself.
*   **Trigger**: "Use the Kit Expert to create a [Deploy Workflow]."
*   **Output**: New Workflows (`.md`), Improved Specs.

---

## 📜 The Spec Kit (Contracts)
We believe in **"Specs as Code"**. Agents communicate via rigorous contracts located in `specs/templates/`.
*   [PRODUCT_SPEC.md](specs/templates/PRODUCT_SPEC.md): The requirements contract.
*   [TECH_DESIGN_SPEC.md](specs/templates/TECH_DESIGN_SPEC.md): The architecture contract.
*   [OPS_READINESS_SPEC.md](specs/templates/OPS_READINESS_SPEC.md): The deployment contract.

## 📅 Planning (Project Management)
We manage time on a multi-month scale using `planning/`.
*   [ROADMAP.md](planning/ROADMAP.md): Quarterly Goals.
*   [BACKLOG.md](planning/BACKLOG.md): Prioritized work.
*   [SPRINT_BOARD.md](planning/SPRINT_BOARD.md): Active 2-week execution.

## 📚 Documentation
*   **[User Guide / Playbook](AGENT_KIT_USER_GUIDE.md)**: Detailed instructions for common scenarios (Greenfield, Bug Fixes, etc).
