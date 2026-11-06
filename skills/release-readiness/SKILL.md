---
name: release-readiness
description: Evaluate exit criteria, open defects, coverage, and risks to produce a release readiness recommendation. Use when preparing the final QA assessment.
---

# Release Readiness Assessment

## Procedure
1. Recompute metrics from `traceability-matrix.csv` and run logs; do not trust reported totals.
2. Evaluate each exit criterion (defaults plus product overrides) as Met / Not met / Unverified, with evidence references.
3. Review open defects by severity, unresolved risks, blocked and skipped tests, and Unverified results.
4. Check coverage gaps: requirements with no executed tests.
5. Decide the recommendation:
   - **Ready**: all criteria met, no unresolved High risks.
   - **Ready with risks**: criteria met or waived with documented risks.
   - **Not ready**: any criterion unmet without waiver, or critical evidence missing.
6. List conditions, waivers needed (human decision), and recommended follow-ups.

## Rule
This is a recommendation only. Release and deployment decisions are human decisions (`instructions/governance-and-approvals.md`).
