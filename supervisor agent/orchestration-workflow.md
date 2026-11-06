# Delegation and Orchestration Workflow

```
User request
   │
   ▼
[Supervisor] onboard product (if no profile) → intake → analyse → clarify
   │
   ▼
[Analyst] strategy ──► [Supervisor review] ──► G1 (human)
   │
   ▼
[Analyst] scenarios + cases ──► [Supervisor review] ──► G2 (human)
   │
   ▼
[Supervisor] execution list, environments, data ──► G3 (human)
   │
   ├──► [Manual Exec] manual cases ─┐
   └──► [Automation]  automated    ─┴─► run log + evidence
   │
   ▼
[Supervisor] evidence validation ── insufficient ──► back to executor
   │
   ▼ failures
[Defect Triage] classify, reproduce, draft defects ──► [Supervisor review]
   │                                      └──► approved drafts: human files tickets
   ▼
retest / regression (via executors) ─► exit criteria ─► QA report ──► G4 (human)
```

## Delegation contract (supervisor → agent)
Every delegation includes: product + profile path; run ID; scope/task; input file paths; required output files and format; constraints and approvals in force; deadline/priority if any.

## Return contract (agent → supervisor)
Artifact paths; summary; result-state counts (where applicable); assumptions; open questions; evidence index; gaps.

## Sequencing and parallelism
- Sequential: strategy → cases → execution list → execution → triage.
- Parallel when independent: manual and automated execution; defect drafts for independent failures.

## Rework loop
The supervisor rejects an output when it fails a quality check, naming the specific gap. The same agent corrects it. After two failed rounds, the supervisor escalates to the human.

## Run folder layout
```
logs/<product>/<run-id>/run-log.md
logs/<product>/<run-id>/approvals.md
logs/<product>/<run-id>/evidence/EV-001_TC-<PROD>-001_<desc>.<ext>
reports/<product>/<run-id>/{strategy.md, traceability-matrix.csv, qa-execution-report.md}
```

## Using the agents
Start Copilot CLI in this repo, select the agent with `/agent` (choose `senior-qa-supervisor`), and give: product, app URL, repo, ticket number, environment.
