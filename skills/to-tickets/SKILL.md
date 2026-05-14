---
name: to-tickets
description: Break implementation increments into tracer-bullet vertical tickets as numbered markdown files under docs/{feature-slug}/tickets/, using a unified template. Use when the user has docs/{feature-slug}/PRD.md and preferably docs/{feature-slug}/IMPLEMENTATION.md and wants AFK-ready implementation tickets; issue-tracker publication is optional when explicitly requested.
---

# To Tickets

## Quick start

- **Input:** `docs/{feature-slug}/PRD.md` and `docs/{feature-slug}/IMPLEMENTATION.md`.
- **Do:** Approve the increment breakdown and write ordered ticket files.
- **Output:** `docs/{feature-slug}/tickets/{nn}-{slug}.md`.
- **Next:** Run **tdd** per ticket.

## Workflow

1. **Gather context.** Prefer `PRD.md + IMPLEMENTATION.md`. Read `IMPLEMENTATION.md` first for sequencing, dependencies, vertical increments, and Maps to PRD; then read `PRD.md` for scope and acceptance.
2. **Gate missing implementation docs.** If `IMPLEMENTATION.md` is missing, stop once, explain sequencing will be coarser, and proceed from `PRD.md` alone only after explicit user confirmation.
3. **Explore when useful.** Ground ticket wording in the project's domain glossary, ADRs, `AGENTS.md`, and repo layout when they provide durable anchors.
4. **Draft implementation increments.** Follow [`references/increment-ticketing-rules.md`](references/increment-ticketing-rules.md). Each ticket is a thin vertical path, not a horizontal layer-only task.
5. **Quiz the user.** Use the host's **Ask User Question** / structured question tool when available. Confirm granularity, dependencies, merges/splits, and HITL/AFK labels.
6. **Write ticket files.** Use [`references/output-conventions.md`](references/output-conventions.md) for directory, ordering, and filename rules. Use [`references/ticket-template.md`](references/ticket-template.md) for every ticket body.
7. **Publish only on request.** If the user explicitly asks, sync the same substance to the configured issue tracker in dependency order. Do not close or modify a parent issue unless asked.
8. **Confirm handoff.** Report the directory, file list, `TBD`s, and **tdd** as the next step.

## Output contract

Each ticket must stand alone and include:

- Summary with Type, Blocked by, and Conflicts / overlaps.
- Documentation references and traceability to PRD + IMPLEMENTATION.
- Approach, layers/boundaries, engineering context, risks, and verification.
- Observable acceptance criteria and granular implementation todos.

Tickets map to implementation increments from `IMPLEMENTATION.md`. Use feature-slice language only for upstream `to-features` context.

## References

- [`references/workflow-contract.md`](references/workflow-contract.md) — portable artifact hierarchy and handoff chain.
- [`references/output-conventions.md`](references/output-conventions.md) — directory, naming, ordering, and publication rules.
- [`references/increment-ticketing-rules.md`](references/increment-ticketing-rules.md) — vertical increment, conflict, and authoring guidance.
- [`references/ticket-template.md`](references/ticket-template.md) — required ticket file body.
- [`references/example-ticket.md`](references/example-ticket.md) — golden ticket example.

## Related skills

- **ticket-researcher** — optionally deepens thin tickets with current technical research.
- **tdd** — implements one ticket at a time with RED -> GREEN -> REFACTOR.
- **finish-feature** — verifies all shipped tickets and writes `IMPLEMENTED.md`.
