# Skill system workflow

This is the canonical artifact contract for the core planning-to-implementation skills. Individual skills may add local rules, but they should not redefine this hierarchy.

## Artifact hierarchy

| Stage | Artifact | Producing skill | Consuming skill |
|-------|----------|-----------------|-----------------|
| Parent requirements | `docs/{initiative-slug}/PRD.md` | `to-prd` | `to-features` |
| Feature slices | `docs/{initiative-slug}/FEATURES.md` | `to-features` | `to-feature-prd` |
| Slice requirements | `docs/{nn}-{feature-slug}/PRD.md` | `to-feature-prd` | `to-implementation-doc`, `to-tickets`, `tdd`, `finish-feature` |
| Implementation outline | `docs/{nn}-{feature-slug}/IMPLEMENTATION.md` | `to-implementation-doc` | `to-tickets`, `tdd`, `finish-feature` |
| Implementation tickets | `docs/{nn}-{feature-slug}/tickets/{nn}-{slug}.md` | `to-tickets` | `tdd`, `finish-feature` |
| Verified as-built handoff | `docs/{nn}-{feature-slug}/IMPLEMENTED.md` | `finish-feature` | future agents and maintainers |

## Handoff order

0. `repo-onboard` inventories and plans migration for existing or messy repos before setup.
1. `setup-skills` prepares `docs/agents/` plus root agent instruction pointers.
2. `agents-md` keeps root agent instructions concise and reference-backed.
3. `grill` sharpens domain language, choices, `CONTEXT.md`, and ADRs before formal planning.
4. `to-prd` writes the parent PRD at `docs/{initiative-slug}/PRD.md`.
5. `to-features` decomposes that PRD into ordered vertical slices at `docs/{initiative-slug}/FEATURES.md`.
6. `to-feature-prd` turns one selected slice into `docs/{nn}-{feature-slug}/PRD.md`.
7. `to-implementation-doc` turns the slice PRD into ticket-ready vertical increments.
8. `to-tickets` writes one ticket per approved implementation increment.
9. `tdd` implements one ticket at a time through RED-GREEN-REFACTOR.
10. `finish-feature` verifies shipped behavior and writes `IMPLEMENTED.md`.

## Naming rules

- `{initiative-slug}` is lowercase ASCII kebab-case, derived from the parent initiative title unless the user provides a slug.
- `{nn}` is the two-digit, zero-padded slice id from the selected `Slice k` heading.
- `{feature-slug}` is lowercase ASCII kebab-case, derived from the selected vertical slice title.
- If a `docs/{nn}-{feature-slug}/` collision refers to a different slice, keep `{nn}` and append a short disambiguator after the title slug.
- Ticket filenames use zero-padded numeric prefixes so lexical order matches implementation order: `01-...`, `02-...`.

## Anti-drift rules

- Do not silently substitute a parent PRD for a slice PRD.
- Do not write tickets from a slice PRD alone unless the user explicitly accepts coarser sequencing.
- Tickets map to implementation increments from `IMPLEMENTATION.md`; they are not a second feature-slicing pass.
- Each artifact should cite the previous artifact it depends on using repo-relative paths.
- Keep `CONTEXT.md` vocabulary stable. If an artifact sharpens durable domain language, update `CONTEXT.md` when authorized or flag the suggested update.
- Issue-tracker publication is optional. Filesystem artifacts are the canonical default unless a user explicitly requests tracker sync.

## Golden example

See [`examples/intelligent-search/README.md`](examples/intelligent-search/README.md) for a complete example chain.
