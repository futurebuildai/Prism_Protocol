# Product Spec (PRD)

> **Status**: [DRAFT | REVIEW | APPROVED]
> **Owner**: [Product Owner Name]
> **Reviewers**: [UX, Tech Lead, Research]
> **Last Updated**: [Date]

## 1. Problem Statement
*   **The "Why"**: What user problem are we solving?
*   **The Goal**: What is the business outcome? (e.g. increase conversion by 5%).
*   **Non-Goals**: What are we expressly NOT doing in this version?

## 2. User Stories & Acceptance Criteria
*   **Story 1**: As a [User], I want to [Action], so that [Benefit].
    *   **Acceptance Criteria (Gherkin)**:
        *   `GIVEN` [User is logged in]
        *   `WHEN` [User clicks X]
        *   `THEN` [System displays Y]
*   **Story 2**: ...

## 3. Functional Requirements (Granular)
### 3.1 Data Models (JSON Schema)
Define the exact data structure involved.
```json
{
  "id": "uuid",
  "status": "enum(PENDING, ACTIVE, CLOSED)",
  "created_at": "ISO8601"
}
```

### 3.2 API Interactions
*   **Inputs**: What data does the user provide? validation rules?
*   **Outputs**: What does the system return?

## 4. UX & UI Flows
*   [Link to Figma/Wireframe]
*   **Key Transitions**: Describe the flow from Screen A to Screen B.
*   **Empty States**: What does it look like with 0 items?
*   **Loading States**: Skeleton or Spinner?

## 5. Edge Cases (The "Dark Path")
*   **Network Failure**: What if the API fails?
*   **Validation Errors**: What if input is malformed?
*   **Permissions**: What if a Read-Only user tries this?
*   **Concurrency**: What if two users edit the same item?

## 6. Analytics & Observability
*   **Events to Track**: `button_clicked`, `flow_completed`.
*   **Success Metrics**: What defines success?

## 7. Security & Compliance
*   **PII**: Does this touch personal data?
*   **Access Control**: Who can see this?

---
> **L7 Reflection**:
> 1. Did I validate that this problem actually exists?
> 2. Did I define the JSON schema strictly?
> 3. Did I cover the error states, not just the happy path?
