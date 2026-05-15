# Ticket output conventions

| Item | Rule |
|------|------|
| **Directory** | `{project-root}/docs/{nn}-{feature-slug}/tickets/` — create if needed |
| **Order** | Filename numeric prefix = implementation order; blockers get smaller numbers |
| **Padding** | Use zero-padded prefixes so lexical sort matches execution order: `01-…`, `02-…`; use `001-` if there may be more than 99 tickets |
| **Filename** | `{nn}-{short-kebab-title}.md`; ASCII, lowercase; derive slug from implementation increment title |
| **Collisions** | If two increments would share the same slug, append `-2`, `-b`, etc. |

Filesystem tickets are the default deliverable.

Publish to an issue tracker only when the user explicitly requests tracker publication. Follow `docs/agents/issue-tracker.md` and triage labels when present. Publish in dependency order so `Blocked by` can reference real issue IDs when useful.
