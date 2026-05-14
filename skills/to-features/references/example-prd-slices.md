# Example: PRD → vertical slices (intelligent search)

Worked example keyed to [to-prd example-intelligent-search.md](../../to-prd/references/example-intelligent-search.md). Illustrates **Slice 0** as tracer bullet and **0-based** dependency ids.

```markdown
# Vertical feature slices (TDD order)

**PRD source:** conversation / to-prd reference (intelligent search excerpt)

Order: Slice 0 Slice 1 Slice 2 Slice 3

### Slice 0 — Tracer Q&A path with fixture retrieval
- **Type:** AFK
- **Tracer bullet:** yes
- **Delivers:** User submits one natural-language question via the primary UI/API surface and receives a synthesized answer that includes at least one citation, using a **deterministic fixture** retriever (no production index yet) so the full request path and test harness are proven.
- **PRD trace:** Stories 1–2 (minimal); AC “every answer includes at least one citation when factual claims are made” (satisfied for a controlled fixture corpus).
- **Depends on:** None
- **TDD note:** RED: “ask returns answer+citation against fixture”; GREEN: thinnest wiring from entrypoint → synthesizer with citation constraint on stubbed chunks.
- **Verify:** One integration-style test exercises the public API or UI flow; latency not in scope for this slice.

### Slice 1 — Live hybrid retrieval and rerank
- **Type:** AFK
- **Tracer bullet:** no
- **Delivers:** Same UX as Slice 0, but retrieval uses the real doc index (keyword + dense + rerank per PRD architecture) before synthesis; answers still citation-backed for factual claims.
- **PRD trace:** Stories 1–2; technical “hybrid retrieval → rerank → LLM synthesis”; testing “contract tests on retrieval API”.
- **Depends on:** Slice 0
- **TDD note:** Replace fixture with real adapter behind the same interface; RED on retrieval contract / ranking invariants; GREEN minimal adapter + one path through rerank.
- **Verify:** Retrieval API contract tests pass; tracer test updated or duplicated for live index (golden micro-corpus acceptable).

### Slice 2 — Multi-turn clarification
- **Type:** AFK
- **Tracer bullet:** no
- **Delivers:** When the query is ambiguous, the system enters a clarification loop and only then synthesizes an answer with citations.
- **PRD trace:** Story 1 AC “multi-turn clarification when ambiguous.”
- **Depends on:** Slice 1
- **TDD note:** RED on conversation state + “clarify then answer” behavior; GREEN smallest state machine or session model without speculative extras.
- **Verify:** Scenario test: vague query → clarifying prompt → refined answer with citations.

### Slice 3 — Code blocks with copy affordance + golden-set hook
- **Type:** AFK
- **Tracer bullet:** no
- **Delivers:** Answers can surface code blocks with an explicit copy control and preserved indentation; CI or local script can run golden-set citation regression from PRD §3/§5.
- **PRD trace:** Story 3; AC on copy + indentation; testing “golden-set regression for end-to-end answer + citation quality.”
- **Depends on:** Slice 1
- **TDD note:** RED on rendering/interaction for code blocks; RED on golden-set harness entrypoint; GREEN minimal UI + one golden case (expand set later).
- **Verify:** UI/integration checks copy action; golden-set job fails if citation set diverges from expected for fixture questions.
```

**Why this order:** Slice 0 establishes the **tracer** before the heavier index work. Slice 1 swaps in real retrieval without adding conversation or UI flourishes. Slice 2 layers ambiguous-query behavior on a working single-turn stack. Slice 3 bundles presentation + eval hook; it depends on Slice 1 (not 2) so copy affordance need not wait for multi-turn unless product ties them — here they stay independent after the shared RAG path exists.
