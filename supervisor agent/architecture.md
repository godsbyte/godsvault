# Architecture and Operating Model

## Overview
A supervisor-led multi-agent QA system on GitHub Copilot custom agents. The **Senior QA Supervisor** coordinates four specialists through a gated lifecycle. The system is product-agnostic: product facts live in `products/<product>.md`, discovered read-only from application repos.

## Folder map
| Folder | Contents |
|---|---|
| `.github/agents/` | The 5 agent definitions (the format Copilot loads) |
| `supervisor agent/` | This documentation: architecture, matrix, workflow, sample |
| `sub-agents/` | Pointer to specialist definitions in `.github/agents/` (see its README) |
| `instructions/` | Shared standards referenced by all agents |
| `skills/` | QA-project-specific reusable procedures |
| `global skills/` | Generic, cross-project capabilities |
| `templates/` | Standard artifact templates |
| `products/` | One profile per product under test |
| `ticket/` | Normalised intake records, `ticket/<product>/<key>.md` |
| `testcases/` | Scenarios, test cases, `automation/<product>/` scripts |
| `reports/` | Strategies, QA reports, matrices, draft defects |
| `logs/` | Run logs, approvals, evidence: `logs/<product>/<run-id>/` |

## Design principles
1. Evidence over assertion: no Passed without evidence (`instructions/evidence-and-quality-standards.md`).
2. Controlled autonomy: four gates plus action-level approvals (`instructions/governance-and-approvals.md`).
3. Single source of truth: shared rules live once in `instructions/`; agents reference them.
4. Least privilege: each agent writes only to its folders.
5. Traceability end to end (`instructions/traceability-model.md`).
6. Specialist capabilities (API, DB, performance, security, AI) are skills until workload justifies separate agents.

## Lifecycle to agent mapping
| Step | Owner | Gate |
|---|---|---|
| Intake, analysis, clarification | Supervisor (+ Analyst) | |
| Risk, scope, strategy | Analyst → Supervisor review | G1 |
| Scenarios and test cases | Analyst → Supervisor review | G2 |
| Execution list, environments, data | Supervisor | G3 |
| Manual / automated execution | Manual Execution / Automation Engineer | |
| Evidence validation | Supervisor | |
| Failure analysis, defects | Defect Triage Analyst | |
| Retest, regression | Supervisor → executors | |
| Exit criteria, QA report | Supervisor | G4 |

## Extending
Add a new specialist agent only when a responsibility has a distinct operational boundary and volume (for example a dedicated performance agent once a product requires continuous load testing). Changes to shared standards need human approval.
