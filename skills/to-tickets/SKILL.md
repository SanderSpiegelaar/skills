---
name: to-tickets
description: Break work into tracer-bullet vertical-slice implementation tickets as numbered markdown files under docs/{feature-slug}/tickets/, using a unified template (documentation references, implementation details, acceptance criteria, implementation todos). Inputs docs/{feature-slug}/PRD.md (to-feature-prd) and docs/{feature-slug}/IMPLEMENTATION.md (to-implementation). Issue-tracker publish only when the user explicitly asks.
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

Every ticket **MUST** use the unified **`<ticket-file-template>`** below—same headings and section purposes—so files stay consistent for humans and AFK agents. Each file should stand alone without requiring the issue tracker.

### 6. Publish to the issue tracker (optional)

**Only when the user explicitly requests tracker publication.**

For each slice, create an issue using the same substance as the markdown ticket (you may paste or adapt the body). Publish in dependency order so **Blocked by** can reference real issue IDs when helpful. Apply the correct triage label for AFK-ready work unless instructed otherwise.

Do **not** close or modify a parent tracker issue unless the user asks.

**Author notes for filling the template:**

- Populate **Documentation references** from **`IMPLEMENTATION.md`** and **`PRD.md`** first; add **`CONTEXT.md`**, **`docs/adr/…`**, **`AGENTS.md`** only when exploration surfaced durable anchors (repo-relative paths).
- Use **Implementation details** for stable boundaries (packages, modules, test areas); avoid brittle line-level paths unless they encode a real constraint.
- **Acceptance criteria** are the observable definition of done—align with PRD acceptance criteria. **Implementation todos** are granular `- [ ]` execution steps; do not paste AC verbatim unless it helps as a milestone checkpoint.
- Order **Implementation todos** roughly by dependency within the slice (mirror **TDD** posture when the PRD or repo conventions expect tests alongside behavior).
- After the quiz is approved, tailor todos to this repo’s layout so an AFK agent can execute without rereading the entire PRD.

<ticket-file-template>
# [Ticket title — same as slice title]

## Summary

- **Type:** HITL | AFK
- **Blocked by:** **`NN-other-slug.md`** (peer ticket in this directory) or **None — can start immediately**

## Documentation references

- **Slice PRD:** `docs/{feature-slug}/PRD.md`
- **Implementation outline:** `docs/{feature-slug}/IMPLEMENTATION.md`
- **Traceability:**
  - **IMPLEMENTATION.md increment:** #… (row index from **Proposed work breakdown**, if applicable)
  - **PRD:** requirement / acceptance-criteria references this slice satisfies (e.g. AC bullets, requirement IDs)
- **Project docs (optional):** e.g. `CONTEXT.md`, `docs/adr/NNN-title.md`, `AGENTS.md` — include only when relevant

## Implementation details

### Approach

How this tracer-bullet slice is executed end-to-end (integration story). Prefer behavior and boundaries over a layer-by-layer rewrite of the PRD.

### Layers and boundaries

Echo **Layers touched** / increments from **`IMPLEMENTATION.md`** where applicable (schema, API, UI, tests, jobs, etc.). Stable repo-relative anchors are welcome (e.g. package or module roots).

### Key risks / gotchas

HITL gates, migrations, backwards compatibility, feature flags — use **`TBD`** if unknown.

### Verification

How to prove this slice locally (commands, manual scenario, test suites to exercise).

Optional: decision-rich **pseudocode**, types, or a trimmed snippet from a prototype—only when prose is weaker; label the source and strip noise.

## Acceptance criteria

Definition of done—observable outcomes aligned with PRD acceptance criteria.

- [ ] …
- [ ] …

## Implementation todos

Granular `- [ ]` checklist for execution (ordering, wiring, code changes, tests). Need not duplicate acceptance criteria verbatim.

- [ ] …
- [ ] …

</ticket-file-template>

Confirm in chat: directory written, file list with paths, and any **`TBD`** carried from source docs.
