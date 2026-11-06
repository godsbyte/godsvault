---
name: regression-impact-selection
description: Select smoke and regression test scope using change impact and risk, and plan retest of fixed defects. Use when a build, fix, or change set needs regression coverage.
---

# Regression and Impact-Based Selection

## Procedure
1. Identify the change set: ticket(s), commits/PR diffs (read-only), fixed defects, config or dependency updates.
2. Map changed components to features, APIs, data flows, and integrations (use code and docs; mark guesses as assumptions).
3. Build scope in tiers:
   - **Smoke**: minimal critical-path checks to decide whether deeper testing is worthwhile.
   - **Targeted regression**: tests tracing to impacted requirements, plus tests linked to recently fixed defects.
   - **Broad regression**: all P1 and High-risk cases when the change is wide or shared components changed.
4. Add retests for every defect awaiting verification (same steps as the original reproduction).
5. Record what was excluded and the risk of excluding it.
6. Present the selected list with rationale for approval at gate G3.

## Output
A scope table: TC ID, tier, reason selected, last result, automation status.
