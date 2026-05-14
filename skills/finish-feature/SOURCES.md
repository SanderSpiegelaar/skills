# finish-feature — Sources and decisions

## Design decisions

1. **`IMPLEMENTED.md`** as default output name — distinguishes **planned** (**`IMPLEMENTATION.md`**) from **as-built**; easy to grep and teach.
2. **Reference-backed execution** — template and checklist kept in **`references/`** so **`SKILL.md`** stays a router.
3. **Honest unverified sections** — prefer explicit **`Unverified`** / **`Not run`** over silent assumptions.

## Coverage

| Source | Used for |
|--------|----------|
| **to-tickets** ticket template (**Layers**, **Verification**, **Implementation details**) | Verification checklist alignment |
| **to-implementation-doc** handoff wording | Pipeline placement |
| **skill-writer** SPEC patterns | SPEC.md maintenance contract |

## Changelog

- **Initial** — Post-ticket verification + **`IMPLEMENTED.md`** template and checklist (`finish-feature skill authoring` plan).

## Open gaps

- None tracked at skill level — project-specific tooling (exact test commands, monorepo roots) stays in **`IMPLEMENTED.md`** per feature.
