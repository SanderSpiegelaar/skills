# Implementation outline — Tracer Q&A path with fixture retrieval

## PRD reference

- **Path:** `docs/00-tracer-qa-path/PRD.md`
- **Example source:** `example-slice-prd.md`
- **Slice identity:** Slice 0 — Tracer Q&A path with fixture retrieval; AFK; tracer bullet.

## Goal and constraints

Build the smallest end-to-end path that accepts a fixture-backed natural-language query and returns a cited answer through the public boundary. Keep retrieval deterministic and avoid production model/provider coupling. The implementation must prove citation metadata survives from fixture source to response.

## Scope alignment

### In scope

- Fixture document source.
- Deterministic retriever.
- Minimal answer composer.
- Public-boundary behavior test.

### Out of scope

- Live index, reranker, clarification, code block UX, full golden-set runner.

## Proposed work breakdown (for ticketing)

| # | Title | User-visible outcome | Layers touched | Depends on | Maps to PRD | Verification | Ticket candidate | Risk / HITL |
|---|-------|----------------------|----------------|------------|-------------|--------------|------------------|-------------|
| 0 | Fixture retrieval answer | User receives an answer for the fixture question | fixture data, query boundary, test | None | AC 1, AC 2 | API/integration test expects answer + citation source ID | `01-fixture-retrieval-answer.md` | Low / AFK |
| 1 | Citation rendering contract | Response exposes citation metadata in a stable shape | response schema, UI/API adapter, test | #0 | AC 2, AC 3 | Test fails when citation metadata is omitted | `02-citation-rendering.md` | Medium / AFK |

## Integration and touchpoints

- Public query boundary: API route, service method, or UI action in the target repo.
- Fixture corpus: small deterministic source controlled by tests.
- Citation metadata: stable source ID plus optional snippet/offset information.

## Risks, unknowns, and spikes

- **TBD:** Exact public boundary name depends on the repo.
- Risk: overfitting the tracer to fixture-only code; ticket should preserve path shape for live retrieval.

## Verification strategy

Each increment has one behavior-focused test. The first proves a fixture answer can be produced; the second proves citation metadata is part of the public contract.

## Handoff

Use `to-tickets` with this implementation outline and the slice PRD. Do not invent extra increments unless the user confirms a split.
