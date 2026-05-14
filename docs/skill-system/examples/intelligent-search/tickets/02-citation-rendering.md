# Citation rendering contract

## Summary

- **Type:** AFK
- **Blocked by:** `01-fixture-retrieval-answer.md`
- **Conflicts / overlaps:** Response schema/public metadata shape overlaps with `01-fixture-retrieval-answer.md`.
- **Expected changed areas:** response schema or view model, citation mapper/adapter, behavior test.
- **Do not change:** live index, reranker, clarification policy.
- **Shared verification:** fixture query integration test plus citation metadata assertion.

## Documentation references

- **Slice PRD:** [`../slice-prd.md`](../slice-prd.md)
- **Implementation outline:** [`../implementation.md`](../implementation.md)
- **Traceability:**
  - **IMPLEMENTATION.md increment:** #1 Citation rendering contract
  - **PRD:** AC for citation metadata and test failure when citation metadata is omitted.

## Implementation details

### Approach

Expose citation metadata in a stable public response shape so consumers can render and verify source attribution.

### Layers and boundaries

Touch the public response contract and the adapter that maps retrieved source metadata into citations.

### Engineering context (libraries, patterns, testability)

- **Libraries / stack:** Use the repo's existing serialization/view-model conventions.
- **Patterns & conventions:** Keep citation source IDs stable and avoid leaking secret or private paths.
- **Testability:** Assert citation source ID at the public boundary.
- **Snippet policy:** Shape-level snippets are allowed only to clarify the response contract.

### Key risks / gotchas

Citation shape can become hard to change. Keep the first version minimal: source ID and display label are enough unless the PRD requires offsets.

### Verification

Run the fixture query test and assert the expected citation source ID is present.

## Acceptance criteria

- [ ] Public response includes citation metadata for the fixture answer.
- [ ] The citation maps to the expected fixture source ID.
- [ ] The test fails if citation metadata is omitted.

## Implementation todos

- [ ] Add failing assertion for citation metadata.
- [ ] Map fixture source metadata into the response.
- [ ] Keep citation shape minimal and stable.
- [ ] Run the narrow test and record the command.
