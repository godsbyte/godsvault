# Evidence and Quality Standards

Non-negotiable rules for every QA agent. Referenced by all agents; do not copy into agent files.

## Rules
1. Never fabricate test execution results.
2. Never report a test as Passed without execution evidence.
3. Always distinguish the states below; never merge them.
4. Attach evidence references (logs, screenshots, reports, command output) to every executed result.
5. Maintain requirement-to-test traceability (see `traceability-model.md`).
6. State missing coverage explicitly; never imply coverage that does not exist.
7. Never silently convert a failure into a pass (no retry-until-green without recording every attempt).
8. Record assumptions and environmental limitations in the run log.
9. Defects must be reproducible: exact steps, environment, data, expected vs actual, evidence.
10. List unresolved risks explicitly in every report.

## Result states
| State | Meaning | Evidence required |
|---|---|---|
| Planned | Designed, not run | None |
| Passed | Executed, actual matched expected | Yes |
| Failed | Executed, actual differed from expected | Yes |
| Blocked | Could not execute (env, data, defect) | Blocker reason |
| Skipped | Deliberately not run | Reason + approver |
| Unverified | A result was claimed but evidence is missing or invalid | Gap description |

A result without supporting evidence is **Unverified**, never Passed.

## Evidence storage
- Path: `logs/<product>/<run-id>/evidence/`; run ID format `YYYYMMDD-HHMM-<ticket-or-scope>`.
- Name files `EV-<nnn>_<TC-id>_<short-desc>.<ext>`; reference them by relative path in results.
- Evidence must show timestamp, environment/build identifier, and command or action taken.
- Never store secrets, tokens, credentials, or personal data in evidence; redact before saving.

## Test case quality checklist (supervisor review)
- Linked to a requirement and scenario.
- Has preconditions, test data, atomic steps, and a verifiable expected result.
- Covers positive, negative, boundary, and error handling where applicable.
- Independent and repeatable; includes cleanup.
- Priority and risk set; type (functional, API, etc.) set.

## Automation reliability checklist
- Reuses the product's existing framework where one exists.
- Deterministic: no fixed sleeps, no order dependence, no shared mutable state.
- Uses synthetic data and cleans up after itself.
- Passes N consecutive runs (default 3) before being declared stable; every run is logged.
- Failures are analysed (product defect, test defect, environment, data) before being reported.

## Assumptions and limitations
Every run log and report must contain an "Assumptions and limitations" section, even if empty ("None recorded").
