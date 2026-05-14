# Vertical increment rules

Use many thin vertical cuts over one thick milestone.

- Increment 0 should be the smallest end-to-end path that proves wiring and one testable behavior when the PRD implies a tracer bullet.
- Each increment must map to acceptance criteria or requirements in `PRD.md`.
- Each increment should be demoable or verifiable on its own.
- Avoid horizontal layer-only plans such as all schema first, then all API, then all UI.
- Keep the outline high-level: it should seed tickets, not script implementation.

When `CONTEXT.md` / `CONTEXT-MAP.md` or ADRs exist, use their vocabulary for boundaries and integration touchpoints. Flag suggested `CONTEXT.md` updates when the outline sharpens durable domain language.

## Handoff rule

Use `to-tickets` with `PRD.md + IMPLEMENTATION.md`. Each ticket maps to one tracer-bullet implementation increment.
