# Slice 0 — Tracer Q&A path with fixture retrieval

## PRD source

- **Parent PRD:** `docs/intelligent-search/PRD.md`
- **Example source:** [`parent-prd.md`](parent-prd.md)
- **Slice list:** [`vertical-slices.md`](vertical-slices.md)

## Parent traceability

- **Parent user stories covered:** Story 1 and Story 2.
- **Parent acceptance criteria covered:** fixture retrieval returns expected source; factual answer includes citation metadata.
- **Not covered by this slice:** live index, reranking, clarification, code block copy affordance, full golden-set runner.

## Slice identity

- **Slice:** 0 — Tracer Q&A path with fixture retrieval
- **PRD trace:** Story 1, Story 2; fixture retrieval and citation AC.
- **Type:** AFK
- **Tracer bullet:** yes

## Goal

- **Problem:** The team needs a small end-to-end path proving query input can produce a grounded cited answer.
- **Solution:** Implement a fixture-backed query path with minimal retrieval, answer composition, and citation metadata.
- **Success:** A public API or UI boundary returns answer text and at least one expected citation for the fixture question.

## Scope

### In scope

- Fixture corpus and deterministic retrieval for one representative question.
- Minimal answer composer that cites retrieved source metadata.
- Behavior-focused test through the public query boundary.

### Out of scope

- Live document index.
- Reranking.
- Multi-turn clarification.
- Code block copy affordance.
- Production model/provider selection.

## Dependencies

- **Slices:** None.
- **Systems / integrations:** Query API/UI boundary, fixture data, citation metadata shape.

## Requirements

### Functional

- Accept a natural-language fixture question.
- Return answer text grounded in fixture source content.
- Return citation metadata with stable source ID.

### Non-functional

- Keep the path deterministic for tests.
- Avoid adding production-only provider dependencies in this tracer slice.

## Acceptance criteria

- [ ] Given the fixture question, the public query boundary returns a non-empty answer.
- [ ] The response contains citation metadata for the expected fixture source.
- [ ] The test fails when citation metadata is omitted.

## Testing and verification

- **TDD note:** RED on public query API returning answer text plus citation metadata; GREEN with fixture retriever and minimal answer composer.
- **Verify:** API/integration test proves expected fixture source appears in citations.

## Open questions

- **TBD:** Exact public boundary name depends on the target repository.
