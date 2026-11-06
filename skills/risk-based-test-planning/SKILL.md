---
name: risk-based-test-planning
description: Analyse requirements for ambiguity, assess risk, define scope and priorities, and draft a test strategy. Use at the start of any testing request before test case design.
---

# Risk-Based Test Planning

Output: strategy per `templates/test-strategy.md` in `reports/<product>/<run-id>/strategy.md`.

## Procedure
1. Gather inputs: tickets, requirements, docs, and relevant source (read-only). Record each source.
2. Extract requirements with IDs (see `instructions/traceability-model.md`). Capture acceptance criteria verbatim.
3. Find ambiguities: vague terms, missing error handling, undefined limits, conflicts, missing non-functional criteria. List as questions; do not assume answers silently.
4. Assess risk per requirement/area: likelihood (complexity, change size, history, dependencies) × impact (users, data, security, money, compliance). Rate High/Medium/Low.
5. Define scope: in, out, and why. Choose test types and manual/automated split guided by risk and product profile.
6. Set entry/exit criteria (defaults in `instructions/severity-and-priority-model.md`).
7. List every action in the plan needing approval per `instructions/governance-and-approvals.md`.
8. Record assumptions and limitations.

## Output rules
Unknowns stay explicit as `UNKNOWN`. The strategy is a draft until the human approves at gate G1.
