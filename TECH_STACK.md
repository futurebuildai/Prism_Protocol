# Technical Stack & Design Guardrails

All autonomous agents must strictly adhere to these technology choices and design principles. Deviations are not permitted without explicit user override.

## 1. Backend & API Layer
*   **Language**: **Go (Golang)** (Latest Stable)
*   **Architecture**: Modular, service-oriented.
*   **API Style**: RESTful or gRPC (depending on performance needs).
*   **Principles**: Strong typing, explicit error handling, concurrency-safe.

## 2. Frontend Web App
*   **Framework**: **Framework-Free / Native Web Components** focus.
*   **Core**: **TypeScript** + **Vite**.
*   **Components**: **Lit** (for lightweight, standard Web Components).
*   **Constraint**: Maximize use of platform standards; minimize heavy framework abstractions.
*   **Design**: Mobile-responsive first.

## 3. Mobile / Edge Native App
*   **Framework**: **Flutter**.
*   **Architecture**: Highly modular, feature-based split.
*   **Focus**: Maintainability and clean separation of UI and business logic.

## 4. AI & Orchestration
*   **Provider**: **Google Cloud Vertex AI / Gemini** (Primary).
*   **Extensibility**: Architecture must allow switching providers via configuration (Adapter pattern), but defaults to Google.

## 5. Design & Documentation Standards
*   **Modularity**: Code must be loosely coupled and highly cohesive.
*   **Documentation**:
    *   **Layman-Accessible**: READMEs and high-level docs must be understandable by non-engineers.
    *   **In-Code**: Godoc for Go, TSDoc for TypeScript.
    *   **Architectural**: key design patterns must be explicitly documented (e.g., ADJs, ADRs).
*   **Patterns**: strict adherence to established patterns (Repository, Factory, Observer) where appropriate.

## 6. Scale & Reliability Standards
**THIS IS NOT AN MVP. All code must be production-grade.**

*   **Scale Target**: 100,000 concurrent users, 10,000 organizations.
*   **Performance**:
    *   API P99 latency < 200ms.
    *   Database queries must be indexed. No N+1 queries.
    *   Connection pooling required (Go: `pgxpool`).
*   **Reliability**:
    *   Health check endpoints (`/healthz`, `/readyz`).
    *   Graceful shutdown handling (`SIGTERM`).
    *   Retry logic for transient failures (exponential backoff).
*   **Logging & Observability**:
    *   Structured JSON logging (Go: `slog`).
    *   OpenTelemetry tracing for distributed calls.
    *   Prometheus metrics for key operations.
*   **Security**:
    *   All user inputs validated (never trust the client).
    *   Role-Based Access Control (RBAC) enforced.
    *   No secrets in code; use environment variables or secret managers.
*   **Data Integrity**:
    *   Database migrations versioned (e.g., `golang-migrate`).
    *   Soft deletes preferred over hard deletes.

## Enforcement
*   **Software Engineers** must generate code matching these specs.
*   **Code Reviewers / Product Owners** must **REJECT** any PR using prohibited frameworks (e.g., React, Node.js backend, Python backend).
