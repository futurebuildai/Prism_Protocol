# Ops Readiness Spec

> **Status**: [DRAFT | REVIEW | READY]
> **Owner**: [Dev Team Lead]
> **Approver**: [Ops/SRE Lead]

## 1. Rollout Strategy
*   **Type**: [Canary | Blue/Green | Feature Flag | Big Bang]
*   **Phases**:
    *   Phase 1: 1% Traffic (Staff Only)
    *   Phase 2: 10% Traffic
    *   Phase 3: 100% Traffic

## 2. Rollback Plan (The "Undo" Button)
*   **Trigger**: What metric tells us to rollback? (e.g. Error Rate > 1%).
*   **Procedure**:
    1.  `git revert ...`
    2.  `db rollback` (Is it safe? If not, forward-fix only?)
*   **Data integrity**: Does rollback corrupt data?

## 3. Observability & Monitoring
*   **Key Metrics**:
    *   Latency (P95, P99)
    *   Error Rate (HTTP 5xx)
    *   Saturation (CPU/Memory)
*   **Dashboards**: Link to Grafana board.
*   **Alerts**: Who gets paged? Thresholds?

## 4. Capacity Planning
*   **Expected Load**: RPS (Requests Per Second).
*   **Impact**: Will this double the database size?
*   **Quotas**: Do we need to increase AWS limits?

## 5. Runbook (SOP)
*   "If [Alert X] fires, do [Action Y]."
*   **Troubleshooting**: Common failure modes and fixes.

## 6. Compliance & Security Check
*   [ ] No secrets in environment variables (use Secret Manager).
*   [ ] PII is masked in logs.
*   [ ] Backup strategy verified.

---
> **L7 Reflection**:
> 1. If this breaks at 3AM, can the On-Call person fix it without waking me up?
> 2. Is the rollback plan tested?
> 3. Did we blow the error budget?
