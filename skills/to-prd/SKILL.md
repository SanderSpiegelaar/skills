---
name: to-prd
description: Turn conversation context or a greenfield idea into a production-grade parent PRD at docs/{initiative-slug}/PRD.md. Use when the user wants a PRD from context, wants to document requirements, plan a feature, scope AI-powered work, or create a durable source for feature slicing; issue-tracker publication is optional when explicitly requested.
---

# To PRD

## Quick start

- **Input:** Idea, conversation context, or grilled plan.
- **Do:** Ask missing product/technical questions and write the parent PRD.
- **Output:** `docs/{initiative-slug}/PRD.md`.
- **Next:** Run **to-features**.

## Workflow

1. **Choose discovery depth.** For thin context, interview fully. For rich context, ask only 0-3 targeted questions where a section would otherwise be guessed or must stay `TBD`.
2. **Use structured questions.** Whenever you need answers or choices, use the host's **Ask User Question** tool when available; otherwise ask clearly numbered questions in chat.
3. **Read domain context.** If `CONTEXT.md` or `CONTEXT-MAP.md` exists, read relevant context before naming concepts, user stories, or technical boundaries. If the PRD introduces durable vocabulary, update `CONTEXT.md` when authorized or flag the suggested glossary update.
4. **Ask about essentials.** Cover core problem, success metrics, constraints, user flow, non-goals, dependencies, hidden complexity, AI evaluation, compliance, and testing scope as applicable.
5. **Draft the PRD.** Use [`references/prd-template.md`](references/prd-template.md). Follow the quality bar in [`references/requirements-quality.md`](references/requirements-quality.md).
6. **Resolve `{initiative-slug}`.** Use lowercase kebab-case ASCII derived from the initiative title unless the user provides a slug.
7. **Write the file.** Persist the approved PRD to `docs/{initiative-slug}/PRD.md`.
8. **Publish only on request.** If the user explicitly asks for tracker publication, publish and apply `ready-for-agent`; no extra triage pass required.
9. **Confirm handoff.** Report the path, remaining `TBD`s, and **to-features** as the next step.

## Output contract

The PRD must include:

- Executive summary with problem, solution, and success criteria.
- User personas, user stories, acceptance criteria, and non-goals.
- AI system requirements when applicable.
- Technical specifications and implementation decisions.
- Testing and validation strategy.
- Risks, phased rollout, and further notes.

Use concrete, measurable requirements. Avoid vague words like "fast", "easy", or "intuitive" unless they are backed by measurable criteria.

## References

- [`references/workflow-contract.md`](references/workflow-contract.md) — portable artifact hierarchy and handoff chain.
- [`references/prd-template.md`](references/prd-template.md) — canonical parent PRD template.
- [`references/requirements-quality.md`](references/requirements-quality.md) — vague vs concrete requirements guidance.
- [`references/example-intelligent-search.md`](references/example-intelligent-search.md) — longer worked example.
- [`references/example-parent-prd.md`](references/example-parent-prd.md) — golden parent PRD example.

## Related skills

- **grill** — sharpen domain language and decisions before the PRD.
- **to-features** — decompose this parent PRD into vertical slices.
- **setup-skills** — configures optional tracker publication and domain-doc locations.
