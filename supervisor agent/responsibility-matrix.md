# Agent Responsibility Matrix

R = responsible, A = accountable/approves, C = consulted, I = informed. Human = the user/QA owner.

| Activity | Supervisor | Analyst | Manual Exec | Automation | Defect Triage | Human |
|---|---|---|---|---|---|---|
| Product onboarding / profile | R | C | | C | | A |
| Ticket intake | R | C | | | | I |
| Requirement analysis | A | R | | | | C |
| Risk and scope | A | R | | | | A (G1) |
| Test strategy | A | R | | | | A (G1) |
| Test case design | A | R | | C | | A (G2) |
| Execution planning | R | C | | C | | A (G3) |
| Manual execution and evidence | A | | R | | | I |
| Automation build and run | A | C | | R | | A (G3; changes to app/CI) |
| Evidence validation | R | | C | C | | I |
| Failure analysis and defect drafts | A | | | C | R | I |
| Filing external tickets | | | | | R (draft) | A |
| Regression selection | R | C | | C | C | A (G3) |
| Exit criteria / readiness recommendation | R | | | | C | I |
| Final QA report | R | | | | | A (G4) |
| Release / deployment decision | C | | | | | R, A |
| Changes to shared standards | C | | | | | R, A |

## Permissions
See the least-privilege table in `instructions/governance-and-approvals.md`.
