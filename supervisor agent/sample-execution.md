# Sample End-to-End Execution (illustrative walkthrough)

> Fictional walkthrough showing the *flow and artifacts*. All product names, IDs, and values are placeholders. It contains no real results and must not be used as evidence for anything.

**Request**: "Test ticket `ACME-123` (password reset) for product *Acme Portal*. App URL: `<qa-url>`. Repo: `<path>`."

| # | Actor | Action | Artifact |
|---|---|---|---|
| 1 | Supervisor | No profile found → asks for environments, confirms repo access is read-only; discovers stack from the repo; drafts profile | `products/acme-portal.md` (user confirms) |
| 2 | Supervisor | `ticket-intake` | `ticket/acme-portal/ACME-123.md`; questions: token lifetime? lockout rule? |
| 3 | Supervisor | Asks the user the two questions; records the answers as requirements | `REQ-ACME-001..004` |
| 4 | Analyst | Risk assessment and strategy | `reports/acme-portal/<run-id>/strategy.md` |
| 5 | Human | **G1** approve; recorded | `approvals.md` |
| 6 | Analyst | Cases with BVA on token expiry, negative cases, decision table for lockout | `testcases/acme-portal/ACME-123.md`, matrix with Planned rows |
| 7 | Supervisor | Review: finds REQ-ACME-004 uncovered → sends back; Analyst adds cases | updated cases |
| 8 | Human | **G2** approve | `approvals.md` |
| 9 | Supervisor | Execution list: 12 cases (8 manual, 4 automated), QA env, synthetic users, cleanup | list in run log |
| 10 | Human | **G3** approve | `approvals.md` |
| 11 | Manual Exec + Automation | Execute in parallel; save outputs | run log, `evidence/EV-*` |
| 12 | Supervisor | Evidence validation: one "Passed" has no artifact → downgraded to Unverified; executor re-runs | corrected log |
| 13 | Defect Triage | One failure reproduced 3/3 → product defect S2/P2 | `reports/acme-portal/defects/DEF-ACME-001.md` (draft) |
| 14 | Human | Approves filing the draft; creates or authorises the Jira ticket | approval recorded |
| 15 | Supervisor | Retest after fix, targeted regression; recompute matrix; readiness: **Ready with risks** | `qa-execution-report.md`, `traceability-matrix.csv` |
| 16 | Human | **G4** accept; makes the release decision | `approvals.md` |

Key behaviours demonstrated: clarification before planning, gate stops, coverage-gap rework, evidence-based downgrade to Unverified, defect drafted not filed, recommendation vs human decision.
