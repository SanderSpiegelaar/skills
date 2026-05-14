---
name: ticket-researcher
description: Reads implementation tickets, interviews the user for research direction, then uses web search (exa) and documentation lookup (context7) to expand the ticket with technical context, examples, and implementation notes. Use when a ticket is too thin to execute, when user says "research this ticket", "expand this ticket", or when a ticket lacks technical detail, library choices, or code examples.
---

# Ticket Researcher

## Quick start

1. Read the ticket file path the user provides
2. Identify gaps: missing libraries, patterns, API choices, or code examples
3. If needed: Ask user 2–4 targeted research questions
4. Run `exa_web_search_exa` and `context7` lookups in parallel
5. Append a `## Technical research` section with findings, tables, and code snippets
6. Update `Status:` to `ready-for-agent` when done

## Workflow

### 1. Read ticket

Read the ticket. Extract:
- What to build
- Acceptance criteria
- Any existing research links or parent PRDs

Flag gaps: no library versions? no code examples? no rationale for choices?

### 2. Interview user

Ask 2–4 concise questions to narrow research scope. Examples:
- "Any preferred libraries for X, or should I research current best options?"
- "Do you want copy-pasteable code examples or just rationale?"
- "Should I check compatibility with our existing stack (Tauri v2, Svelte 5, etc.)?"
- "Any specific docs to search (e.g., tokio.rs, docs.rs)?"

### 3. Research

Parallel calls:
- `exa_web_search_exa` for real-world usage patterns, recent articles, version recommendations
- `context7` (or `librarian` / `webfetch`) for official API docs, crate docs, framework guides

Index findings with `ctx_index` for reference while writing.

### 4. Expand ticket

Append a `## Technical research` section containing:

- **Why each choice** — table mapping decision → rationale
- **Code examples** — minimal working snippets for the ticket's domain
- **Integration notes** — how it fits existing stack (Tauri, Svelte, SQLite, etc.)
- **Gotchas / risks** — version conflicts, known issues, migration steps
- **Testing notes** — how to verify the change

Keep examples concrete. Use project paths and existing module names where known.

### 5. Update status

Set `Status: ready-for-agent` if the ticket now has enough context to execute.

## Rules

- Never delete existing ticket content — only append
- Keep `## Technical research` under ~150 lines; link to `EXAMPLES.md` or `REFERENCE.md` if it grows
- If no research is needed, tell user and stop — don't inflate
- Always cite sources: link URLs or doc pages in findings
