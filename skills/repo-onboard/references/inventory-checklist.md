# Inventory Checklist

Open this when building the current-state inventory for a target repository.

## Repository Signals

- Confirm repo root with `git rev-parse --show-toplevel` when possible.
- Capture remotes with `git remote -v`.
- Note package/tooling signals only when they affect agent instructions.

## Agent Instruction Files

Check:
- root `AGENTS.md`
- root `CLAUDE.md`
- nested `AGENTS.md` files
- nested `CLAUDE.md` files
- `.cursorrules`
- `.cursor/rules/`
- `.github/copilot-instructions.md`
- other agent-specific docs named by the user or linked from root instructions

For each file, record:
- path
- intended scope
- referenced commands or docs
- whether content is still actionable
- overlaps with other instruction files

## Workflow And Domain Docs

Check:
- `docs/agents/`
- `docs/skill-system/`
- `CONTEXT.md`
- `CONTEXT-MAP.md`
- context-local `CONTEXT.md` files
- `docs/adr/`
- `.scratch/`
- `docs/**/PRD.md`
- `docs/**/IMPLEMENTATION.md`
- `docs/**/tickets/*.md`
- `docs/**/IMPLEMENTED.md`

Record whether each artifact appears canonical, stale, duplicated, or unrelated to the workflow.

## Inventory Output

Group findings as:
- current root agent instructions
- existing workflow docs
- domain and decision docs
- tracker signals
- duplicates and conflicts
- missing standard workflow files

Do not propose edits until this inventory is complete enough to explain the current state.
