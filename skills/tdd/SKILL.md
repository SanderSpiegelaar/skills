---
name: tdd
description: Test-driven development with red-green-refactor loop. Use when user wants to build features or fix bugs using TDD, mentions red-green-refactor, wants integration tests, asks for test-first development, or is implementing a ticket from docs/{feature-slug}/tickets/.
---

# Test-Driven Development

## Quick start

- **Input:** One ticket plus referenced PRD/implementation docs.
- **Do:** Implement one behavior at a time through RED-GREEN-REFACTOR.
- **Output:** Passing behavior-focused tests and minimal implementation.
- **Next:** Continue tickets, then run **finish-feature**.

## Workflow

1. **Read ticket context when present.** Start with the assigned ticket, referenced `docs/{feature-slug}/PRD.md`, referenced `docs/{feature-slug}/IMPLEMENTATION.md`, relevant `CONTEXT.md` / `CONTEXT-MAP.md`, and ADRs.
2. **Plan behavior, not internals.** Confirm the public interface and highest-value observable behaviors. Use structured questions when choices are blocking.
3. **Avoid horizontal slicing.** Do not write all tests first and then all implementation. See [`references/horizontal-slices.md`](references/horizontal-slices.md).
4. **Write one RED test.** The test must describe behavior through a public interface and fail for the expected reason.
5. **Go GREEN minimally.** Add only enough implementation to pass the current test.
6. **Repeat one behavior at a time.** Each next test should respond to what the previous cycle revealed.
7. **Refactor only while green.** Use [`references/refactoring.md`](references/refactoring.md); run tests after each refactor step.
8. **Update planning docs cautiously.** Update ticket checkboxes only when project convention allows editing planning docs.
9. **Handoff when complete.** After all tickets under `docs/{feature-slug}/tickets/` are complete and verified, recommend [finish-feature](../finish-feature/SKILL.md).

## Output contract

- Tests verify behavior through public interfaces, not implementation details.
- Each RED -> GREEN cycle covers one behavior.
- Implementation stays minimal until a passing test justifies more.
- Refactors preserve behavior and keep tests green.

## References

- [`references/tests.md`](references/tests.md) — good test examples.
- [`references/mocking.md`](references/mocking.md) — mocking guidelines.
- [`references/interface-design.md`](references/interface-design.md) — testable interface design.
- [`references/deep-modules.md`](references/deep-modules.md) — small interface, deep implementation.
- [`references/refactoring.md`](references/refactoring.md) — refactor candidates and rules.
- [`references/horizontal-slices.md`](references/horizontal-slices.md) — anti-pattern details.

## Related skills

- **to-tickets** — provides executable ticket input.
- **finish-feature** — verifies shipped tickets and writes `IMPLEMENTED.md`.
