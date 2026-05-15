# to-tickets Specification

## Intent

**to-tickets** turns **`docs/{nn}-{feature-slug}/PRD.md`** ([to-feature-prd](../to-feature-prd/SKILL.md)) plus **`docs/{nn}-{feature-slug}/IMPLEMENTATION.md`** ([to-implementation-doc](../to-implementation-doc/SKILL.md)) into **numbered markdown implementation tickets** under **`docs/{nn}-{feature-slug}/tickets/`**, each representing one **tracer-bullet implementation increment** inside the selected feature slice and following a **unified ticket template**: **Summary**, **Documentation references**, **Implementation details** (including **Engineering context (libraries, patterns, testability)** alongside approach, layers/boundaries, risks, verification), **Acceptance criteria**, and **Implementation todos**. Files are the **canonical default deliverable**; issue-tracker publication is **optional** and only when the user explicitly requests it.

## Scope

In scope:

- Consuming slice **`PRD.md`** + **`IMPLEMENTATION.md`** with **IMPLEMENTATION first**, **PRD** second for acceptance and scope
- Filesystem output: **`{project-root}/docs/{nn}-{feature-slug}/tickets/{nn}-{slug}.md`** using the unified template in **`SKILL.md`**
- Implementation ordering via numeric filename prefixes (dependency-aware)
- User quiz loop before writing files
- Vertical-increment rules (HITL / AFK, end-to-end behavior)

Out of scope:

- Authoring **`PRD.md`** or **`IMPLEMENTATION.md`** (use **to-feature-prd** / **to-implementation-doc**)
- Default issue-tracker publishing (explicit user request only)

## Users And Trigger Context

- **Primary users:** Engineers and agents handing off from **to-implementation-doc** to concrete work items
- **Common user requests:** “Turn IMPLEMENTATION into tickets,” “write tickets under docs,” “break this slice into numbered tasks”
- **Should not trigger for:** Whole-repo epics without resolved **`feature-slug`** paths, or when the user only wants a chat list with **no files** (confirm intent first)

## Runtime Contract

- **Preferred inputs:** **`docs/{nn}-{feature-slug}/PRD.md`** and **`docs/{nn}-{feature-slug}/IMPLEMENTATION.md`** (paths or bodies)
- **Fallback:** **`PRD.md` only** — allowed **only after explicit user confirmation** that coarser sequencing is acceptable (otherwise steer to **to-implementation-doc**)
- **Required outputs:** One **`*.md`** file per approved implementation increment under **`docs/{nn}-{feature-slug}/tickets/`**, ordered by implementation sequence; body **must** follow **`SKILL.md`** unified template (in order): **Summary** (type, blocked-by, conflicts/overlaps); **Documentation references** (PRD + IMPLEMENTATION paths, traceability, optional CONTEXT/ADR/AGENTS); **Implementation details** (approach, layers/boundaries, **engineering context** (libraries, patterns, testability, snippet discipline per **`SKILL.md`**), key risks/gotchas, verification); **Acceptance criteria** (definition of done); **Implementation todos** (granular checklists)
- **Non-negotiable constraints:** Numeric prefixes reflect dependency order; filenames zero-padded for stable sort; vertical increments only; no tracker publish unless user asks
- **Expected bundled files:** `references/output-conventions.md`, `references/increment-ticketing-rules.md`, and `references/ticket-template.md`

## Downstream / Integrations

- **Issue tracker:** Optional sync when user requests — follow **`docs/agents/issue-tracker.md`** and triage labels when present

## Source And Evidence Model

Authoritative sources:

- **`skills/to-feature-prd/SKILL.md`** — **`PRD.md`** path and slug rules
- **`skills/to-implementation-doc/SKILL.md`** — **`IMPLEMENTATION.md`** shape and increment table
- **`skills/to-tickets/SKILL.md`** — process, naming, template

## Reference Architecture

- **`SKILL.md`:** activation, quick start, concise process, output contract, related skills
- **`SPEC.md`:** this maintenance contract
- **`references/`:** output conventions, increment rules, and ticket template

## Validation

- **Lightweight validation:** `uv run skills/skill-writer/scripts/quick_validate.py skills/to-tickets`
- **Acceptance gates:** Valid frontmatter; explicit **`docs/{nn}-{feature-slug}/tickets/`** contract; unified ticket template sections documented in references (**Implementation details** includes **engineering context** subsection per template); tracker publish documented as opt-in; IMPLEMENTATION+PRD happy path + PRD-only gated fallback; reference links resolve

## Known Limitations

- Missing **`IMPLEMENTATION.md`** forces weaker sequencing unless the user runs **to-implementation-doc**
- Ticket filenames are heuristic; collisions handled by suffixes per **`SKILL.md`**

## Maintenance Notes

- **Update `SKILL.md` and references** when **to-feature-prd** / **to-implementation-doc** paths or templates change
- **Update `SPEC.md`** when output layout, ordering rules, or tracker policy changes
