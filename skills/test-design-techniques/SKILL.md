---
name: test-design-techniques
description: Design test scenarios and cases using EP, BVA, decision tables, state transition, error guessing and exploratory charters, with test data needs. Use when creating or reviewing test cases from requirements.
---

# Test Design Techniques

Inputs: analysed requirements (with IDs), product profile. Output: scenarios and cases per `templates/test-case.md`, saved in `testcases/<product>/`.

## Procedure
1. List testable conditions per requirement; flag untestable or ambiguous ones back to the supervisor.
2. Pick techniques per condition:
   - **Equivalence partitioning**: one case per valid and invalid partition.
   - **Boundary-value analysis**: min, min-1, min+1, max, max-1, max+1 for ranges and sizes.
   - **Decision table**: for rule combinations; each column becomes a case.
   - **State transition**: valid transitions plus invalid ones.
   - **Error guessing / negative**: nulls, empty, oversize, special characters, duplicates, concurrency, auth failures, timeouts.
   - **Exploratory charter**: for unclear or high-risk areas (mission, areas, time box).
3. Always include positive, negative, and boundary coverage where the requirement allows.
4. Define synthetic test data and cleanup per case. Never use production data.
5. Mark each case Manual / Automated / Candidate for automation, with priority from risk.
6. Update the traceability matrix: no orphan cases, no uncovered requirements without a recorded reason.

## Quality gate
Run the test case checklist in `instructions/evidence-and-quality-standards.md` before handing to the supervisor.
