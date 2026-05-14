---
name: to-implementation-doc
description: After to-feature-prd, produce a high-level IMPLEMENTATION.md next to docs/{feature-slug}/PRD.md for ticket breakdown with to-tickets. Use when the user wants an implementation bridge doc, slice-scoped technical sequencing, or handoff from slice PRD to issues.
---

# To Implementation Doc

## Quick start

- **Input:** `docs/{feature-slug}/PRD.md`.
- **Do:** Map the slice PRD into vertical implementation increments.
- **Output:** `docs/{feature-slug}/IMPLEMENTATION.md`.
- **Next:** Run **to-tickets**.

## Workflow

1. **Ingest the slice PRD.** Extract slice identity, type, dependencies, requirements, acceptance criteria, Verify, and TDD note.
2. **Check readiness.** Goal, Scope, Requirements, and Acceptance criteria should not be mostly empty or `TBD`. If they are, stop once and ask for minimum missing detail.
3. **Read context lightly.** Optionally skim repo layout, `AGENTS.md`, `CONTEXT.md` / `CONTEXT-MAP.md`, and relevant ADRs for vocabulary and boundaries. Do not add scope beyond the PRD.
4. **Ask only when blocked.** If dependencies or slice boundaries are ambiguous, run at most one batched **Ask User Question** round; otherwise proceed.
5. **Draft vertical increments.** Use [`references/increment-rules.md`](references/increment-rules.md) and [`references/implementation-template.md`](references/implementation-template.md).
6. **Write the file.** Persist `docs/{feature-slug}/IMPLEMENTATION.md` next to `PRD.md`.
7. **Confirm handoff.** Report the path, remaining `TBD`s, and **to-tickets** as the next step.

## Output contract

`IMPLEMENTATION.md` must be high level and ticket-oriented:

- PRD reference and slice identity.
- Goal, constraints, and scope alignment.
- Proposed vertical increments mapped to PRD acceptance criteria.
- Integration touchpoints, risks, unknowns, verification strategy, and handoff.

Do not write production code. Use brief pseudocode only when it locks a decision needed for ticketing.

## References

- [`references/implementation-template.md`](references/implementation-template.md) — canonical implementation outline.
- [`references/increment-rules.md`](references/increment-rules.md) — vertical-increment and handoff rules.

## Related skills

- **to-feature-prd** — produces the slice PRD.
- **to-tickets** — consumes `PRD.md + IMPLEMENTATION.md` and writes tickets.
- **finish-feature** — writes `IMPLEMENTED.md` after implementation.
- **to-features** — produces the earlier slice list.
- **tdd** — implements tickets RED -> GREEN.
