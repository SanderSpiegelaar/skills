# Changelog

## 2026-05-14

- Standardized the core workflow artifact hierarchy: parent PRDs at `docs/{initiative-slug}/PRD.md`, slice PRDs at `docs/{feature-slug}/PRD.md`, implementation outlines at `docs/{feature-slug}/IMPLEMENTATION.md`, tickets under `docs/{feature-slug}/tickets/`, and as-built handoffs at `docs/{feature-slug}/IMPLEMENTED.md`.
- Kept `to-implementation-doc` as the canonical skill name and updated stale `to-implementation` references in core workflow docs/specs.
- Replaced stale `to-issues` references in `setup-skills` with the current `to-tickets` workflow.
- Added shared Ask User Question guidance for structured decision points where relevant.
- Added shared `CONTEXT.md` / `CONTEXT-MAP.md` guidance for preserving and flagging durable domain vocabulary.
- Clarified the workflow handoff chain across `setup-skills`, `agents-md`, `grill`, `to-prd`, `to-features`, `to-feature-prd`, `to-implementation-doc`, `to-tickets`, `tdd`, and `finish-feature`.
- Clarified `to-tickets` granularity: tickets map to implementation increments from `IMPLEMENTATION.md`, with optional conflicts/overlaps noted in each ticket.
- Updated `README.md` to match the new docs-first workflow and fixed stale skill/validator links.
