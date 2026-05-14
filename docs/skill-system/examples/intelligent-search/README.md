# Intelligent search golden example

This directory shows one complete artifact chain for the core workflow. It is intentionally small, but each file traces to the previous artifact.

| Artifact | Produced by | Purpose |
|----------|-------------|---------|
| [`parent-prd.md`](parent-prd.md) | `to-prd` | Parent initiative PRD, equivalent to `docs/intelligent-search/PRD.md` in a target repo |
| [`vertical-slices.md`](vertical-slices.md) | `to-features` | Ordered vertical slices from the parent PRD |
| [`slice-prd.md`](slice-prd.md) | `to-feature-prd` | Slice-scoped PRD, equivalent to `docs/tracer-qa-path/PRD.md` |
| [`implementation.md`](implementation.md) | `to-implementation-doc` | Ticket-ready vertical increments |
| [`tickets/01-fixture-retrieval-answer.md`](tickets/01-fixture-retrieval-answer.md) | `to-tickets` | First executable implementation ticket |
| [`tickets/02-citation-rendering.md`](tickets/02-citation-rendering.md) | `to-tickets` | Second executable implementation ticket |
| [`implemented.md`](implemented.md) | `finish-feature` | Verified as-built handoff example |

Use this pack as a style example, not as a product requirement. Real project artifacts should keep the same traceability shape while adapting details to the repository.
