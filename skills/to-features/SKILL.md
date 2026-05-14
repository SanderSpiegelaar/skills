---
name: to-features
description: Break a PRD produced by to-prd into vertical feature slices numbered Slice 0..n in TDD-friendly implementation order (tracer bullet first, RED→GREEN increments). Use when the user wants a PRD decomposed into implementable slices, vertical slices from requirements, or an ordered breakdown before coding or ticketing.
---

# To Features

Decompose a **to-prd-shaped** PRD into **vertical slices** in **strict implementation order** for smooth **TDD** (tracer bullets, not horizontal layers). Preferred input is a parent PRD at **`docs/{initiative-slug}/PRD.md`**.

Issue tracker wiring and triage labels should already exist before optional publication — run **setup-skills** if not.

## Quick start

- **Input:** `docs/{initiative-slug}/PRD.md`.
- **Do:** Break the PRD into vertical slices in TDD order.
- **Output:** Slice 0..n list with dependencies, PRD trace, TDD notes, and verification.
- **Next:** Run **to-feature-prd** for one selected slice.

## When to use

- After **to-prd** (or equivalent) when you have a PRD body to implement
- User asks for feature breakdown, vertical slices, implementation order, or “how to sequence this for TDD”
- **Do not** use for horizontal milestones (“all DB, then all API”); use vertical slices only

## Input contract

The PRD MUST align with the template in [to-prd](../to-prd/SKILL.md) (`<prd-template>`): executive summary, user stories (numbered), acceptance criteria, technical specs, testing and validation, etc.

**Sources (best first):** `docs/{initiative-slug}/PRD.md` → published PRD issue body → pasted PRD → conversation that clearly contains those sections.

**If input is thin:** stop and ask for missing sections or mark unknowns `TBD` — do not invent scope.

## Vertical slice rules

- Each slice is a **thin vertical** cut through the stack: it is **demoable or verifiable on its own** end-to-end (behavior + tests/eval hook as the PRD defines), not a single layer
- Prefer **many thin slices** over few thick ones
- **Wrong:** finish all schema, then all services, then all UI (horizontal)
- **Right:** each slice completes one coherent path; later slices build on earlier ones

## TDD ordering rubric

Apply in order when sequencing slices:

1. **Slice 0 = tracer bullet.** Smallest end-to-end path that proves project wiring (test harness, main integration surface) and delivers **one** concrete, testable behavior from the PRD
2. **Later slices.** Each adds **one coherent capability** (or a tight group of acceptance criteria that naturally ship together), completable with **RED→GREEN** cycles without unfinished horizontal foundations
3. **Dependencies.** Use a small DAG: real blockers (shared contracts, auth, persistence shape, external integrations) come earlier — still as **vertical** increments, not layer-wide work
4. **Polish.** Defer cosmetic-only work until core behaviors exist unless the PRD marks it MVP-critical
5. **HITL / spikes.** If a slice needs a human decision or time-boxed spike before coding, label it **HITL**; otherwise **AFK** (optional but helps ordering)

Alignment: see [tdd](../tdd/SKILL.md) (vertical slices, anti-horizontal-slicing).

## Question protocol

When you need user choices on the breakdown, use the **Ask User Question** tool when available; otherwise numbered questions in chat.

If `CONTEXT.md` or `CONTEXT-MAP.md` exists, preserve the project's domain vocabulary when naming slices and acceptance traces. If slicing reveals a durable vocabulary gap, flag it for `grill` or a `CONTEXT.md` update instead of inventing synonyms.

## Process

1. **Ingest** the PRD; note numbered user stories, acceptance criteria, technical decisions, and testing/eval section
2. **Draft slices** obeying the vertical slice rules and TDD ordering rubric
3. **Number** slices in implementation order only: **Slice 0**, **Slice 1**, … (**0-based**)
4. **Dependencies** between slices use these ids only (e.g. `Depends on: Slice 0`), never issue numbers
5. **Present** output using the template below
6. **Confirm** with the user: granularity, dependency edges, tracer placement (Slice 0), and HITL/AFK labels if used
7. **Iterate** until approved. Recommended durable route: run **to-feature-prd** on one selected slice, then **to-implementation-doc**, then **to-tickets**. Fast route: hand the approved list to **to-tickets** only when there is already enough detail to write implementation tickets safely.

## Output template

Use this structure verbatim (adapt field content only):

```markdown
# Vertical feature slices (TDD order)

**PRD source:** [docs/{initiative-slug}/PRD.md / issue URL / paste note / conversation]

Order: Slice 0 Slice 1 … Slice n

### Slice 0 — [title]
- **Type:** AFK | HITL
- **Tracer bullet:** yes (must be yes for Slice 0)
- **Delivers:** [one short paragraph: end-to-end behavior]
- **PRD trace:** [user story numbers; AC or section refs]
- **Depends on:** None
- **TDD note:** [what RED→GREEN proves for this slice — behavior language, not file churn]
- **Verify:** [observable check; test level; eval/golden set if PRD §3/§5 applies]

### Slice 1 — [title]
- **Type:** AFK | HITL
- **Tracer bullet:** no
- **Delivers:** …
- **PRD trace:** …
- **Depends on:** Slice … (use slice indices only)
- **TDD note:** …
- **Verify:** …

[repeat for Slice 2 … Slice n]
```

## Example

See [references/example-prd-slices.md](references/example-prd-slices.md) for a focused slice-list example and [`references/example-intelligent-search-slices.md`](references/example-intelligent-search-slices.md) for the golden workflow example. The durable downstream route is defined in [`references/workflow-contract.md`](references/workflow-contract.md).
