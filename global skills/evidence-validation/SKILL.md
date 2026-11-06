---
name: evidence-validation
description: Validate that execution results are backed by genuine, sufficient evidence and assign result states accordingly. Use when reviewing any executed test result or agent output.
---

# Evidence Validation

Generic and reusable across projects. Project rules: `instructions/evidence-and-quality-standards.md`.

## Procedure
For each claimed result:
1. Does an evidence artifact exist at the referenced path? (check the file)
2. Does it show the action/command, the output, a timestamp, and the build/environment?
3. Does the actual outcome in the evidence support the claimed result?
4. Is the result consistent with the run log and the traceability matrix?
5. Are there signs of selective reporting (reruns without logged failures, truncated output)?

## Verdicts
- **Valid**: evidence supports the result.
- **Insufficient**: set result to Unverified and request specific evidence.
- **Contradictory**: set to Failed or Unverified and escalate to the supervisor.

Never accept a summary statement in place of an artifact.
