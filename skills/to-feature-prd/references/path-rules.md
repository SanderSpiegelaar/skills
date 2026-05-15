# Slice PRD path rules

- **`{nn}`:** two-digit, zero-padded slice id from the selected `Slice k` heading. Examples: `Slice 0` -> `00`, `Slice 1` -> `01`, `Slice 12` -> `12`.
- **`{feature-slug}`:** lowercase kebab-case, ASCII only, derived from the slice title.
- Collapse whitespace and strip punctuation in the title slug.
- **Path:** `{project-root}/docs/{nn}-{feature-slug}/PRD.md`.
- Create `docs/{nn}-{feature-slug}/` if needed.
- If the slice number is missing or ambiguous, ask for it during the sanity pass before writing.
- If `docs/{nn}-{feature-slug}/` already exists for a different slice, keep `{nn}` and append a short disambiguator after the title slug.
- Use the exact filename `PRD.md` with capital `PRD`.
- Confirm the numbered slug during the sanity pass.
