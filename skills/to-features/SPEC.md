# to-features Specification

## Intent

**to-features** turns a **to-prd**-compatible PRD into an ordered list of **vertical feature slices** suitable for **TDD**: **Slice 0** is the tracer bullet; later slices extend behavior in **RED→GREEN**-friendly steps. Slice ids are **0-based** and used consistently for **depends-on** references so the plan stays unambiguous before tracker issues exist.

## Scope

In scope:

- Consuming PRDs shaped like the template in `skills/to-prd/SKILL.md`
- Vertical (not horizontal) decomposition and TDD-oriented sequencing
- Explicit **Slice 0…n** output with traceability to user stories and acceptance criteria
- Optional **AFK / HITL** typing when it clarifies blockers

Out of scope:

- Creating or editing PRDs (use **to-prd**)
- Publishing issues (use **to-tickets** after the slice list is approved)
- Writing production code or tests (use **tdd** and project conventions)

## Users And Trigger Context

- **Primary users:** Engineers and agents planning implementation after a PRD exists
- **Common user requests:** “Break this PRD into features,” “vertical slices for TDD,” “implementation order from the PRD,” “what’s the tracer bullet?”
- **Should not trigger for:** PRD authoring only, generic project management without a PRD, or requests explicitly asking only for tracker tickets without a slice plan

## Runtime Contract

- **Required first actions:** Obtain a PRD (or equivalent sections); refuse to fabricate missing scope
- **Required outputs:** Markdown matching the output template in `SKILL.md` with **0-based** slice numbering and **slice-index-only** dependencies
- **Non-negotiable constraints:** Vertical slices only; Slice 0 is the tracer bullet; ordering must support incremental RED→GREEN work per **tdd** skill
- **Expected bundled files loaded at runtime:** `references/example-prd-slices.md` when the agent needs a style example

## Source And Evidence Model

Authoritative sources:

- Parent PRD (issue, paste, or conversation)
- `skills/to-prd/SKILL.md` (template shape)
- `skills/tdd/SKILL.md` (vertical vs horizontal slicing)
- `skills/to-tickets/SKILL.md` (optional downstream: issues)

Data that must not be stored in skill artifacts:

- Secrets, customer data, private URLs or identifiers not needed for reproduction

## Reference Architecture

- **`SKILL.md`:** activation, rules, process, output template
- **`SPEC.md`:** this maintenance contract
- **`references/`:** working example (`example-prd-slices.md`)
- **`references/evidence/`:** not used initially
- **`scripts/`:** none
- **`assets/`:** none

## Validation

- **Lightweight validation:** `uv run skills/skill-writer/scripts/quick_validate.py skills/to-features`
- **Acceptance gates:** Valid frontmatter; all `references/` links from `SKILL.md` resolve; output template present; 0-based numbering stated explicitly in `SKILL.md`

## Known Limitations

- Ordering is heuristic; domain-specific blockers may need user correction
- Thin PRDs force more `TBD` and user questions — the skill does not replace discovery

## Maintenance Notes

- **Update `SKILL.md`** when PRD template expectations (from to-prd) or TDD vocabulary changes materially
- **Update `references/example-prd-slices.md`** when an example would reduce common failure modes (wrong Slice 0, horizontal ordering)
- **Update `SPEC.md`** when scope, outputs, or validation gates change
