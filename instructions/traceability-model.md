# Traceability Model

Chain: **Requirement → Scenario → Test Case → Execution → Evidence → Defect → Release Assessment**

## Identifiers
`<PROD>` = short product code from `products/<product>.md`.

| Artifact | ID format | Location |
|---|---|---|
| Requirement | `REQ-<PROD>-001` (or source ticket key, e.g. Jira key, recorded alongside) | Source ticket / `ticket/` |
| Scenario | `SCN-<PROD>-001` | `testcases/<product>/` |
| Test case | `TC-<PROD>-001` | `testcases/<product>/` |
| Execution | `EX-<run-id>-<TC-id>` | `logs/<product>/<run-id>/` |
| Evidence | `EV-001` per run | `logs/<product>/<run-id>/evidence/` |
| Defect | `DEF-<PROD>-001` (until a Jira/GitHub key exists) | `reports/<product>/defects/` |

IDs are never reused. Retired items are marked `Retired`, not deleted.

## Traceability matrix
CSV at `reports/<product>/<run-id>/traceability-matrix.csv` (template: `templates/traceability-matrix.csv`).
Columns: `requirement_id, requirement_source, scenario_id, test_case_id, type, priority, execution_id, result, evidence_refs, defect_ids, notes`

Rules:
- Every requirement has at least one scenario, or an explicit "No coverage" row with reason.
- Every test case traces to at least one requirement (no orphan tests).
- Every Failed result links to a defect (draft or filed) or a documented non-defect reason.
- Every Passed result lists evidence references; otherwise it is Unverified.
- The supervisor recomputes coverage from the matrix; it does not trust agent-reported totals.

## Coverage metrics
- Requirement coverage = requirements with ≥1 executed test / total in-scope requirements.
- Execution coverage = Executed / Planned.
- Report Passed, Failed, Blocked, Skipped, Unverified counts separately.
