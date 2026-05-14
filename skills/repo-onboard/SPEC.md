# Repo Onboard Specification

## Intent

`repo-onboard` prepares an existing repository for the local agent workflow. It is for repos that may already contain agent instructions, planning docs, tracker conventions, or partially adopted workflow files.

The skill's main job is intake and migration planning. It discovers the current state, classifies what should move or be referenced, and only writes after the user confirms the exact plan.

## Scope

In scope:
- inventorying root and nested agent instruction files
- detecting existing `docs/agents/`, domain docs, ADRs, and local issue folders
- detecting GitHub remotes and local markdown tracker conventions
- planning migration into `docs/agents/` and root instruction pointers
- routing to `setup-skills` and `agents-md`

Out of scope:
- supporting Jira, Linear, GitLab issues, or other trackers in v1
- rewriting the core skill-system artifact hierarchy
- deleting or overwriting legacy docs without explicit approval
- implementing feature PRDs, tickets, or code changes as part of onboarding

## Users And Trigger Context

- Primary users: maintainers adopting the workflow in an existing project.
- Common requests: "onboard this repo", "migrate this project into our workflow", "scaffold agent docs", "prepare this repo for to-prd/to-tickets", "standardize AGENTS.md".
- Should not trigger for: creating a brand-new clean `AGENTS.md` only, implementing tickets, or normal code review.

## Runtime Contract

- Required first actions: inspect the repository before asking questions or proposing files.
- Required outputs: inventory, classification, exact migration plan, and only then confirmed edits.
- Non-negotiable constraints: plan before write, preserve user-authored content, support only GitHub/local tracker targets.
- Expected bundled files loaded at runtime:
  - `references/inventory-checklist.md`
  - `references/migration-mapping.md`
  - `references/tracker-detection.md`
  - `references/workflow-contract.md`

## Source And Evidence Model

Authoritative sources:
- `references/workflow-contract.md`
- `skills/setup-skills/SKILL.md`
- `skills/agents-md/SKILL.md`

Useful improvement sources:
- onboarding attempts in real repositories
- examples where legacy docs were preserved cleanly
- validation results from `skills/skill-writer/scripts/quick_validate.py`

Data that must not be stored:
- private repository contents copied from user projects
- credentials, issue tokens, or private remote URLs beyond generic detection notes

## Maintenance Rules

- Keep `SKILL.md` as the runtime router and move branch details into direct reference files.
- Do not add tracker support until the downstream workflow can consume it.
- Update this spec if tracker scope, write-confirmation policy, or migration output contract changes.
