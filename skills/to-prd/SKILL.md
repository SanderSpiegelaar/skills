---
name: to-prd
description: Turn conversation context or a greenfield idea into a production-grade PRD (executive summary, user stories with acceptance criteria, technical specs, AI requirements when applicable, risks) and publish it to the project issue tracker. Use when the user wants a PRD from context, wants to document requirements, plan a feature, or scope AI-powered work.
---

# To PRD

Design comprehensive PRDs that bridge business intent and technical execution—for modern software and AI-powered features. The issue tracker and triage label vocabulary should have been provided; run `/setup-skills` if not.

## When to use

- Starting a new product or feature cycle, or translating a vague idea into a concrete specification
- Defining requirements for AI-powered features
- Turning **current conversation context** into a tracker-backed PRD stakeholders can treat as scope
- Stakeholders need a single source of truth for scope
- User asks to write a PRD, document requirements, or plan a feature

## Requirements quality

Use concrete, measurable criteria. Avoid "fast", "easy", or "intuitive".

```diff
# Vague (BAD)
- The search should be fast and return relevant results.
- The UI must look modern and be easy to use.

# Concrete (GOOD)
+ The search must return results within 200ms for a 10k record dataset.
+ The search algorithm must achieve >= 85% Precision@10 in benchmark evals.
+ The UI must follow the 'Vercel/Next.js' design system and achieve 100% Lighthouse Accessibility score.
```

## Process

### Question protocol

Whenever you need answers or choices from the user during this skill—including discovery, gap-fill, module confirmation, or scoped feedback on a draft—**always use the Ask User Question tool** (the structured question UI). Do **not** rely on burying questions in plain chat when that tool is available: it keeps options explicit and responses easy to track. If the host has no equivalent tool, fall back to clearly numbered questions in messages.

### Context-aware discovery

Before drafting, decide how much discovery you need:

- **Thin context** (vague idea, new thread, or explicit greenfield PRD): run **Phase 1–2** below in full. Ask about the core problem, success metrics, and constraints; map user flow and non-goals. Do not assume unstated context.
- **Rich context** (ongoing technical conversation and repo understanding): **do not** force a full interview. Ask **0–3 targeted questions** only where a section would otherwise be guessed or must stay `TBD` (e.g. KPIs, deadlines, AI evaluation, compliance).

### Phase 1: Discovery (the interview, when needed)

Use **Ask User Question** for each discovery round (you can batch related topics into one form when the tool allows multiple questions).

**Ask about (as applicable):**

- **The core problem**: Why build this now?
- **Success metrics**: How do we know it worked?
- **Constraints**: Budget, tech stack, deadline, compliance?

### Phase 2: Analysis and scoping

- Map the **user flow**.
- Define **non-goals** to protect the timeline.
- Identify dependencies and hidden complexity.

### Phase 3: Drafting and publication

1. Explore the repo if you have not already. Use the project's domain glossary and respect ADRs in the areas you touch.

2. Sketch the major modules to build or modify. Prefer **deep modules**: a lot of functionality behind a simple, stable, testable interface.

3. Check with the user that the module breakdown matches their expectations. Confirm which modules should have tests—use **Ask User Question** for these confirmations.

4. Write the PRD using the template below. Iterate: share a draft and invite feedback on specific sections when helpful.

5. Publish to the project issue tracker. Apply the **`ready-for-agent`** triage label—no additional triage pass required.

## Implementation guidelines

### DO

- **Define testing**: For AI systems, specify how to validate output quality and accuracy.
- **Iterate**: Present a draft and ask for feedback on specific sections when useful; use **Ask User Question** when offering section-level choices or next-step options.

### DON'T

- **Skip discovery when context is thin**: Do not write a full PRD without filling obvious gaps (problem, success bar, constraints)—ask or mark `TBD`.
- **Hallucinate constraints**: If the user did not specify stack, budget, or dates, ask or label **`TBD`**.

## Example (trimmed)

See [references/example-intelligent-search.md](references/example-intelligent-search.md) for a longer worked example.

**Executive summary (excerpt):** Problem—finding snippets in large doc repos; solution—NL search with citations; success—50% faster task time, citation accuracy ≥ 95%.

**User story (excerpt):** As a developer, I want to ask natural-language questions so I do not have to guess keywords. **AC:** multi-turn clarification; code blocks with a clear copy affordance.

**AI (excerpt):** Tools: code search, grep, web fetch. Eval: 50 benchmark questions, 90% citation match to expected sources.

<prd-template>

### 1. Executive summary

- **Problem statement**: 1–2 sentences on the pain point.
- **Proposed solution**: 1–2 sentences on the fix.
- **Success criteria**: 3–5 measurable KPIs.

### 2. User experience and functionality

- **User personas**: Who is this for?
- **User stories**: `As a [user], I want to [action] so that [benefit].` Provide a **long, numbered list** that covers the feature thoroughly.
- **Acceptance criteria**: Bulleted "done" definitions per story (or grouped by story).
- **Non-goals**: What we are **not** building (out of scope).

### 3. AI system requirements (if applicable)

- **Tool requirements**: Tools and APIs the system needs.
- **Evaluation strategy**: How to measure output quality and accuracy.

### 4. Technical specifications

- **Architecture overview**: Data flow and component interaction.
- **Integration points**: APIs, databases, auth.
- **Security and privacy**: Data handling and compliance.

#### Implementation decisions

Capture decisions here (no file paths or generic code snippets—they go stale):

- Modules built or modified; interfaces that change
- Technical clarifications, architecture, schema, API contracts, important interactions

**Exception:** If a prototype encodes a decision more precisely than prose (state machine, reducer, schema, type shape), inline only the decision-rich fragment and note it came from a prototype.

### 5. Testing and validation

- What makes a **good test** here (external behavior, not implementation details).
- **Which modules** are in scope for automated tests.
- **Prior art**: similar tests elsewhere in the codebase.
- For AI: tie to evaluation strategy in section 3.

### 6. Risks and roadmap

- **Phased rollout**: e.g. MVP → v1.1 → v2.0.
- **Technical risks**: Latency, cost, dependency or vendor failure.

### 7. Further notes

Any additional context that does not fit above.

</prd-template>
