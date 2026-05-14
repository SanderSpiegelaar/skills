---
name: to-feature-prd
description: Turn one vertical slice from to-features into a slice-scoped PRD file after a short Ask User Question sanity pass; writes docs/{feature-slug}/PRD.md in the target project. Use when the user wants a per-slice PRD, feature-folder docs from a slice, or to formalize Slice k before implementation.
---

# To Feature PRD

## Quick start

- **Input:** One slice from **to-features** plus parent PRD source.
- **Do:** Run a short sanity pass and write the slice-scoped PRD.
- **Output:** `docs/{feature-slug}/PRD.md`.
- **Next:** Run **to-implementation-doc**.

## Workflow

1. **Require one slice.** The slice must match the [to-features](../to-features/SKILL.md) output shape: title, Type, Tracer bullet, Delivers, PRD trace, Depends on, TDD note, and Verify. If multiple slices are supplied, ask which single slice to document.
2. **Require PRD source.** Prefer `docs/{initiative-slug}/PRD.md`; otherwise accept URL, repo path, issue link, paste, or excerpt. If missing, ask once before drafting.
3. **Run a short sanity pass.** Use one batched **Ask User Question** round; use at most two rounds if blockers remain. Cover slice boundaries, ambiguous acceptance, dependency assumptions, HITL risk, and directory slug.
4. **Preserve domain vocabulary.** If `CONTEXT.md` / `CONTEXT-MAP.md` exists, use existing terms. This is not a full [grill](../grill/SKILL.md) session unless the user asks.
5. **Resolve `{feature-slug}`.** Follow [`references/path-rules.md`](references/path-rules.md).
6. **Draft and write.** Use [`references/slice-prd-template.md`](references/slice-prd-template.md), link or cite the parent PRD, and write `docs/{feature-slug}/PRD.md`.
7. **Confirm handoff.** Report the path, chosen slug, remaining `TBD`s, and **to-implementation-doc** as the next step.

## Output contract

The slice PRD must stay slice-scoped and include:

- Parent PRD source.
- Slice identity, type, PRD trace, and tracer-bullet status.
- Goal, scope, dependencies, requirements, acceptance criteria, testing/verification, and open questions.

Do not expand scope beyond the selected slice plus user answers. Use `TBD` where still unknown after questions.

## References

- [`../../docs/skill-system/workflow.md`](../../docs/skill-system/workflow.md) — canonical artifact hierarchy and handoff chain.
- [`references/slice-prd-template.md`](references/slice-prd-template.md) — canonical `PRD.md` body.
- [`references/path-rules.md`](references/path-rules.md) — slug, collision, and path rules.
- [`../../docs/skill-system/examples/intelligent-search/slice-prd.md`](../../docs/skill-system/examples/intelligent-search/slice-prd.md) — golden slice PRD example.

## Related skills

- **to-features** — produces the selected slice input.
- **to-implementation-doc** — recommended next step after `PRD.md`.
- **to-tickets** — consumes `IMPLEMENTATION.md` to write numbered tickets.
- **to-prd** — writes the parent PRD at `docs/{initiative-slug}/PRD.md`.
- **tdd** — implements tickets against observable behavior.
