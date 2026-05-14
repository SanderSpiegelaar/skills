# Slice PRD path rules

- **`{feature-slug}`:** lowercase kebab-case, ASCII only, derived from the slice title.
- Collapse whitespace and strip punctuation.
- **Path:** `{project-root}/docs/{feature-slug}/PRD.md`.
- Create `docs/{feature-slug}/` if needed.
- If `docs/{feature-slug}/` already exists for a different slice, append `-slice-{k}`.
- Use the exact filename `PRD.md` with capital `PRD`.
- Confirm the slug during the sanity pass.
