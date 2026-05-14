# Implemented — Tracer Q&A path with fixture retrieval

## Feature identity

| Field | Value |
|-------|-------|
| **Slug** | `tracer-qa-path` |
| **Status** | Example shipped |
| **PRD** | `PRD.md` |
| **Implementation outline** | `IMPLEMENTATION.md` |
| **Tickets dir** | `tickets/` |
| **This doc generated** | 2026-05-14 |

## Future agent quickstart

- **Read first:** `PRD.md`, `IMPLEMENTATION.md`, then both ticket files.
- **Run first:** the target repo's narrow fixture query test.
- **Safe assumptions:** this example only claims fixture-backed query behavior and citation metadata.
- **Known gaps:** live retrieval, reranking, clarification, and code block UX are intentionally out of scope.

## As-built summary

The tracer path accepts a known fixture question and returns a non-empty answer with citation metadata for the expected fixture source. The shipped behavior proves the public query boundary can carry source attribution end to end.

## Canonical map — read this first

| Concern | Primary locations (repo-relative) | Notes |
|---------|----------------------------------|-------|
| Query boundary | target repo API/UI boundary | Exact path is repo-specific |
| Fixture corpus | target repo test fixtures | Deterministic, not live index |
| Citation contract | response schema or view model | Source ID required |

## Runtime and configuration

| Name / knob | Purpose | Notes |
|-------------|---------|-------|
| Fixture corpus | Test-only document source | Example only |

## Data, boundaries, and integrations

- **Ownership:** Search/query feature area.
- **External systems:** None in this tracer example.
- **Invariants / contracts:** Response includes answer text plus citation metadata.

## Verification

| Check | Command or scenario | Result |
|-------|---------------------|--------|
| Fixture query returns answer | target repo narrow test | Pass in example |
| Citation metadata present | target repo narrow test | Pass in example |

## PRD acceptance — observed mapping

| PRD acceptance (short) | How we prove it | Notes |
|------------------------|-----------------|-------|
| Non-empty fixture answer | Query boundary test | Example path |
| Expected citation source | Citation assertion | Example path |

## Ticket traceability

| Ticket file | Main code / artifacts | Drift vs ticket? |
|-------------|----------------------|------------------|
| `tickets/01-fixture-retrieval-answer.md` | Query boundary, fixture data, test | None in example |
| `tickets/02-citation-rendering.md` | Response metadata, citation adapter, test | None in example |

## Non-goals and do-not-assume

- **Not implemented:** live index, reranker, clarification, code block copy affordance.
- **Do not assume:** production model/provider selection.

## Known gaps and follow-ups

- Expand from fixture retrieval to live retrieval.
- Add golden-set evaluation once the live path exists.

## Document integrity

- **Coverage:** All tickets under `tickets/` were read: Yes.
- **Verification gaps:** Example commands are target-repo placeholders.
