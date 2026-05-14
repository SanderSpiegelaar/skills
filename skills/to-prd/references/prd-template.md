# Parent PRD template

Use this structure for `docs/{initiative-slug}/PRD.md`.

```markdown
# [Initiative title]

| Field | Value |
|-------|-------|
| **Status** | Draft / Approved / Superseded |
| **Owner** | [person/team or TBD] |
| **Last updated** | [YYYY-MM-DD] |
| **Source** | [conversation / issue / doc / link] |
| **Initiative slug** | `docs/{initiative-slug}/PRD.md` |

### 1. Executive summary

- **Problem statement**: 1–2 sentences on the pain point.
- **Proposed solution**: 1–2 sentences on the fix.
- **Success criteria**: 3–5 measurable KPIs.

### 2. User experience and functionality

- **User personas**: Who is this for?
- **User stories**: `As a [user], I want to [action] so that [benefit].` Provide a numbered list that covers the feature thoroughly.
- **Acceptance criteria**: Bulleted "done" definitions per story, or grouped by story.

### 3. Non-goals

What we are not building. Include adjacent ideas that are easy to confuse with this initiative.

### 4. AI system requirements (if applicable)

- **Tool requirements**: Tools and APIs the system needs.
- **Evaluation strategy**: How to measure output quality and accuracy.

### 5. Technical specifications

- **Architecture overview**: Data flow and component interaction.
- **Integration points**: APIs, databases, auth.
- **Security and privacy**: Data handling and compliance.

#### Implementation decisions

Capture decisions here. Avoid file paths or generic code snippets that go stale:

- Modules built or modified; interfaces that change
- Technical clarifications, architecture, schema, API contracts, important interactions

**Exception:** If a prototype encodes a decision more precisely than prose, inline only the decision-rich fragment and note it came from a prototype.

### 6. Testing and validation

- What makes a good test here: external behavior, not implementation details.
- Which modules are in scope for automated tests.
- Prior art: similar tests elsewhere in the codebase.
- For AI: tie to evaluation strategy in section 3.

### 7. Risks and roadmap

- **Phased rollout**: e.g. MVP -> v1.1 -> v2.0.
- **Technical risks**: Latency, cost, dependency or vendor failure.

### 8. Open questions

- **TBD:** [question, owner if known, and why it matters]

### 9. Further notes

Any additional context that does not fit above.
```
