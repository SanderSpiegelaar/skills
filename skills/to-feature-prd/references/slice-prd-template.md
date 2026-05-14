# Slice PRD template

Use this structure for `docs/{feature-slug}/PRD.md`.

```markdown
# [Slice k — title]

## PRD source

[Link or pointer to parent PRD]

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

- [deferrals to other slices or parent PRD]

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
