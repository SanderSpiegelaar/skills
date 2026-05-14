# to-implementation-doc Specification

## Intent

**to-implementation-doc** turns a slice-scoped **`docs/{feature-slug}/PRD.md`** (from **to-feature-prd**) into a co-located **`docs/{feature-slug}/IMPLEMENTATION.md`**: a **high-level** outline whose main section is **proposed vertical increments** mapped to PRD acceptance criteria, so **to-tickets** can produce numbered markdown tickets under **`docs/{feature-slug}/tickets/`** without re-deriving sequencing from the PRD alone.

## Scope

In scope:

- Input contract tied to **to-feature-prd** output path and slug rules
- Default output at `{project-root}/docs/{feature-slug}/IMPLEMENTATION.md`
- Ticket-oriented template (work breakdown, dependencies, traceability, verification, handoff)
- Optional shallow codebase / `CONTEXT.md` / ADR read for vocabulary only (no scope expansion)

Out of scope:

- Authoring or replacing **`PRD.md`** (use **to-feature-prd**)
- Writing filesystem tickets or publishing tracker issues (use **to-tickets**)
- Full detailed design (exhaustive ERDs, layer-by-layer specs, production code)

## Users And Trigger Context

- **Primary users:** Engineers and agents moving from a **single-slice PRD** to **implementation tickets**
- **Common user requests:** “Implementation outline for this slice,” “sequence work for ticketing,” “bridge PRD to issues”
- **Should not trigger for:** Epic-wide plans without a slice PRD, or when the user only wants issues without **`IMPLEMENTATION.md`** ( **to-tickets** may still run on **`PRD.md`** alone)

## Runtime Contract

- **Required inputs:** **`docs/{feature-slug}/PRD.md`** (path or body); same **`{feature-slug}`** for output directory
- **Required outputs:** Markdown file **`IMPLEMENTATION.md`** using the template in **`SKILL.md`**, with **Proposed work breakdown (for ticketing)** populated as numbered vertical increments with PRD traceability
- **Non-negotiable constraints:** No new scope beyond the PRD; increments must be **vertical** and **tracer-first** when the PRD implies a tracer bullet; do not paste the entire parent PRD
- **Expected bundled files:** none required at runtime (`SKILL.md` self-contained)

## Downstream Consumer

- **to-tickets** should prefer **`PRD.md` + `IMPLEMENTATION.md`**, reading **`IMPLEMENTATION.md`** first for sequencing and dependencies, **`PRD.md`** for acceptance and scope
- **Default output:** numbered markdown files under **`docs/{feature-slug}/tickets/`**; issue-tracker publication only when the user explicitly requests it

## Source And Evidence Model

Authoritative sources:

- Slice **`PRD.md`** in the target project
- **`skills/to-feature-prd/SKILL.md`** (slug/path rules, PRD shape)
- **`skills/to-tickets/SKILL.md`** (vertical slice rules, issue shape)

## Reference Architecture

- **`SKILL.md`:** activation, input/output contract, process, output template
- **`SPEC.md`:** this maintenance contract

## Validation

- **Lightweight validation:** `uv run skills/skill-writer/scripts/quick_validate.py skills/to-implementation-doc` (when runner exists in repo)
- **Acceptance gates:** Valid frontmatter; explicit paths **`PRD.md`** / **`IMPLEMENTATION.md`**; template includes ticketing handoff and vertical-increment rules

## Known Limitations

- Thin or **`TBD`**-heavy PRDs require user questions—**to-implementation-doc** does not invent scope
- Project-specific doc layouts may need mirroring notes in **`AGENTS.md`** (skill allows legacy mirror only when conventions require it)

## Maintenance Notes

- **Update `SKILL.md`** when **to-feature-prd** PRD template or **to-tickets** input expectations change
- **Update `SPEC.md`** when the IO contract or downstream handoff changes
