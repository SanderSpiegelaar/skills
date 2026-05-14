# Vertical feature slices (TDD order)

**PRD source:** `docs/intelligent-search/PRD.md` (represented here by `example-parent-prd.md`)

Order: Slice 0 Slice 1 Slice 2 Slice 3

### Slice 0 — Tracer Q&A path with fixture retrieval
- **Type:** AFK
- **Tracer bullet:** yes
- **Delivers:** A user can ask one fixture-backed question and receive an answer with at least one citation from the fixture corpus.
- **PRD trace:** Story 1, Story 2; AC for fixture retrieval and cited factual answer.
- **Depends on:** None
- **TDD note:** RED on public query API returning answer text plus citation metadata for a fixture question; GREEN with fixture retriever and minimal answer composer.
- **Verify:** API/integration test proves expected fixture source appears in citations.

### Slice 1 — Live hybrid retrieval and rerank
- **Type:** AFK
- **Tracer bullet:** no
- **Delivers:** The same query path works against the live document index with reranking and stable source IDs.
- **PRD trace:** Story 1, Story 2; technical specs for retriever and reranker.
- **Depends on:** Slice 0
- **TDD note:** RED on retrieval contract against a seeded live-index fixture; GREEN with minimal index adapter.
- **Verify:** Retrieval contract tests pass for seeded corpus.

### Slice 2 — Multi-turn clarification
- **Type:** HITL
- **Tracer bullet:** no
- **Delivers:** Ambiguous questions return a clarification prompt instead of an unsupported final answer.
- **PRD trace:** Story 4; AC for ambiguous questions.
- **Depends on:** Slice 0
- **TDD note:** RED on ambiguous query fixture returning `needs_clarification`; GREEN with simple ambiguity policy.
- **Verify:** Integration test covers ambiguous and non-ambiguous query outcomes.

### Slice 3 — Code blocks with copy affordance and golden-set hook
- **Type:** AFK
- **Tracer bullet:** no
- **Delivers:** Answers can render code blocks with preserved indentation and a copy action; golden-set citation checks can run locally or in CI.
- **PRD trace:** Story 3; AI evaluation strategy.
- **Depends on:** Slice 0
- **TDD note:** RED on rendering/copy behavior and one golden-set citation case; GREEN with minimal UI and eval runner hook.
- **Verify:** UI test covers copy action; golden-set job fails if expected citations diverge.
