# Implementation outline template

Use this structure for `docs/{feature-slug}/IMPLEMENTATION.md`.

```markdown
# Implementation outline — [Slice title from PRD]

## PRD reference

- **Path:** `docs/{feature-slug}/PRD.md`
- **Slice identity:** (from PRD — index, title, type, tracer bullet if any)

## Goal and constraints

[3–6 sentences: problem, approach, success. Call out HITL gates and AFK assumptions from the PRD where relevant.]

## Scope alignment

### In scope

[Echo PRD; no new scope.]

### Out of scope

[Echo PRD deferrals.]

## Proposed work breakdown (for ticketing)

Numbered vertical increments:

| # | Title | User-visible outcome | Layers touched (one line) | Depends on | Maps to PRD |
|---|--------|----------------------|---------------------------|------------|-------------|
| 0 | … | … | e.g. schema, API, UI, tests | None / #n | AC: … |

[Alternatively use a bullet list with the same fields per increment if tables are awkward.]

## Integration and touchpoints

[Concise list: systems, boundaries, auth, data ownership, external APIs.]

[Optional: small Mermaid diagram only if it disambiguates a flow.]

## Risks, unknowns, and spikes

- … (TBD where needed; flag HITL.)

## Verification strategy

[How increments tie to Verify, TDD note, and testing/validation from the PRD.]

## Handoff

Use to-tickets with PRD.md and this IMPLEMENTATION.md together. It writes numbered tickets under docs/{feature-slug}/tickets/.
```
