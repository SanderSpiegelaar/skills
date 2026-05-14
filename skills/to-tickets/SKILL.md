---
name: to-tickets
description: Break work into tracer-bullet vertical-slice implementation tickets as numbered markdown files under docs/{feature-slug}/tickets/, using docs/{feature-slug}/PRD.md (to-feature-prd) and docs/{feature-slug}/IMPLEMENTATION.md (to-implementation). Use when the user wants implementation tickets on disk, a slice ticket breakdown, or handoff from IMPLEMENTATION.md to executable work items. Issue-tracker publish only when the user explicitly asks.
---

# To tickets

Break approved work into **independently grabbable implementation tickets** as **numbered markdown files** under **`docs/{feature-slug}/tickets/`**, using **vertical slices** (tracer bullets).

**Happy-path inputs:** **`docs/{feature-slug}/PRD.md`** ([to-feature-prd](../to-feature-prd/SKILL.md)) and **`docs/{feature-slug}/IMPLEMENTATION.md`** ([to-implementation](../to-implementation/SKILL.md)) in the **target project root**. Same **`{feature-slug}`** (kebab-case) as those files’ directory.

**Default output:** filesystem tickets only. **Do not** publish to the issue tracker unless the **user explicitly asks**; if they do, use the repo’s tracker config and triage vocabulary (see **`docs/agents/`** — run setup skills if missing).

## Output conventions

| Item | Rule |
|------|------|
| **Directory** | `{project-root}/docs/{feature-slug}/tickets/` — create if needed |
| **Order** | Filename numeric prefix = **implementation order** (topological: blockers lower than dependents) |
| **Padding** | Use zero-padded prefixes so lexical sort matches execution order: `01-…`, `02-…`; use `001-` if there may be more than 99 tickets |
| **Filename** | `{nn}-{short-kebab-title}.md` — ASCII, lowercase; derive slug from slice title (collapse whitespace, strip punctuation) |
| **Collisions** | If two slices would share the same slug, append `-2`, `-b`, etc. |

## Process

### 1. Gather context

Work from conversation context or paths the user supplies.

**Slice workflow (preferred):**

1. Resolve **`docs/{feature-slug}/PRD.md`** and **`docs/{feature-slug}/IMPLEMENTATION.md`**.
2. **Reading order:** **`IMPLEMENTATION.md` first** — sequencing, dependencies, proposed vertical increments and **Maps to PRD**; then **`PRD.md`** — scope, requirements, acceptance criteria.

**If `IMPLEMENTATION.md` is missing:** do **not** silently substitute. **Stop once**, explain that sequencing will be coarser, and proceed from **`PRD.md` alone only after explicit user confirmation** (they may prefer running **to-implementation** first).

**Other sources:** If the user passes an issue reference (number, URL, or path), fetch and read it when breaking down from tracker context instead of slice docs.

### 2. Explore the codebase (optional)

If you have not already explored the codebase, do so to ground ticket wording in the project’s domain glossary and ADRs.

### 3. Draft vertical slices

Break the work into **tracer bullet** tickets. Each ticket is a thin vertical slice through **all** integration layers end-to-end, **not** a horizontal layer-only task.

Slices may be **HITL** or **AFK**. HITL slices need human interaction (decision, review). AFK slices can be implemented without human context. Prefer AFK where possible.

<vertical-slice-rules>
- Each slice delivers a narrow but COMPLETE path through every layer (schema, API, UI, tests)
- A completed slice is demoable or verifiable on its own
- Prefer many thin slices over few thick ones
</vertical-slice-rules>

### 4. Quiz the user

Present the proposed breakdown as a numbered list. For each slice, show:

- **Title**: short descriptive name
- **Type**: HITL / AFK
- **Blocked by**: which other slices (if any) must complete first
- **User stories covered**: which user stories this addresses (if the source material has them)

Ask the user:

- Does the granularity feel right? (too coarse / too fine)
- Are the dependency relationships correct?
- Should any slices be merged or split further?
- Are the correct slices marked as HITL and AFK?

Iterate until the user approves the breakdown.

### 5. Write ticket files

For **each approved slice**, write one file under **`docs/{feature-slug}/tickets/`** using the numeric prefix and naming rules above. Assign **sequential order** consistent with dependencies (blockers get smaller numbers).

Use the ticket body template below. Each file should stand alone for an AFK agent without requiring the issue tracker.

### 6. Publish to the issue tracker (optional)

**Only when the user explicitly requests tracker publication.**

For each slice, create an issue using the same substance as the markdown ticket (you may paste or adapt the body). Publish in dependency order so **Blocked by** can reference real issue IDs when helpful. Apply the correct triage label for AFK-ready work unless instructed otherwise.

Do **not** close or modify a parent tracker issue unless the user asks.

<ticket-file-template>
# [Ticket title — same as slice title]

## Context

- **Feature docs:** `docs/{feature-slug}/PRD.md`, `docs/{feature-slug}/IMPLEMENTATION.md`
- **Type:** HITL | AFK

## Traceability

- **IMPLEMENTATION.md increment:** #… (row index from **Proposed work breakdown**, if applicable)
- **PRD:** requirement / AC references this slice satisfies (e.g. AC bullets, requirement IDs)

## What to build

A concise description of this vertical slice. Describe the end-to-end behavior, not layer-by-layer implementation.

Avoid specific file paths or code snippets — they go stale fast. Exception: if a prototype produced a snippet that encodes a decision more precisely than prose can (state machine, reducer, schema, type shape), inline it here and note briefly that it came from a prototype. Trim to the decision-rich parts — not a working demo, just the important bits.

## Acceptance criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Blocked by

- **`NN-other-slug.md`** (this repo’s ticket file) or **None — can start immediately**

</ticket-file-template>

Confirm in chat: directory written, file list with paths, and any **`TBD`** carried from source docs.
