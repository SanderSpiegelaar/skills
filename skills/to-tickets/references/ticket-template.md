# Ticket file template

Every ticket under `docs/{feature-slug}/tickets/` must follow this structure.

```markdown
# [Ticket title — same as increment title]

## Summary

- **Type:** HITL | AFK
- **Blocked by:** `NN-other-slug.md` (peer ticket in this directory) or **None — can start immediately**
- **Conflicts / overlaps:** [peer ticket, migration, API, or file area] or **None known**
- **Expected changed areas:** [repo-relative module roots, test areas, docs] or **TBD**
- **Do not change:** [boundaries, modules, migrations, APIs] or **None known**
- **Shared verification:** [test/scenario shared with peer tickets] or **None**

## Documentation references

- **Slice PRD:** `docs/{feature-slug}/PRD.md`
- **Implementation outline:** `docs/{feature-slug}/IMPLEMENTATION.md`
- **Traceability:**
  - **IMPLEMENTATION.md increment:** #… (row index from Proposed work breakdown, if applicable)
  - **PRD:** requirement / acceptance-criteria references this increment satisfies
- **Project docs (optional):** e.g. `CONTEXT.md`, `docs/adr/NNN-title.md`, `AGENTS.md` — include only when relevant

## Implementation details

### Approach

How this tracer-bullet increment is executed end-to-end. Prefer behavior and boundaries over a layer-by-layer rewrite of the PRD.

### Layers and boundaries

Echo Layers touched / increments from `IMPLEMENTATION.md` where applicable. Stable repo-relative anchors are welcome.

### Engineering context (libraries, patterns, testability)

- **Libraries / stack:** Candidate libraries or built-ins worth using; versioning or pinning stance.
- **Patterns & conventions:** Repo idioms for layering, dependency direction, naming, error handling, async/IO posture.
- **Testability:** Test seams and existing suites or styles to extend.
- **Snippet policy:** Default to links + rationale. Use minimal shape-level snippets only when public API surface is ambiguous.

### Key risks / gotchas

HITL gates, migrations, backwards compatibility, feature flags — use TBD if unknown.

### Verification

How to prove this increment locally: commands, manual scenario, test suites to exercise.

If verification is shared with another ticket, name the shared scenario and explain what this ticket uniquely proves.

## Acceptance criteria

Definition of done: observable outcomes aligned with PRD acceptance criteria.

- [ ] …
- [ ] …

## Implementation todos

Granular checklist for execution. Need not duplicate acceptance criteria verbatim.

- [ ] …
- [ ] …
```
