# Template: `IMPLEMENTED.md`

Copy this skeleton into **`docs/{nn}-{feature-slug}/IMPLEMENTED.md`** (or team override). Strip unused sections rather than filling with fluff. Every **non-empty** bullet should be **verifiable** or explicitly marked **`Unverified`** / **`TBD`**.

````markdown
# Implemented — [Feature title]

## Feature identity

| Field | Value |
|-------|--------|
| **Slug** | `{nn}-{feature-slug}` |
| **Status** | Shipped |
| **PRD** | `docs/{nn}-{feature-slug}/PRD.md` |
| **Implementation outline** | `docs/{nn}-{feature-slug}/IMPLEMENTATION.md` or **`Missing`** |
| **Tickets dir** | `docs/{nn}-{feature-slug}/tickets/` |
| **This doc generated** | [ISO date or **`TBD`**] |

## Future agent quickstart

- **Read first:** [PRD / IMPLEMENTATION / ticket files most relevant to future work]
- **Run first:** [narrow verification command or manual scenario, or **`TBD`**]
- **Safe assumptions:** [what this handoff verified]
- **Known gaps:** [short list or **None known**]

## As-built summary

[One short paragraph: what the system **does now** — behavior and boundaries, **not** original product intent unless it matches reality.]

## Canonical map — read this first

| Concern | Primary locations (repo-relative) | Notes |
|---------|----------------------------------|-------|
| … | … | … |

Prefer **directories or stable module names** over line numbers.

## Runtime and configuration

| Name / knob | Purpose | Notes |
|-------------|---------|-------|
| Env: `…` | … | **`Unverified`** if not read from code/docs |
| Feature flag / config: … | … | Default: … |

Never paste secret values — names and where to configure only.

## Data, boundaries, and integrations

- **Ownership:** …
- **External systems:** … (APIs, queues, third parties)
- **Invariants / contracts:** …

## Verification

| Check | Command or scenario | Result |
|-------|---------------------|--------|
| … | … | **Pass** / **Not run** / **`Unverified`** |

Link CI job or workflow path if known and stable.

## PRD acceptance — observed mapping

| PRD acceptance (short) | How we prove it | Notes |
|------------------------|-----------------|-------|
| … | test / manual step / API behavior | |

## Ticket traceability

| Ticket file | Main code / artifacts | Drift vs ticket? |
|-------------|----------------------|------------------|
| `tickets/01-….md` | … | **None** / **See notes:** … |

## Non-goals and do-not-assume

- **Not implemented:** …
- **Easy to confuse with X:** …
- **Do not assume:** …

## Known gaps and follow-ups

- … (optional; keep separate from “not implemented” if these are acknowledged debt)

## Document integrity

- **Coverage:** All tickets under `tickets/` were read: **Yes** / **No** (explain)
- **Verification gaps:** …
````

## Section contract

| Section | Purpose |
|---------|---------|
| **As-built summary** | Fast narrative for humans |
| **Canonical map** | Stops codebase-wide fuzzy search |
| **Runtime and configuration** | Prevents silent wrong-env assumptions |
| **Verification** | Ground truth for “does it work” |
| **Future agent quickstart** | Fast restart path for the next agent |
| **Non-goals and do-not-assume** | Stops speculative “fixes” and scope creep |
