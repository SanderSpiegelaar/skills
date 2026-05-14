# to-feature-prd Specification

## Intent

**to-feature-prd** turns **one vertical slice** from a **to-features** breakdown into a **thin PRD** saved as `docs/{feature-slug}/PRD.md` in the target project. A short **Ask User Question** sanity pass reduces ambiguous scope before writing the file.

## Scope

In scope:

- Consuming a single slice block in the format defined in `skills/to-features/SKILL.md`
- One or two rounds of structured user questions before drafting
- Filesystem output at project root: `docs/{feature-slug}/PRD.md`

Out of scope:

- Authoring or publishing the **parent** PRD (use **to-prd**)
- Creating slice lists (use **to-features**)
- Numbered implementation ticket files under **`docs/{feature-slug}/tickets/`** (use **to-tickets**)
- Full domain grilling with `CONTEXT.md` / ADR updates (use **grill** unless the user asks)

## Users And Trigger Context

- **Primary users:** Engineers and agents who want a documented, slice-sized spec next to the repo
- **Common user requests:** “PRD for Slice 2”, “put this slice in docs”, “sanity-check then write PRD.md”
- **Should not trigger for:** Whole-product PRDs, generic PM documents without a **to-features** slice input

## Runtime Contract

- **Required first actions:** Obtain exactly one slice + **PRD source**; refuse to fabricate scope beyond **Delivers** / **PRD trace** / **Verify**
- **Required outputs:** Markdown file at `docs/{feature-slug}/PRD.md` using the template in `SKILL.md`
- **Non-negotiable constraints:** Ask User Question for the sanity pass when available; slug rules in `SKILL.md`; no tracker publish in this skill
- **Expected bundled files loaded at runtime:** none required (link to **to-features** for input shape)

## Source And Evidence Model

Authoritative sources:

- The selected slice text and **PRD source** line from **to-features** output
- Parent PRD, preferably `docs/{initiative-slug}/PRD.md`, when the user provides a path, link, or paste
- `skills/to-features/SKILL.md` (slice template)
- `skills/to-feature-prd/SKILL.md` (runtime template)

Data that must not be stored in skill artifacts:

- Secrets, customer data, private identifiers not needed for reproduction

## Reference Architecture

- **`SKILL.md`:** activation, process, slug rules, PRD template
- **`SPEC.md`:** this maintenance contract
- **`references/`:** not used initially
- **`scripts/`:** none

## Validation

- **Lightweight validation:** `uv run skills/skill-writer/scripts/quick_validate.py skills/to-feature-prd`
- **Acceptance gates:** Valid frontmatter; `name` matches folder `to-feature-prd`; input/output contracts stated in `SKILL.md`; PRD output path and filename documented

## Known Limitations

- Thin slice text or missing parent PRD forces more **`TBD`** and follow-up questions
- Slug derivation is heuristic; user confirmation in the sanity pass is required

## Maintenance Notes

- **Update `SKILL.md`** when **to-features** slice fields or **to-prd** cross-links change materially
- **Update `SPEC.md`** when outputs, paths, or validation gates change
