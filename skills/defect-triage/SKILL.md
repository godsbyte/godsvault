---
name: defect-triage
description: Analyse failed tests, classify the cause, assess severity and priority, investigate root cause, draft reproducible defect reports, and recommend retest and closure. Use after any failed or blocked test.
---

# Defect Triage

Inputs: failed result, evidence, run log. Output: failure analysis in the run log and draft defects in `reports/<product>/defects/` per `templates/defect-report.md`.

## Procedure
1. Verify the failure evidence exists. If not, mark the result Unverified and request evidence.
2. Reproduce at least 2 more times where safe and non-destructive; log every attempt, passing ones too.
3. Classify: Product defect / Test defect / Environment issue / Data issue / Requirement ambiguity / Not reproducible (`instructions/severity-and-priority-model.md`).
4. For product defects: assign severity and priority with justification; check for duplicates in existing drafts and, if available, the ticket system (read-only).
5. Investigate root cause read-only (logs, code paths). State it as *suspected* unless proven; cite evidence.
6. Identify regression impact: related features, shared components, other tests to rerun.
7. Draft the defect with exact reproduction steps, environment/build, data, expected vs actual, evidence links.
8. Recommend retest steps and closure criteria.

## Boundaries
Never file or edit external tickets without approval. Never change application code to "fix" a defect.
