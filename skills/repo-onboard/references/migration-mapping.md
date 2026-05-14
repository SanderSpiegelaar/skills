# Migration Mapping

Open this when classifying discovered material and preparing the migration plan.

## Classification Targets

| Classification | Destination or action |
| --- | --- |
| Root instruction content | Keep in `AGENTS.md` or `CLAUDE.md` as concise repo-wide guidance |
| Agent workflow settings | Move or summarize into `docs/agents/` |
| Domain vocabulary and decisions | Reference from `docs/agents/domain.md`; preserve source docs |
| Historical or legacy notes | Preserve in place or move only with approval |
| Unrelated project docs | Leave untouched |

## Standard Destinations

- `docs/agents/issue-tracker.md`: supported tracker choice and publishing rules.
- `docs/agents/triage-labels.md`: label vocabulary consumed by triage and ticket workflows.
- `docs/agents/domain.md`: where domain context and ADRs live.
- Root `AGENTS.md` or `CLAUDE.md`: short pointers to `docs/agents/` and repo-specific commands.

Use `CLAUDE.md` as the edited entrypoint only when it already exists and is clearly the project's maintained agent file. Otherwise prefer `AGENTS.md`. Do not create divergent copies.

## Plan Format

The migration plan must list:
- files to create
- files to edit
- sections to move, summarize, or link
- files to preserve unchanged
- tracker choice detected or recommended
- follow-up skill to run, if any

## Preservation Rules

- Summarize and link user-authored content instead of deleting it.
- Keep command tables only when commands were verified from repo files.
- Mark unresolved conflicts as questions before writing.
- Do not move large docs into root agent instructions.
- Do not create new workflow stages beyond the canonical skill-system hierarchy.

## Follow-Up Routing

- Use **setup-skills** after plan approval when standard `docs/agents/` files need to be created or refreshed.
- Use **agents-md** after migration when root instructions are too long, duplicated, or need concise references.
- Use planning skills only after onboarding artifacts exist and the user asks for planning work.
