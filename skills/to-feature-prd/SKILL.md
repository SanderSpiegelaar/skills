---
name: to-feature-prd
description: Turn one vertical slice from to-features into a slice-scoped PRD file after a short Ask User Question sanity pass; writes docs/{feature-slug}/PRD.md in the target project. Use when the user wants a per-slice PRD, feature-folder docs from a slice, or to formalize Slice k before implementation.
---

Produce a **thin, slice-scoped PRD** from **exactly one** block in a **to-features** breakdown, sanity-check assumptions with the user, then persist it under **`docs/{feature-slug}/PRD.md`** at the **workspace project root**.

For full-product PRDs and issue-tracker publication, use **to-prd**. For breaking a PRD into slices, use **to-features**.

## When to use

- After **to-features** when you want a standalone PRD for **one** slice (e.g. before **tdd** or manual implementation)
- User asks for a slice PRD, `docs/<feature>/PRD.md`, or to “document Slice k”
- **Do not** use for whole-product PRDs, Epic-only specs, or replacing **to-prd**

## Input contract

You MUST have:

1. **One slice section** matching the template in [to-features](../to-features/SKILL.md) (`### Slice k — [title]` with **Delivers**, **PRD trace**, **Depends on**, **Verify**, **TDD note**, etc.).
2. **PRD source** for the parent PRD (URL, repo path, issue link, or explicit paste/excerpt). If missing, ask once before drafting — do **not** invent scope beyond **Delivers**, **PRD trace**, and **Verify**.

If the user supplied multiple slices, stop and ask which **single** slice to document.

## Question protocol (short sanity pass)

Before drafting **PRD.md**:

1. Run **one** batched **Ask User Question** round (structured UI); use **at most two** rounds if blockers remain (e.g. unresolved scope or slug disagreement).
2. Cover what matters for **this slice only**: boundaries vs parent PRD, ambiguous acceptance, **Depends on** assumptions, **HITL** / risk, and **confirmation of the directory slug** for `docs/{feature-slug}/`.
3. This is **not** a full [grill](../grill/SKILL.md) session — no obligation to edit `CONTEXT.md` or ADRs unless the user asks.
4. If the host has no Ask User Question tool, use clearly numbered multiple-choice questions in chat (same topics).

Do **not** expand scope beyond what the slice + answers justify; use **`TBD`** where still unknown after questions.

## Slug and path rules

- **`{feature-slug}`:** lowercase **kebab-case**, ASCII only, derived from the slice title (collapse whitespace; strip punctuation).
- **Path:** `{project-root}/docs/{feature-slug}/PRD.md` — create the directory if needed.
- **Collision:** if `docs/{feature-slug}/` already exists and is for a different slice, append `-slice-{k}` (e.g. `search-autocomplete-slice-2`).
- **`PRD.md`:** use this exact filename (capital **PRD**).

## Process

1. **Ingest** the slice and PRD source; note **Type** (AFK | HITL), **Tracer bullet**, **Delivers**, **PRD trace**, **Depends on**, **TDD note**, **Verify**.
2. **Sanity pass** via Ask User Question (see above).
3. **Draft** `PRD.md` body using the template below (slice-scoped; link or cite parent PRD — do not paste the entire parent PRD).
4. **Write** the file at `docs/{feature-slug}/PRD.md`.
5. **Confirm** in chat: path written, slug chosen, and any remaining **`TBD`** items.

## Output template (contents of PRD.md)

Use this structure; adapt headings only if the project already defines a slice PRD convention.

```markdown
# [Slice k — title]

## PRD source

[Link or pointer to parent PRD]

## Slice identity

- **Slice:** k — [title]
- **PRD trace:** [from slice]
- **Type:** AFK | HITL
- **Tracer bullet:** yes | no

## Goal

- **Problem:** [slice-only, from Delivers + sanity answers]
- **Solution:** [how this slice addresses it]
- **Success:** [observable outcomes for this slice]

## Scope

### In scope

- …

### Out of scope

- [deferrals to other slices or parent PRD]

## Dependencies

- **Slices:** [Depends on — slice indices only]
- **Systems / integrations:** …

## Requirements

### Functional

- …

### Non-functional

- …

## Acceptance criteria

- [ ] … (aligned with **Verify** and PRD trace)

## Testing and verification

- **TDD note:** [from slice]
- **Verify:** [from slice — expanded if needed]

## Open questions

- … (omit section if none; keep **TBD** visible elsewhere if needed)
```

## Related skills

- **to-features** — produces slice input
- **to-implementation** — recommended next step after `PRD.md`: writes `docs/{feature-slug}/IMPLEMENTATION.md` for **to-tickets**
- **to-tickets** — after `IMPLEMENTATION.md`: writes numbered tickets under `docs/{feature-slug}/tickets/`
- **to-prd** — full PRD + tracker workflow
- **tdd** — implementation against vertical slices
