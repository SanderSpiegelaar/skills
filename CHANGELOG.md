# Changelog

## 2026-05-14 — Golden examples and workflow contract

- Added `docs/skill-system/workflow.md` as the canonical artifact hierarchy and handoff contract for the core workflow.
- Added the intelligent-search golden example chain under `docs/skill-system/examples/intelligent-search/`.
- Added missing core `SPEC.md` files for `setup-skills`, `grill`, `to-prd`, and `tdd`.
- Upgraded parent PRD, slice PRD, implementation outline, ticket, and implemented handoff templates with stronger traceability and future-agent restart fields.
- Linked core runtime skills and `README.md` to the shared workflow contract and golden examples.

## 2026-05-14

- Split long core `SKILL.md` files into concise reference-backed entrypoints for `setup-skills`, `to-prd`, `to-feature-prd`, `to-implementation-doc`, `to-tickets`, `tdd`, and `skill-writer`.
- Moved bulky templates, path rules, ticketing rules, TDD guidance, and setup seed docs into `references/` while preserving workflow behavior.
- Standardized the core workflow artifact hierarchy: parent PRDs at `docs/{initiative-slug}/PRD.md`, slice PRDs at `docs/{feature-slug}/PRD.md`, implementation outlines at `docs/{feature-slug}/IMPLEMENTATION.md`, tickets under `docs/{feature-slug}/tickets/`, and as-built handoffs at `docs/{feature-slug}/IMPLEMENTED.md`.
- Kept `to-implementation-doc` as the canonical skill name and updated stale `to-implementation` references in core workflow docs/specs.
- Replaced stale legacy issue-writing references in `setup-skills` with the current `to-tickets` workflow.
- Added shared Ask User Question guidance for structured decision points where relevant.
- Added shared `CONTEXT.md` / `CONTEXT-MAP.md` guidance for preserving and flagging durable domain vocabulary.
- Clarified the workflow handoff chain across `setup-skills`, `agents-md`, `grill`, `to-prd`, `to-features`, `to-feature-prd`, `to-implementation-doc`, `to-tickets`, `tdd`, and `finish-feature`.
- Clarified `to-tickets` granularity: tickets map to implementation increments from `IMPLEMENTATION.md`, with optional conflicts/overlaps noted in each ticket.
- Updated `README.md` to match the new docs-first workflow and fixed stale skill/validator links.
