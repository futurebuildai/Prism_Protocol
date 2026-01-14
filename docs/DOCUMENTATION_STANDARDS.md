# Documentation Standards

All code produced by the Antigravity Agent Spec Kit must be **Docs-First**. Documentation is a mandatory deliverable, not an afterthought.

---

## 1. In-Code Documentation

### Go (Godoc)
Every exported function, type, and constant MUST have a comment.
```go
// CalculateTotal computes the final order total including tax.
// It returns an error if the cart is empty.
func CalculateTotal(cart *Cart, taxRate float64) (float64, error) { ... }
```

### TypeScript (TSDoc)
Every exported function and class MUST have a TSDoc comment.
```typescript
/**
 * Creates a new user session.
 * @param userId - The unique identifier for the user.
 * @returns A SessionToken object.
 * @throws {AuthError} If the user is not found.
 */
export function createSession(userId: string): SessionToken { ... }
```

---

## 2. Module READMEs

Every new package or module MUST have a `README.md` at its root containing:
1.  **Purpose**: What does this module do?
2.  **Usage**: How do I use it? (Code example)
3.  **Dependencies**: What does it rely on?

---

## 3. API Specification (OpenAPI 3.0+)

All REST API endpoints MUST be documented in an OpenAPI spec file (`openapi.yaml` or `openapi.json`).
*   **Location**: `api/openapi.yaml`
*   **Requirement**: Any new endpoint must have a corresponding entry before the PR is merged.

---

## 4. Design Documents

Before writing any significant code, the engineer MUST produce a "Design & Trade-offs" document. See `skills/software_engineer/SKILL.md` for the required sections.

---

## 5. Sprint READMEs

At the end of each sprint, the Product Owner MUST create a `sprints/SPRINT-N-README.md` summarizing:
*   What was built
*   How to use it
*   Testing strategy
*   Deployment notes

---

## Enforcement

| Layer | Enforced By | Rejection Criteria |
| :--- | :--- | :--- |
| In-Code | Linter (`golangci-lint`, `eslint`) | Missing doc comments |
| Module READMEs | Product Owner | Missing `README.md` in new modules |
| API Spec | Product Owner | API changes without OpenAPI diff |
| Design Docs | Product Owner | Coding without a design doc |
