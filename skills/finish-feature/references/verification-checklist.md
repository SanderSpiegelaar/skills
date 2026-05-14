# Verification checklist (finish-feature)

Use while reading **`docs/{feature-slug}/PRD.md`**, **`IMPLEMENTATION.md`** (if any), **`tickets/*.md`**, and the **repository**. Goal: **`IMPLEMENTED.md`** reflects **observed reality**, not ticket prose alone.

## 1. Scope and completeness

| Step | Action |
|------|--------|
| 1a | Confirm **every** file in **`docs/{feature-slug}/tickets/`** was opened and considered |
| 1b | List ticket filenames in **`IMPLEMENTED.md` → Ticket traceability** |
| 1c | Compare PRD **out of scope** / deferred items vs code — carry into **Non-goals and do-not-assume** |

## 2. Paths and symbols

For each ticket’s **Layers and boundaries** / **Implementation details**:

| Step | Action |
|------|--------|
| 2a | For each cited **path**, confirm file or directory exists (**grep**, list dir, **read**) |
| 2b | For cited **exported symbols**, **routes**, or **jobs**, confirm definition exists or mark **`Unverified`** |
| 2c | If ticket names a moved or renamed path, note **drift** in the traceability table |

## 3. Flags, migrations, schema

| Step | Action |
|------|--------|
| 3a | **Feature flags / remote config:** find definition and default / rollout notes in code or config |
| 3b | **Database migrations:** identify migration files tied to tickets; confirm present if claimed |
| 3c | **Breaking changes:** document compatibility behavior under **Data, boundaries** or **Non-goals** |

## 4. Verification commands

For each ticket’s **Verification** section and PRD **Verify** guidance:

| Step | Action |
|------|--------|
| 4a | Prefer **narrow** commands (single test file, package-scoped lint) over full suite unless user or time allows |
| 4b | If a command is **risky**, **slow**, or **environment-dependent**, **do not run** — record **`Not run`** with reason |
| 4c | If no command exists, record **`Unverified`** and suggest a minimal command if obvious |

## 5. Acceptance criteria reconciliation

| Step | Action |
|------|--------|
| 5a | For each PRD **acceptance** bullet, tie to **tests**, **manual scenario**, or **observable behavior** |
| 5b | If acceptance is **met differently** than PRD wording, document the **actual** criterion |

## 6. Anti-assumption pass

Before finishing **`IMPLEMENTED.md`**:

| Step | Action |
|------|--------|
| 6a | Add **`Do not assume`** lines where plausible failure modes exist; otherwise say **None identified** briefly |
| 6b | List **similar but unrelated** surfaces in codebase if confusion is likely |
| 6c | Carry forward ticket **`TBD`** into **`IMPLEMENTED.md`** or resolve |

## 7. Escalation (stop-once triggers)

Stop and ask once (batched):

- **`feature-slug`** or **project root** unclear
- **Tickets incomplete** but user insists on **`IMPLEMENTED.md`** — clarify partial-slice wording
- **Conflicting claims** across tickets and code that the repo alone cannot settle
