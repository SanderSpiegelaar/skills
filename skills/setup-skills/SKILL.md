---
name: setup-skills
description: Sets up an `## Agent skills` block in AGENTS.md/CLAUDE.md and `docs/agents/` so engineering skills know this repo's issue tracker, triage labels, and domain doc layout. Use when preparing a repo for to-prd, to-features, to-feature-prd, to-implementation-doc, to-tickets, triage, diagnose, tdd, finish-feature, improve-codebase-architecture, or zoom-out.
disable-model-invocation: true
---

# Setup Skills

## Quick start

- **Input:** Target repo needing agent workflow setup.
- **Do:** Inspect repo signals, ask tracker/domain-doc choices, create `docs/agents/` and agent instruction pointers.
- **Output:** `docs/agents/issue-tracker.md`, `triage-labels.md`, `domain.md`, plus `AGENTS.md` / `CLAUDE.md` alignment.
- **Next:** Run **agents-md** if root instructions need cleanup. Use the bundled workflow contract for artifact names and handoff order.

## Workflow

1. **Explore first.** Check `git remote -v`, `.git/config`, root `AGENTS.md` / `CLAUDE.md`, existing `docs/agents/`, `CONTEXT.md`, `CONTEXT-MAP.md`, `docs/adr/`, context-local ADRs, and `.scratch/`.
2. **Ask two setup questions.** Use the host's **Ask User Question** / structured question tool when available; otherwise ask concise numbered questions in chat.
3. **Issue tracker choice.** Explain that `to-tickets`, `triage`, and `to-prd` may publish to the tracker when the user asks. Support only GitHub issues or local markdown under `.scratch/<feature>/`. Default to GitHub when a GitHub remote exists; otherwise local markdown.
4. **Domain docs choice.** Confirm single-context (`CONTEXT.md` + `docs/adr/`) or multi-context (`CONTEXT-MAP.md` pointing at context-specific `CONTEXT.md` files).
5. **Apply triage defaults.** Use the five default state labels unless the user explicitly requests custom label strings: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`.
6. **Show a draft before writing.** Include the `## Agent skills` block plus the three `docs/agents/*.md` files. Let the user edit before writing.
7. **Write the chosen agent entrypoint.** Edit `CLAUDE.md` if it exists; otherwise `AGENTS.md`; if neither exists, ask which one to create. Do not create divergent `AGENTS.md` and `CLAUDE.md` copies.
8. **Validate agent instructions.** If root `AGENTS.md` is missing or weak, follow [agents-md](../agents-md/SKILL.md) end-to-end while preserving the `## Agent skills` block.

## Output contract

- Copy the selected seed from [`references/issue-tracker-github.md`](references/issue-tracker-github.md) or [`references/issue-tracker-local.md`](references/issue-tracker-local.md) to `docs/agents/issue-tracker.md`.
- Copy [`references/triage-labels.md`](references/triage-labels.md) to `docs/agents/triage-labels.md`, editing only custom label mappings the user requested.
- Copy [`references/domain.md`](references/domain.md) to `docs/agents/domain.md`, editing the chosen domain-doc layout.
- Insert or update the block in [`references/agent-skills-block.md`](references/agent-skills-block.md).
- Confirm the written paths and which engineering skills consume them.

## References

- [`references/workflow-contract.md`](references/workflow-contract.md) — portable artifact hierarchy and handoff chain for the core workflow.
- [`references/agent-skills-block.md`](references/agent-skills-block.md) — `AGENTS.md` / `CLAUDE.md` block.
- [`references/issue-tracker-github.md`](references/issue-tracker-github.md) — GitHub issue-tracker seed.
- [`references/issue-tracker-local.md`](references/issue-tracker-local.md) — local markdown issue-tracker seed.
- [`references/triage-labels.md`](references/triage-labels.md) — default state-label mapping.
- [`references/domain.md`](references/domain.md) — domain-doc consumer rules.

## Related skills

- **agents-md** — normalizes concise agent instructions after setup.
- **to-prd / to-tickets / triage** — consume tracker and triage settings.
- **grill / tdd / finish-feature / improve-codebase-architecture** — consume domain-doc settings.
