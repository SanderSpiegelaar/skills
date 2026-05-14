# to-prd Specification

## Intent

**to-prd** turns conversation context, a greenfield idea, or a grilled plan into a parent PRD at `docs/{initiative-slug}/PRD.md`. It is the durable source for feature slicing; issue-tracker publication is optional and only when explicitly requested.

## Scope

In scope:

- Parent PRD authoring using `references/prd-template.md`
- Discovery questions for problem, users, constraints, success metrics, AI requirements, testing, risks, and open questions
- Domain vocabulary preservation via `CONTEXT.md` / `CONTEXT-MAP.md`
- Handoff to `to-features`

Out of scope:

- Writing slice PRDs
- Writing implementation outlines or tickets
- Publishing to issue trackers by default

## Runtime Contract

- **Required outputs:** `docs/{initiative-slug}/PRD.md`
- **Slug rules:** lowercase ASCII kebab-case derived from initiative title unless the user provides one
- **Question protocol:** use structured questions when available; ask only for missing/high-impact details
- **Non-negotiable constraints:** mark unknowns as `TBD`; do not invent constraints, dates, metrics, or compliance requirements

## Source And Evidence Model

Authoritative sources:

- User conversation and answers
- Existing repo docs, `CONTEXT.md`, ADRs, and relevant code when available
- `docs/skill-system/workflow.md` for artifact hierarchy
- `references/prd-template.md` for PRD body structure
- `docs/skill-system/examples/intelligent-search/parent-prd.md` for golden style

## Validation

- `SKILL.md` frontmatter is valid and links resolve.
- PRD template includes metadata, non-goals, testing, risks, and open questions.
- Output path remains `docs/{initiative-slug}/PRD.md`.
- Handoff to `to-features` is explicit.

## Maintenance Notes

- Update this SPEC when parent PRD scope, path policy, issue publication policy, or template contract changes.
