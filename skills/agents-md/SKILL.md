---
name: agents-md
description: Creates and maintains concise AGENTS.md and CLAUDE.md project instruction files. Use when asked to create AGENTS.md, update AGENTS.md, maintain agent docs, set up CLAUDE.md, document repository agent conventions, keep coding-agent instructions minimal and reference-backed, or bootstrap agent docs for an empty repo, greenfield scaffold, or low-signal tree.
---

# Maintaining AGENTS.md

Goal: concise, actionable agent instructions. Target under 60 lines; never exceed 100.

## Workflow

### Mandatory agent defaults

Unless the user overrides (e.g. “skip caveman”, “normal mode”, “do not push”):

- **Caveman-first:** Before substantive work each user turn/session, invoke/read the **caveman** skill (host discovery) or repo path `skills/caveman/SKILL.md` when maintained in-tree.
- **Commit and push:** When this skill’s maintenance work is finished and edits exist: inspect `git status`, commit only meaningful changes with a clear imperative message and **Commit Attribution** (below); push to the current branch upstream if a remote exists, push is permitted, user did not forbid it, and there is unpushed work.

1. Inspect before writing:
   - package manager: lock files and manifests
   - commands: `package.json`, `Makefile`, task runners, CI workflows
   - docs/specs/policies: `README.md`, `CONTRIBUTING.md`, `docs/`, `specs/`, `policies/`, `SECURITY.md`, `.github/`
   - conventions: current code patterns, test layout, generated files, legacy areas to avoid
   **Low-signal repository:** if **any** of the following is true, elicit before drafting `AGENTS.md` (do not guess commands or paths):
   - No lockfile and no actionable package/build manifest (or only a generic/placeholder template).
   - No real application or source tree beyond scaffold placeholders.
   - README-only or nearly empty tree (e.g. `.git` and `README.md` only).
   - User asked for agent instructions before tooling or layout exists.
   **Elicitation:** Use the host's structured question flow. In **Cursor**, call **`AskQuestion`** for discrete choices: primary language/stack, package manager, test runner, lint/format entrypoints, monorepo vs single package, CI config location if any, and **minimal stub now** vs **defer command tables** until the repo has verifiable scripts. For topics that do not fit multiple choice, ask a short follow-up in chat.
   **Guards:** Do not list fabricated commands. If something remains unknown after elicitation, omit that part of the file or mark it explicitly pending; never invent plausible-looking paths.
2. Choose scope:
   - root `AGENTS.md`: repo-wide defaults
   - nested `AGENTS.md`: only when a subtree has different commands or rules
   - closest instruction file wins; keep narrower files shorter than root files
3. Write the smallest useful file.
4. Verify exact paths and commands exist; verify `## Agent runtime defaults` (if emitted) cites no bogus repo paths.

## File Setup

- Create `AGENTS.md` at the repository root.
- If a Claude-compatible entrypoint is required, symlink `CLAUDE.md` to `AGENTS.md`.
- Do not maintain divergent `AGENTS.md` and `CLAUDE.md` copies.

## Default Sections

Use only sections that add non-obvious value.

````markdown
# Agent Instructions

## Agent runtime defaults
- Caveman-first: invoke/read **caveman** skill each user turn/session unless user opts out (“normal mode”, “skip caveman”, “no caveman”).
- Finish work: after task completion, stage and commit with required attribution; push upstream when safe, permitted, and user did not forbid.

## Package Manager
- Use **pnpm**: `pnpm install`

## Commands
| Task | Command |
|------|---------|
| Test file | `pnpm vitest run path/to/file.test.ts` |
| Lint file | `pnpm eslint path/to/file.ts` |

## External References
| Need | File |
|------|------|
| Setup | `CONTRIBUTING.md` |
| Architecture | `docs/architecture.md` |
| Security policy | `SECURITY.md` |

## Key Conventions
- Generated files: update with `pnpm generate`; do not edit by hand.

## Commit Attribution
AI commits MUST include:
```
Co-Authored-By: (the agent's name and attribution byline)
```
````

## Writing Rules

- Use headings, bullets, and tables; avoid paragraphs.
- Use repo-relative paths; avoid vague references like "see docs".
- Reference existing docs/specs/policies instead of copying them.
- List exact external files for setup, architecture, API specs, security, release, and policy docs when they exist.
- Prefer file-scoped test/lint/typecheck commands; include full builds only when no narrower command exists.
- Put commands in tables when there is more than one.
- Keep one rule per bullet.
- Keep rationale out unless it prevents a likely mistake.
- Do not restate linter, formatter, or typechecker config.
- Do not list installed skills or plugins except mandatory names in **`## Agent runtime defaults`** (caveman-first); avoid other skill inventories.
- Do not include generic quality slogans.
- When `## Agent skills` and `docs/agents/` already exist (e.g. after `setup-skills`), **preserve** that section and rely on those files for issue-tracker, triage-label, and domain detail instead of inlining them.

## External Reference Rules

Good:

```markdown
## External References
| Need | File |
|------|------|
| API contract | `docs/api.md` |
| Release process | `docs/releasing.md` |
```

## Anti-Patterns

- welcome text, intros, conclusions, or pleasantries
- long prose explaining why instructions matter
- duplicated content from `README.md`, `CONTRIBUTING.md`, or policy docs
- project-wide commands when file-scoped commands are available
- nested `AGENTS.md` files that repeat root instructions
- stack-specific command tables built only from assumptions after inspection and elicitation failed to confirm them
