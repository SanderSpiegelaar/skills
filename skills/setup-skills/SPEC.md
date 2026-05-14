# setup-skills Specification

## Intent

**setup-skills** prepares a target repository for the core engineering skill workflow by creating or updating `docs/agents/` configuration and root agent-instruction pointers. It does not create product artifacts; it establishes the repo conventions that downstream skills read.

## Scope

In scope:

- Issue tracker choice: GitHub issues or local markdown under `.scratch/<feature>/`
- Triage label mapping using the default state labels unless the user overrides
- Domain-doc layout choice: single-context `CONTEXT.md` + `docs/adr/`, or multi-context `CONTEXT-MAP.md`
- `## Agent skills` block in `AGENTS.md` or `CLAUDE.md`
- Bundled reference to the workflow contract at `references/workflow-contract.md`

Out of scope:

- Creating PRDs, tickets, ADRs, or implementation docs
- Inventing tracker labels beyond the supported state vocabulary
- Creating divergent `AGENTS.md` and `CLAUDE.md` bodies

## Runtime Contract

- **Required first actions:** inspect repo signals before asking the user
- **Required outputs:** `docs/agents/issue-tracker.md`, `docs/agents/triage-labels.md`, `docs/agents/domain.md`, and an agent-instruction pointer block
- **User questions:** use structured questions when available for tracker and domain-doc layout
- **Non-negotiable constraints:** preserve existing user instructions, avoid duplicate `## Agent skills` blocks, and keep runtime references portable when installed outside this repository

## Validation

- `SKILL.md` frontmatter is valid and links resolve.
- Seed reference files exist for tracker, triage labels, domain docs, workflow contract, and agent block.
- Output contract names all files setup writes.
- Related skills include the workflow consumers.

## Maintenance Notes

- Update this SPEC when setup outputs, supported tracker choices, or domain-doc layout policy changes.
- Update seed references when downstream skills need new shared setup context.
