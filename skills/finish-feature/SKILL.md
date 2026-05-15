---
name: finish-feature
description: After all docs/{nn}-{feature-slug}/tickets/ are implemented and merged, verify code against PRD, IMPLEMENTATION, and tickets, then write docs/{nn}-{feature-slug}/IMPLEMENTED.md (as-built handoff). Use when a feature is shipped, tickets are done, you need an anti-assumption summary, or quick orientation for future agents without rereading the codebase.
---

# Finish feature

Close the loop after **[to-tickets](../to-tickets/SKILL.md)**: produce a **verified as-built** document so later agents (or humans) know **what actually shipped**, **where it lives**, and **what not to assume**.

**Execution shape:** reference-backed skill — templates and checklists live under **`references/`**; load them when drafting or verifying.

## Quick start

- **Input:** Completed `docs/{nn}-{feature-slug}/tickets/*.md` plus repo state.
- **Do:** Verify shipped behavior against PRD, implementation outline, and tickets.
- **Output:** `docs/{nn}-{feature-slug}/IMPLEMENTED.md`.
- **Next:** Use it as the future-agent handoff.

## References

| Open when you need… | Read |
|---------------------|------|
| Full markdown skeleton for **`IMPLEMENTED.md`** | [`references/implemented-template.md`](references/implemented-template.md) |
| Step-by-step verification against tickets + code | [`references/verification-checklist.md`](references/verification-checklist.md) |
| Golden as-built style example | [`references/example-implemented.md`](references/example-implemented.md) |

## When to use

- Every ticket under **`docs/{nn}-{feature-slug}/tickets/`** is **done** (merged, or verified complete on the branch the user specifies)
- User asks for a **feature handoff**, **as-built doc**, **ship notes**, or **what we implemented**
- Future work on the same slice should avoid **guesswork** and **ticket drift**

**Do not** use for:

- Turning a PRD into tickets — use **[to-tickets](../to-tickets/SKILL.md)** (+ **[to-implementation-doc](../to-implementation-doc/SKILL.md)**)
- Planning or slicing — **to-feature-prd**, **to-features**, **to-implementation-doc**
- When tickets are **not** finished — clarify scope or stop

## Output path (default)

Write:

**`{project-root}/docs/{nn}-{feature-slug}/IMPLEMENTED.md`**

**Filename override:** If **`AGENTS.md`**, **`CONTRIBUTING.md`**, or an explicit user instruction defines a different as-built filename (e.g. `AS-BUILT.md`, `SHIP-NOTES.md`), use that name **in the same directory** and keep the **same section contract** as [`references/implemented-template.md`](references/implemented-template.md).

## Input contract

You MUST have:

1. **`docs/{nn}-{feature-slug}/PRD.md`**
2. **`docs/{nn}-{feature-slug}/tickets/*.md`** (all slice tickets — read **every** file)
3. Target **project root** (workspace or path the user gives)

Recommended:

4. **`docs/{nn}-{feature-slug}/IMPLEMENTATION.md`** — sequencing and increment traceability

If **`IMPLEMENTATION.md`** is missing: proceed from **PRD + tickets**, and note reduced traceability under **Ticket traceability** / **Verification** in **`IMPLEMENTED.md`**.

## Process

1. **Resolve** `{nn}-{feature-slug}`, `{project-root}`, and output filename (default **`IMPLEMENTED.md`**).
2. **Read** `PRD.md`, `IMPLEMENTATION.md` (if present), and **all** ticket files — extract claimed paths, flags, migrations, APIs, verification commands.
3. **Verify** using [`references/verification-checklist.md`](references/verification-checklist.md): confirm paths and behavior claims against the repo (read/grep); run **narrow, safe** test/lint commands from tickets when listed; record **explicit unverified** where you cannot verify.
4. **Draft** **`IMPLEMENTED.md`** from [`references/implemented-template.md`](references/implemented-template.md). Prefer tables, bullets, and repo-relative paths; include **Non-goals & do-not-assume** and any **ticket ↔ code drift**.
5. Check whether shipped behavior introduced or clarified durable domain vocabulary. If so, update `CONTEXT.md` when the user has authorized context edits; otherwise flag the suggested glossary update in chat.
6. If finishing work in this skill collection itself, remind the agent to update the repo-level `CHANGELOG.md` with the changes made.
7. **Write** the file at the resolved path (create **`docs/{nn}-{feature-slug}/`** only if absent and appropriate).
8. **Confirm** in chat: path written; **`TBD` / unverified** items; **drift** between tickets and code.

## Optional follow-up

- Only when the **user asks**: add a one-line pointer in root **`AGENTS.md`** “External References” via **[agents-md](../agents-md/SKILL.md)** to **`IMPLEMENTED.md`** (or the overridden filename).

## Related skills

- **to-tickets** — filesystem tickets before implementation
- **to-implementation-doc** — **`IMPLEMENTATION.md`** outline
- **agents-md** — optional **`AGENTS.md`** pointer

## Context template

- **Project root:** [path]
- **`{nn}-{feature-slug}`:** [zero-padded slice id + kebab-case slug]
- **Branch / merge state (if relevant):** [e.g. all on `main`]
- **Output filename (if not default):** [e.g. `AS-BUILT.md`]
