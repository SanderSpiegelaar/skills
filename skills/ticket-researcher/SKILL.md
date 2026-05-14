---
name: ticket-researcher
description: Reads an implementation ticket, interviews the user to narrow scope, then enriches it with citations-first technical research (libraries, patterns, gotchas, testability) via web search and official-docs lookup — optional minimal API-shape notes, not screenplay-length code. Use when user says “research this ticket”, “expand this ticket”, when a ticket is too thin to execute cleanly, lacks library/stack guidance, or needs upstream doc refreshes aligned with **to-tickets** engineering-context expectations.
---

# Ticket Researcher

Optional **deepening pass** after a ticket exists (for example files from [**to-tickets**](../to-tickets/SKILL.md)). Aligns appended output with the **Implementation details** sections in that skill’s template: decisions → integration/patterns → risks → verification/testability → **minimal** shapes only where needed.

## Quick start

1. Read the ticket path the user provides.
2. List **gaps** that would block senior-level execution: unclear library/stack choices; missing pinning or compat notes; unexplained integration boundaries; vague **test seams** / verification paths; contradictory or absent risk notes. **Do not** treat “no copy-paste code” as a gap by itself — prose plus **cited docs** often suffice.
3. If needed: ask **2–4** concise research-scoping questions (see Interview).
4. In parallel where possible: **web search** (patterns, compatibility, deprecations) **and** **official documentation lookup** (your environment’s doc MCP, doc fetch, or similar — e.g. Exa web search + Context7-class tools when configured).
5. Append **`## Technical research`** using the structure in **Expand ticket**. Default to **patterns, pitfalls, citations** — snippets only when API shape stays ambiguous after docs are linked.

Use whatever tool names your MCP or IDE exposes; if a tool is unavailable, skip it and note the gap briefly.

## Workflow

### 1. Read ticket

Read the ticket. Extract:

- What to build
- Acceptance criteria
- Existing documentation references, traceability, **Engineering context** material (from **to-tickets**) if present
- Verification / test hints already stated

Flag **real gaps** — examples:

| Gap type | Signals |
|---------|---------|
| Libraries / pinning | Candidates missing; version or breaking-change posture unclear |
| Patterns / boundaries | No idioms matched to repo stack; layering or seams unclear |
| Testability | No test seams or suite hooks; verification hand-wavy vs AC |
| Risks | High-impact foot-guns undocumented (migrations, async, FFI, semver) |

**Do not:** require “code examples sections” before calling the ticket workable; inflated snippets can **limit** the executing agent.

### 2. Interview user

Ask **2–4** targeted questions when scope is ambiguous. Tailor to gaps; examples:

- “Preferred libraries/constraints vs open research for X?”
- “Pin to existing lockfile/stack (name versions)?”
- “Depth: doc links + patterns only, or one minimal shape where API is ambiguous?”
- “Any must-read canonical docs URLs or internal ADRs?”

Drop the framing “copy-paste vs rationale” unless the user chooses explicit snippets.

### 3. Research

Use tools appropriate to **your runtime**:

- **Web search** — field reports, deprecation notices, version matrix discussions, idiomatic patterns  
- **Official docs MCP or fetch** — API contracts, correctness constraints, authoritative migration guides  
- If your workspace offers **bookmark/index helpers** *(e.g. `ctx_index`)* — use them only to organize citations while drafting; they are optional

Parallelize independent lookups. Prefer **canonical links** over long quoted blocks.

### 4. Expand ticket

**Append only** — never delete upstream content. Append **`## Technical research`** mirroring [**to-tickets**](../to-tickets/SKILL.md) **Implementation details** flow:

1. **Decisions — table mapping choice → rationale** (with doc links / release-note URLs)
2. **Patterns & integration** — how idioms attach to layers/modules named in the ticket (project-relative paths where known); **no** scripted full implementations
3. **Gotchas / risks** — version conflicts, concurrency/IO traps, migrations, semver landmines *(deepen ticket’s Key risks section, don’t duplicate emptily)*
4. **Verification & testability** — concrete suites/commands, seams (time, IO, RNG), properties tied to AC — **instructional**, not pasted test bodies
5. **API shape / pseudocode (optional)** — at most **short** illustrative fragments **only if** ambiguity remains **after** links; prefix with language + “adapt to codebase” disclaimer

Prefer bullet lists and compact tables over prose dumps. Tie every non-obvious claim to a **linked** source where practical.

### 5. Update status

If tickets carry **`Status:`** frontmatter or a summary line convention, set **`ready-for-agent`** once decisions, risks, verification, and test seams are actionable **without** depending on pasted production code blocks.

---

## Rules

- **Append-only:** never strip existing narrative; integrate by reference (“see subsection X above”).
- **`## Technical research` length:** aim **≤ ~150 lines**; spill long tables or rare deep dives into **`REFERENCE.md`** / sibling files and link from this section **only when the user/repo uses that pattern**.
- **Avoid inflation:** stop if gaps are imaginary; summarize “no external research warranted” briefly.
- **Citations mandatory** for portability claims or version-sensitive advice (URLs / doc headings).
- **Snippet stance:** aligns with [**to-tickets**](../to-tickets/SKILL.md) **snippet policy** — links + rationale first; snippets last resort.

## Related skills

- **to-tickets** — authoring numbered slice tickets plus **Engineering context** template baseline ([SKILL](../to-tickets/SKILL.md)).
