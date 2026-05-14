---
name: repo-onboard
description: Inspects and migrates existing repositories into the agent workflow by inventorying agent instructions, docs, and issue-tracker signals before proposing changes. Use when onboarding, scaffolding, migrating, adopting, or preparing an existing repo for AGENTS.md, docs/agents, issue tracking, triage, planning, TDD, or the skills workflow.
---

# Repo Onboard

## Quick start

- **Input:** Target repository path and any user goal for adopting the workflow.
- **Do:** Inspect first, inventory existing instructions/docs/tracker signals, then present an exact migration plan before writing.
- **Output:** A conservative onboarding plan, followed by confirmed edits that normalize the repo into `docs/agents/` and the core workflow.
- **Next:** Run **setup-skills** for standard `docs/agents/` seeds; run **agents-md** for root instruction cleanup.

## Workflow

1. **Inspect before asking.** Check repository root, `git remote -v`, root and nested `AGENTS.md` / `CLAUDE.md`, `.cursorrules`, `.github/`, `docs/`, `CONTEXT.md`, `CONTEXT-MAP.md`, `docs/adr/`, and `.scratch/`.
2. **Build the inventory.** Use [`references/inventory-checklist.md`](references/inventory-checklist.md) to list discovered agent instructions, workflow docs, domain docs, and issue-tracker signals.
3. **Classify material.** Use [`references/migration-mapping.md`](references/migration-mapping.md) to classify each source as root instruction content, `docs/agents/` content, domain-doc reference, historical/legacy material, or unrelated.
4. **Detect tracker support.** Use [`references/tracker-detection.md`](references/tracker-detection.md) for GitHub and local markdown issue tracking only.
5. **Use the workflow contract.** Use [`references/workflow-contract.md`](references/workflow-contract.md) for canonical artifact names and handoff order.
6. **Present the migration plan.** Include exact files to create/edit, sections to move or summarize, tracker choice detected or recommended, and any content that will be preserved without moving.
7. **Wait for confirmation before writing.** Do not edit, delete, rename, or move user-authored docs until the user approves the migration plan.
8. **Apply with narrow edits.** Preserve user-authored content by summarizing and linking. Delete or overwrite legacy docs only when explicitly approved.
9. **Route follow-up skills.**
   - Run **setup-skills** when `docs/agents/issue-tracker.md`, `triage-labels.md`, or `domain.md` seeds are missing or stale.
   - Run **agents-md** when root `AGENTS.md` / `CLAUDE.md` needs concise pointers or duplicate cleanup.

## Output Contract

- Start with the discovered current state, not generic setup advice.
- Separate proposed changes from confirmed writes.
- Keep GitHub and local markdown as the only supported tracker targets.
- Normalize into the existing skill-system workflow; do not invent a new artifact hierarchy.
- Report final paths changed and which downstream skills can now consume them.

## Related Skills

- **setup-skills** — seeds `docs/agents/` and the `## Agent skills` block after the migration plan is accepted.
- **agents-md** — keeps root agent instructions concise and reference-backed.
- **to-prd / to-tickets / triage / tdd / finish-feature** — consume the normalized workflow artifacts.
