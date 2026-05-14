---
name: setup-skills
description: Sets up an `## Agent skills` block in AGENTS.md/CLAUDE.md and `docs/agents/` so the engineering skills know this repo's issue tracker (GitHub or local markdown), triage label vocabulary, and domain doc layout. Run before first use of `to-issues`, `to-prd`, `triage`, `diagnose`, `tdd`, `improve-codebase-architecture`, or `zoom-out` — or if those skills appear to be missing context about the issue tracker, triage labels, or domain docs.
disable-model-invocation: true
---

# Setup Skills

Scaffold the per-repo configuration that the engineering skills assume:

- **Issue tracker** — where issues live (**GitHub** or **local markdown** under `.scratch/`)
- **Triage labels** — by default, the same five state-role strings the `triage` skill uses (1:1 mapping); customize only when the user asks
- **Domain docs** — where `CONTEXT.md` and ADRs live, and the consumer rules for reading them

This is a prompt-driven skill, not a deterministic script. Explore, present what you found, confirm with the user, then write.

## Process

### 1. Explore

Look at the current repo to understand its starting state. Read whatever exists; don't assume:

- `git remote -v` and `.git/config` — does a remote point at `github.com`? Which repo?
- `AGENTS.md` and `CLAUDE.md` at the repo root — does either exist? Is there already an `## Agent skills` section in either?
- `CONTEXT.md` and `CONTEXT-MAP.md` at the repo root
- `docs/adr/` and any `src/*/docs/adr/` directories
- `docs/agents/` — does this skill's prior output already exist?
- `.scratch/` — sign that a local-markdown issue tracker convention is already in use

### 2. Present findings and ask

Summarise what's present and what's missing. Walk the user through **two** decisions **one at a time** — present a section, get the user's answer, then move to the next. Don't dump both at once.

Assume the user does not know what these terms mean. Each section starts with a short explainer (what it is, why these skills need it, what changes if they pick differently). Then show the choices and the default.

**Section A — Issue tracker.**

> Explainer: The "issue tracker" is where issues live for this repo. Skills like `to-issues`, `triage`, and `to-prd` read from and write to it — they need to know whether to use the `gh` CLI (GitHub Issues) or markdown files under `.scratch/`. Pick the place you actually track work for this repo.

Only two options are supported:

- **GitHub** — issues live in the repo's GitHub Issues (uses the `gh` CLI)
- **Local markdown** — issues live as files under `.scratch/<feature>/` in this repo (good for solo projects or when you are not using GitHub Issues)

Default posture: if a `git remote` points at GitHub, propose **GitHub**. Otherwise propose **local markdown** (or whichever of the two the user prefers if they override).

**Section B — Domain docs.**

> Explainer: Some skills (`improve-codebase-architecture`, `diagnose`, `tdd`) read a `CONTEXT.md` file to learn the project's domain language, and `docs/adr/` for past architectural decisions. They need to know whether the repo has one global context or multiple (e.g. a monorepo with separate frontend/backend contexts) so they look in the right place.

Confirm the layout:

- **Single-context** — one `CONTEXT.md` + `docs/adr/` at the repo root. Most repos are this.
- **Multi-context** — `CONTEXT-MAP.md` at the root pointing to per-context `CONTEXT.md` files (typically a monorepo).

After Sections A and B are settled, apply the triage defaults below — no extra prompts unless the user volunteered custom label strings.

**Triage labels (for the agent — not a third user interview).**

Unless the user states otherwise, assume the five canonical **state** roles from the `triage` skill map **1:1** to identical label strings in the issue tracker:

- `needs-triage` — maintainer needs to evaluate
- `needs-info` — waiting on reporter
- `ready-for-agent` — fully specified, AFK-ready (an agent can pick it up with no human context)
- `ready-for-human` — needs human implementation
- `wontfix` — will not be actioned

Seed `docs/agents/triage-labels.md` from [triage-labels.md](./triage-labels.md) without asking per-role questions.

**Do not** run a triage-label interview unless the user explicitly wants different label strings or says existing tracker labels conflict with these defaults. If they do, capture overrides in the right-hand column of `docs/agents/triage-labels.md`.

### 3. Confirm and edit

Show the user a draft of:

- The `## Agent skills` block to add to whichever of `CLAUDE.md` / `AGENTS.md` is being edited (see step 4 for selection rules)
- The contents of `docs/agents/issue-tracker.md`, `docs/agents/triage-labels.md`, `docs/agents/domain.md`

For `triage-labels.md`, note in one line that it matches the default `triage` vocabulary unless the user requested custom label strings.

Let them edit before writing.

### 4. Write

**Pick the file to edit:**

- If `CLAUDE.md` exists, edit it.
- Else if `AGENTS.md` exists, edit it.
- If neither exists, ask the user which one to create — don't pick for them.

Never create `AGENTS.md` when `CLAUDE.md` already exists (or vice versa) — always edit the one that's already there.

If an `## Agent skills` block already exists in the chosen file, update its contents in-place rather than appending a duplicate. Don't overwrite user edits to the surrounding sections.

The block:

```markdown
## Agent skills

### Issue tracker

[one-line summary of where issues are tracked]. See `docs/agents/issue-tracker.md`.

### Triage labels

[one-line summary of the label vocabulary]. See `docs/agents/triage-labels.md`.

### Domain docs

[one-line summary of layout — "single-context" or "multi-context"]. See `docs/agents/domain.md`.
```

Then write the three docs files using the seed templates in this skill folder:

- [issue-tracker-github.md](./issue-tracker-github.md) — if GitHub was chosen
- [issue-tracker-local.md](./issue-tracker-local.md) — if local markdown was chosen
- [triage-labels.md](./triage-labels.md) — label mapping (defaults unless the user asked for overrides)
- [domain.md](./domain.md) — domain doc consumer rules + layout

Copy the matching issue-tracker seed to `docs/agents/issue-tracker.md`.

### 5. Done

Tell the user the setup is complete and which engineering skills will now read from these files. Mention they can edit `docs/agents/*.md` directly later — re-running this skill is only necessary if they want to switch issue trackers or restart from scratch.
