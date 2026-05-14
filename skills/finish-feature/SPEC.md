# finish-feature Specification

## Intent

**finish-feature** runs after **to-tickets** work is implemented: verify the repository against **`docs/{feature-slug}/PRD.md`**, **`IMPLEMENTATION.md`** (recommended), and **all** **`docs/{feature-slug}/tickets/*.md`**, then write **`docs/{feature-slug}/IMPLEMENTED.md`** — a concise **as-built** handoff so future agents avoid inferring behavior from stale plans or guesses.

Default filename **`IMPLEMENTED.md`** pairs with **`IMPLEMENTATION.md`** (planned outline vs verified reality).

## Scope

In scope:

- Preconditions and input contract aligned with **to-tickets** paths
- Verification discipline (paths, symbols, flags, migrations, narrow test commands when safe)
- **`IMPLEMENTED.md`** section contract (`references/implemented-template.md`)
- Filename override when **`AGENTS.md`** / user convention requires another name
- Optional **`AGENTS.md`** pointer — **only when the user asks** (delegated to **agents-md**)

Out of scope:

- Creating **`PRD.md`**, **`IMPLEMENTATION.md`**, or ticket files
- Closing tracker issues or release management
- Full code audit or pen-test style review

## Users And Trigger Context

- **Primary users:** Agents and engineers post-merge on a slice
- **Common user requests:** “Feature is done”, “document what we shipped”, “as-built for `{slug}`”, “anti-assumption handoff”
- **Should not trigger for:** Incomplete tickets (unless user explicitly scopes a partial handoff — then label status accordingly in **`IMPLEMENTED.md`**)

## Runtime Contract

- **Required inputs:** **`docs/{feature-slug}/PRD.md`**; **all** **`docs/{feature-slug}/tickets/*.md`**; **`{project-root}`**
- **Recommended:** **`docs/{feature-slug}/IMPLEMENTATION.md`**
- **Required outputs:** **`docs/{feature-slug}/IMPLEMENTED.md`** (unless overridden — same folder, same template contract)
- **Non-negotiable constraints:** Verify claims against repo when possible; mark **`Unverified`** / **`Not run`** honestly; cite repo-relative anchors; document ticket-to-code drift
- **Bundled references:** **`references/implemented-template.md`**, **`references/verification-checklist.md`**

## Pipeline Position

Upstream: **to-tickets** (and typically **to-implementation**, **to-feature-prd**)  
Uses: target project repository state after implementation

## Validation

Run from repo root:

`uv run skills/skill-writer/scripts/quick_validate.py skills/finish-feature`

## Known Limitations

- Cannot substitute reading code when tickets omit paths — output will retain verification gaps.
- Verification commands depend on workspace safety and user/environment constraints; **`Not run`** is valid.
