# Slice PRD template

Use this structure for `docs/{nn}-{feature-slug}/PRD.md`.

```markdown
# [Slice k — title]

## PRD source

- **Parent PRD:** `docs/{initiative-slug}/PRD.md`
- **Slice list:** [link or pointer to to-features output]

## Parent traceability

- **Parent user stories covered:** [story numbers / titles]
- **Parent acceptance criteria covered:** [AC refs]
- **Not covered by this slice:** [explicit exclusions and deferred slices]

## Slice identity

- **Slice:** k — [title]
- **PRD trace:** [from slice]
- **Type:** AFK | HITL
- **Tracer bullet:** yes | no

## Goal

- **Problem:** [slice-only, from Delivers + sanity answers]
- **Solution:** [how this slice addresses it]
- **Success:** [observable outcomes for this slice]

## Scope

### In scope

- …

### Out of scope

- [deferrals to other slices or parent PRD; do not repeat “Not covered” unless useful]

## Dependencies

- **Slices:** [Depends on — slice indices only]
- **Systems / integrations:** …

## Requirements

### Functional

- …

### Non-functional

- …

## Acceptance criteria

- [ ] … (aligned with Verify and PRD trace)

## Testing and verification

- **TDD note:** [from slice]
- **Verify:** [from slice — expanded if needed]

## Open questions

- … (omit section if none; keep TBD visible elsewhere if needed)
```
