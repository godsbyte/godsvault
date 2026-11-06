# Governance and Approvals

Semi-autonomous operation: agents act freely within approved scope and stop for human approval at defined gates.

The presence of a tool or permission is **not** authorization. Only an explicit, recorded human approval is.

## Allowed without extra approval (within an approved product and scope)
- Read requirements, tickets, documentation, and application source (read-only).
- Generate strategies, scenarios, test cases, automation scripts (in this QA repo only).
- Execute approved, non-destructive tests in approved non-production environments.
- Analyse logs and results; draft defects and reports in this QA repo.

## Requires explicit human approval
| Action | Gate |
|---|---|
| Destructive or potentially disruptive testing | Per action |
| Any production access or testing | Per action |
| Changes to application source code | Per change |
| Changes to CI/CD pipelines | Per change |
| Database modifications | Per change |
| Creating or modifying external tickets (Jira/GitHub) | Per ticket |
| Deployment and release decisions | Per decision |
| Security tests that could affect availability (load, fuzzing, DoS-like) | Per test |
| Changes to shared QA standards (`instructions/`, `templates/`, `global skills/`) | Per change |
| Opening a PR against an application repo | Per PR |
| Using credentials not defined in the product profile | Per use |

## Mandatory workflow gates
| Gate | After | Approver action |
|---|---|---|
| G1 | Test strategy and scope | Approve / revise |
| G2 | Test scenarios and test cases | Approve / revise |
| G3 | Before any execution (environment, data, tests list) | Approve / revise |
| G4 | Final QA report | Accept / request more evidence |

The supervisor must stop and wait at each gate. Silence is not approval.

## Approval record
Every approval (and rejection) is appended to `logs/<product>/<run-id>/approvals.md`:
`timestamp | gate or action | scope | approver (as stated by the user) | decision | conditions`

## Agent permission model (least privilege)
| Agent | May write | May execute | Never without approval |
|---|---|---|---|
| Senior QA Supervisor | QA repo files | Read-only commands | Anything in the approval table |
| Test Analyst & Designer | `testcases/`, `reports/`, `products/` | None | Standards changes |
| Manual Execution & Evidence | `logs/` | Approved manual-support commands | Prod access, data changes |
| Automation Engineer | `testcases/automation/` | Approved test runners (non-prod) | App repo/CI changes, PRs |
| Defect & Triage Analyst | `reports/<product>/defects/` | Read-only diagnostics | Creating external tickets |

## Escalation
Agents escalate to the supervisor, and the supervisor escalates to the human, when: requirements are ambiguous or conflicting; evidence is missing or contradictory; an action would require approval; an environment is unreachable or looks like production; a secret or personal data is discovered in material under test.
