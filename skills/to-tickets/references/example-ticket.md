# Fixture retrieval answer

## Summary

- **Type:** AFK
- **Blocked by:** None — can start immediately
- **Conflicts / overlaps:** `02-citation-rendering.md` touches response metadata shape; coordinate public response contract.
- **Expected changed areas:** query boundary, fixture data, behavior test.
- **Do not change:** live index integration, reranker, production model/provider wiring.
- **Shared verification:** fixture query integration test.

## Documentation references

- **Slice PRD:** `../PRD.md`
- **Implementation outline:** `../IMPLEMENTATION.md`
- **Traceability:**
  - **IMPLEMENTATION.md increment:** #0 Fixture retrieval answer
  - **PRD:** AC for non-empty answer and expected fixture source citation.
- **Project docs (optional):** `CONTEXT.md` / ADRs only when the target repo defines search vocabulary.

## Implementation details

### Approach

Create the smallest deterministic query path that accepts a known fixture question and returns an answer from fixture content.

### Layers and boundaries

Touch the public query boundary, fixture corpus, retrieval/composition logic, and one behavior-focused test. Keep live retrieval out of scope.

### Engineering context (libraries, patterns, testability)

- **Libraries / stack:** Defer to the target repo test runner and existing API/UI patterns.
- **Patterns & conventions:** Keep fixture retrieval injectable so live retrieval can replace it in a later increment.
- **Testability:** Inject fixture corpus or retriever; assert public response behavior rather than private method calls.
- **Snippet policy:** Use only shape-level examples if the public response contract is unclear.

### Key risks / gotchas

Do not hard-code production assumptions from the fixture. Keep the tracer path structurally close to the future live path.

### Verification

Run the narrow test for the query boundary. The test should fail if the fixture source is not used.

## Acceptance criteria

- [ ] Fixture question returns a non-empty answer through the public boundary.
- [ ] The answer is grounded in the fixture source.
- [ ] The behavior test fails when fixture retrieval is disabled.

## Implementation todos

- [ ] Add or identify a minimal fixture source.
- [ ] Add a failing behavior test for the fixture question.
- [ ] Implement deterministic fixture retrieval.
- [ ] Return minimal answer text through the public boundary.
- [ ] Run the narrow test and record the command.
