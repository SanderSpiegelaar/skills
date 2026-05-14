# tdd Specification

## Intent

**tdd** implements features or fixes through RED-GREEN-REFACTOR. When invoked from the core workflow, it consumes one ticket under `docs/{feature-slug}/tickets/` plus referenced PRD and implementation docs.

## Scope

In scope:

- Reading ticket context and referenced docs before implementation
- One behavior-focused RED test at a time
- Minimal GREEN implementation
- Refactoring only while tests are green
- Handoff to `finish-feature` after all tickets are complete

Out of scope:

- Writing all tests before implementation
- Verifying private implementation details as the main test strategy
- Editing ticket checkboxes when project conventions do not allow planning-doc updates

## Runtime Contract

- **Preferred input:** one implementation ticket plus referenced `PRD.md` and `IMPLEMENTATION.md`
- **Required outputs:** passing behavior-focused tests and minimal implementation
- **Non-negotiable constraints:** tests verify public behavior; never refactor while RED; do not speculate beyond the current behavior

## Source And Evidence Model

Authoritative sources:

- Assigned ticket
- Referenced `docs/{feature-slug}/PRD.md`
- Referenced `docs/{feature-slug}/IMPLEMENTATION.md`
- Relevant `CONTEXT.md`, ADRs, and repo test conventions
- `references/` guidance for tests, mocking, interfaces, refactoring, deep modules, and horizontal-slice avoidance

## Validation

- `SKILL.md` frontmatter is valid and links resolve.
- Ticket-driven input contract is present.
- RED-GREEN-REFACTOR loop remains one behavior at a time.
- Handoff to `finish-feature` is explicit.

## Maintenance Notes

- Update this SPEC when TDD workflow, ticket input policy, checkbox policy, or reference set changes.
