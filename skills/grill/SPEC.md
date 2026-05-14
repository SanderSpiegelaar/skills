# grill Specification

## Intent

**grill** is the pre-PRD interrogation skill. It challenges plans against repository truth, domain vocabulary, ADRs, code behavior, and external facts when needed. Its durable output is sharper decisions, `CONTEXT.md` vocabulary, and ADRs when a decision warrants one.

## Scope

In scope:

- Structured decision questioning after repo/document exploration
- `CONTEXT.md` updates for resolved domain vocabulary
- ADR offers for hard-to-reverse, surprising, trade-off decisions
- Handoff to `to-prd` when the plan is ready to formalize

Out of scope:

- Writing parent PRDs directly
- Writing implementation tickets
- Treating `CONTEXT.md` as an implementation spec

## Runtime Contract

- **Required first actions:** read relevant `CONTEXT.md` / `CONTEXT-MAP.md`, ADRs, and code before asking questions that repo truth can answer
- **Question protocol:** use structured questions when available; include recommended options only when evidence supports them
- **Required outputs:** clarified decisions in chat plus immediate doc updates when the user authorizes them
- **Non-negotiable constraints:** never fabricate paths, commands, or behavior to make options look informed

## Validation

- `SKILL.md` retains research-before-question behavior.
- `CONTEXT.md` remains glossary-only.
- ADR criteria remain strict.
- Handoff to `to-prd` is explicit.

## Maintenance Notes

- Update this SPEC when grilling scope, question protocol, context-authoring rules, or ADR criteria change.
