---
name: ticket-intake
description: Normalise testing input from Jira tickets, GitHub issues, requirements, or pasted/exported content into a structured intake record. Use when a new testing request arrives.
---

# Ticket Intake

Generic across projects. Intake records are saved in `ticket/<product>/<ticket-key>.md`.

## Procedure
1. Identify the source type and key. GitHub issues: read with `gh` (read-only). Jira: use an available Jira tool if one is configured; otherwise ask the user to paste or export the ticket into `ticket/`.
2. Extract: title, description, acceptance criteria, priority, linked issues/PRs, attachments, comments with decisions, and build/version info.
3. Record the source link and retrieval timestamp.
4. Flag missing or ambiguous information as questions; do not invent acceptance criteria.
5. Never create or edit external tickets here; that needs approval.

## Output
```
# <KEY> — <title>
Source | Retrieved | Product | Type
## Description
## Acceptance criteria (verbatim)
## Linked items
## Open questions
```
