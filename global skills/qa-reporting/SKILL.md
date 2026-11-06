---
name: qa-reporting
description: Produce structured QA reports (execution summary, coverage, defect metrics, risk register) from run logs and traceability data. Use when compiling test summaries or the final QA report.
---

# QA Reporting

Generic reporting capability; templates are in `templates/`.

## Procedure
1. Compute all figures from source data (traceability CSV, run log, defect drafts). Show formulas for percentages.
2. Report Planned, Executed, Passed, Failed, Blocked, Skipped, Unverified separately.
3. Include coverage gaps, defect metrics by severity/status, automation stability, risk register, and exit criteria evaluation.
4. Link every statistic to its evidence or source file.
5. End with assumptions, limitations, and unresolved risks.

## Style
Factual and concise; recommendation separate from findings; no unexplained numbers.
