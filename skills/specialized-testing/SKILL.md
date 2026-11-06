---
name: specialized-testing
description: Guidance for API, database, performance, security, compatibility, infrastructure, and AI/LLM-agent testing, including safety limits and approval triggers. Use when a product profile includes these test types.
---

# Specialized Testing

Apply only the types listed in the product profile. Tooling comes from the product's existing stack; propose, never impose.

| Type | Focus | Safety / approval |
|---|---|---|
| API | Contract, status codes, validation, auth, idempotency, error bodies, pagination | Non-prod only; avoid mutating shared data |
| Database | Schema/constraint checks, data integrity, migration effects | Read-only queries by default; **any write needs approval** |
| Performance | Baselines, load/stress, latency percentiles | **Load tests need approval** (availability risk); define limits first |
| Security | AuthN/AuthZ, input validation, secrets exposure, dependency risk | **Active scanning/fuzzing needs approval**; never exploit beyond proof |
| Compatibility | Browsers, OS, versions | Matrix from profile |
| Infrastructure | Deployment config, probes, scaling, resilience | Non-prod only; **disruptive actions need approval** |
| AI / LLM / agent | Output quality, hallucination, prompt injection, guardrails, PII leakage, tool-use correctness, determinism and regression sets | Use synthetic prompts and data; record model/version and parameters as evidence |

## Rules
- Each case still follows the standard template, traceability, and evidence rules.
- Non-deterministic results (LLM): define acceptance criteria (rubric/thresholds), run multiple samples, log all outputs.
- Anything outside the approved scope is escalated to the supervisor.
