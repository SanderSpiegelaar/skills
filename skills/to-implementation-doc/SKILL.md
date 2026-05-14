---
name: to-implementation-doc
description: After to-feature-prd, produce a high-level IMPLEMENTATION.md next to docs/{feature-slug}/PRD.md for ticket breakdown with to-tickets. Use when the user wants an implementation bridge doc, slice-scoped technical sequencing, or handoff from slice PRD to issues.
---

Turn a **slice-scoped PRD** from **[to-feature-prd](../to-feature-prd/SKILL.md)** into a **high-level, ticket-oriented** implementation document. The output seeds **[to-tickets](../to-tickets/SKILL.md)** with vertical increments, dependencies, and traceability—**not** a full low-level design spec.

**Note:** Do **not** write production code unless **pseudocode** is needed to lock a decision.

## When to use

- Immediately after **`docs/{feature-slug}/PRD.md`** exists (from **to-feature-prd**)
- User asks for an implementation outline, technical sequencing, or “what to ticket next” for one slice
- Before **to-tickets** when you want dependency hints and PRD-to-work mapping in one place

**Do not** use for: whole-product or epic-wide plans without a slice PRD, replacing **to-feature-prd**, or writing implementation ticket files (use **to-tickets**).

## Input contract

You MUST have:

1. **`docs/{feature-slug}/PRD.md`** — path in the target project or full pasted body. Use the **same** `{feature-slug}` as in that file’s directory.
2. Enough substance to proceed: **Goal**, **Scope**, **Requirements**, and **Acceptance criteria** should not be mostly empty or **`TBD`**. If they are, **stop once** and ask for the minimum missing detail (mirror **to-feature-prd** discipline).

Optional: shallow read of the codebase or `AGENTS.md` for domain terms and ADRs—only if it improves ticket vocabulary without expanding scope.

## Output path

Write:

`{project-root}/docs/{feature-slug}/IMPLEMENTATION.md`

Use the exact filename **`IMPLEMENTATION.md`** (capital **I**), co-located with **`PRD.md`**.

If the project’s documentation standard requires a second copy elsewhere (e.g. legacy planning trees), mirror only when **`AGENTS.md`** or team conventions explicitly require it; **default** is the co-located path above.

## Process

1. **Ingest** `PRD.md`: slice identity, type (AFK | HITL), dependencies, requirements, acceptance criteria, **Verify** / TDD note.
2. **Optional:** skim repo layout and ADRs for naming and boundaries—do not add scope beyond the PRD.
3. If **Depends on** or slice boundaries are ambiguous, run **at most one** batched **Ask User Question** round (or numbered multiple-choice in chat). **Not** a full [grill](../grill/SKILL.md).
4. **Draft** `IMPLEMENTATION.md` using the template below (adapt headings only if the project defines a local convention).
5. **Write** the file at `docs/{feature-slug}/IMPLEMENTATION.md`.
6. **Confirm** in chat: path written, and any remaining **`TBD`** items.

## Output template (contents of IMPLEMENTATION.md)

Use this structure; keep it **high level** and **oriented toward tracer-bullet vertical slices** for **to-tickets**.

```markdown
# Implementation outline — [Slice title from PRD]

## PRD reference

- **Path:** `docs/{feature-slug}/PRD.md`
- **Slice identity:** (from PRD — index, title, type, tracer bullet if any)

## Goal and constraints

[3–6 sentences: problem, approach, success. Call out **HITL** gates and **AFK** assumptions from the PRD where relevant.]

## Scope alignment

### In scope

[Echo PRD; no new scope.]

### Out of scope

[Echo PRD deferrals.]

## Proposed work breakdown (for ticketing)

Numbered **vertical increments** (tracer-first mindset). Each item:

| # | Title | User-visible outcome | Layers touched (one line) | Depends on | Maps to PRD |
|---|--------|----------------------|---------------------------|------------|-------------|
| 0 | … | … | e.g. schema, API, UI, tests | None / #n | AC: … |

[Alternatively use a bullet list with the same fields per increment if tables are awkward.]

Rules:

- Prefer **many thin** vertical cuts over one thick milestone.
- **Increment 0** should be the smallest end-to-end path that proves wiring and one testable behavior (tracer bullet), when the PRD implies it.
- Each row must map to **acceptance criteria** or requirements in `PRD.md`.

## Integration and touchpoints

[Concise list: systems, boundaries, auth, data ownership, external APIs.]

[Optional: small Mermaid diagram **only** if it disambiguates a flow—not required for every doc.]

## Risks, unknowns, and spikes

- … (**TBD** where needed; flag **HITL**.)

## Verification strategy

[How increments tie to **Verify**, **TDD note**, and testing/validation from the PRD—not a full test matrix.]

## Handoff

Use the **to-tickets** skill with **`PRD.md`** and this **`IMPLEMENTATION.md`** together. It writes numbered markdown tickets under **`docs/{feature-slug}/tickets/`** (default deliverable). Publishing to the issue tracker is **optional** and only when the user asks. Each ticket must be a **tracer-bullet vertical slice** (end-to-end, demoable or verifiable), not horizontal layer-only work. After tickets are merged, **[finish-feature](../finish-feature/SKILL.md)** can write **`docs/{feature-slug}/IMPLEMENTED.md`** (verified as-built handoff).
```

## Related skills

- **to-feature-prd** — produces **`PRD.md`**
- **to-tickets** — consumes **`PRD.md` + `IMPLEMENTATION.md`** (preferred); writes **`docs/{feature-slug}/tickets/*.md`** by default
- **finish-feature** — after implementation; writes **`docs/{feature-slug}/IMPLEMENTED.md`**
- **to-features** — slice list before `PRD.md`
- **tdd** — RED→GREEN against a slice

## Context template

- **`docs/{feature-slug}/PRD.md`:** [path or pasted body]
