# Implementation increment ticketing rules

Each ticket should be one thin vertical path through all integration layers it touches. A completed increment is demoable or verifiable on its own.

## Drafting rules

- Prefer many thin increments over few thick ones.
- Use HITL when human interaction is required for a decision or review.
- Use AFK when the ticket can be implemented without additional human context.
- Populate Documentation references from `IMPLEMENTATION.md` and `PRD.md` first.
- Add `CONTEXT.md`, ADRs, and `AGENTS.md` only when exploration surfaced durable anchors.
- Use Implementation details for stable boundaries, package/module roots, test areas, and important constraints.
- Avoid long copy-paste solutions or exhaustive walkthroughs.
- Prefer citations, patterns, and short API references so the executing agent can adapt to the repo.

## Conflicts and overlaps

Use **Conflicts / overlaps** when two tickets touch the same files, migrations, APIs, feature flags, or rollout gates. Each ticket should have a unique acceptance surface. Shared regression coverage must be labeled as shared.

## Verification

Acceptance criteria are observable definitions of done. Implementation todos are execution steps. Order todos roughly by dependency within the increment and mirror TDD posture when repo conventions expect tests alongside behavior.
