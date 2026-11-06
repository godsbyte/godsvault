# Severity and Priority Model

Severity = technical impact. Priority = urgency of fix. Assess both and justify each.

## Severity
| Level | Definition |
|---|---|
| S1 Critical | Outage, data loss/corruption, security breach, core flow impossible with no workaround |
| S2 Major | Major function broken or seriously degraded; workaround is difficult |
| S3 Moderate | Function impaired; reasonable workaround exists |
| S4 Minor | Cosmetic, wording, or low-impact issue |

## Priority
| Level | Definition |
|---|---|
| P1 | Fix immediately; blocks release or testing |
| P2 | Fix in the current release |
| P3 | Fix when scheduled |
| P4 | Backlog |

## Test case risk/priority
Test case priority derives from risk = likelihood × impact (High / Medium / Low). Regression and smoke selection use it (see `skills/regression-impact-selection`).

## Defect classification
Each failed test is classified before reporting: Product defect, Test defect, Environment issue, Data issue, Requirement ambiguity, or Not reproducible. Only Product defects and confirmed requirement gaps become defect tickets; others are recorded in the run log.

## Release exit criteria defaults (override per product in `products/<product>.md`)
- 100% of P1 test cases executed; no open S1/S2 defects.
- ≥95% of planned in-scope test cases executed, none Unverified without waiver.
- No unresolved High risks without an approved mitigation or waiver.
The supervisor recommends; a human makes the release decision.
