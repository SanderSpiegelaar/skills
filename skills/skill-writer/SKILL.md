---
name: skill-writer
description: Create, synthesize, and iteratively improve agent skills following the Agent Skills specification. Use when asked to create a skill, write a skill, synthesize sources into a skill, improve a skill from examples or outcomes, update a skill, or maintain skill docs and registration.
---

# Skill Writer

## Quick start

Input: a requested skill capability, existing source material, or feedback about a current skill.

Output: a concise `SKILL.md` plus references, scripts, examples, `SPEC.md`, and registration updates when needed.

Use this skill as a router: load only the reference files needed for the current authoring shape.

## Workflow

1. **Resolve target and shape.** Determine skill name, install path, host conventions, trigger description, and whether this is a new skill or update. See [`references/authoring-path.md`](references/authoring-path.md).
2. **Select execution shape.** Pick inline, reference-backed, script-backed, argument-driven, or asset-template layout from [`references/execution-shapes.md`](references/execution-shapes.md).
3. **Synthesize or iterate.** For source synthesis use [`references/synthesis-path.md`](references/synthesis-path.md). For outcome/example improvement use [`references/iteration-path.md`](references/iteration-path.md).
4. **Author artifacts.** Keep `SKILL.md` concise and move optional detail into `references/`. Use templates under the **Artifact Layout References** below.
5. **Add scripts only for deterministic work.** Use scripts for validation, formatting, generation, or repeated error-prone logic.
6. **Create or update `SPEC.md`.** Use [`references/spec-template.md`](references/spec-template.md) when creating a new skill or materially changing behavior.
7. **Validate.** Run `uv run skills/skill-writer/scripts/quick_validate.py skills/<skill-folder>` when available, then inspect links and frontmatter.
8. **Report.** Summarize changed files, remaining open questions, and validation results.

## Output contract

- Frontmatter includes `name` and a trigger-rich `description`.
- `SKILL.md` is the short entrypoint; references are one level deep where practical.
- Bundled scripts are deterministic and documented by the skill.
- Examples, templates, or schemas are included when they prevent repeated generated prose.
- Registration or marketplace metadata is updated only when the repo uses it.

## Core Workflow References

- Authoring: [`authoring-path.md`](references/authoring-path.md), [`source-discovery.md`](references/source-discovery.md), [`synthesis-path.md`](references/synthesis-path.md), [`source-adaptation.md`](references/source-adaptation.md)
- Iteration: [`iteration-path.md`](references/iteration-path.md), [`iteration-evidence.md`](references/iteration-evidence.md), [`structure-troubleshooting.md`](references/structure-troubleshooting.md)
- Design: [`design-principles.md`](references/design-principles.md), [`description-optimization.md`](references/description-optimization.md), [`reference-architecture.md`](references/reference-architecture.md)
- Validation: [`registration-validation.md`](references/registration-validation.md), [`output-contracts.md`](references/output-contracts.md), [`spec-template.md`](references/spec-template.md)

## Artifact Layout References

- [`layout-inline-skill.md`](references/layout-inline-skill.md)
- [`layout-reference-backed-skill.md`](references/layout-reference-backed-skill.md)
- [`layout-script-backed-workflow.md`](references/layout-script-backed-workflow.md)
- [`layout-argument-driven-skill.md`](references/layout-argument-driven-skill.md)
- [`layout-asset-template-skill.md`](references/layout-asset-template-skill.md)

## Workflow Mechanic References

- [`workflow-plan-validate-execute.md`](references/workflow-plan-validate-execute.md)
- [`workflow-prompt-chaining.md`](references/workflow-prompt-chaining.md)
- [`workflow-routing.md`](references/workflow-routing.md)
- [`workflow-orchestrator-workers.md`](references/workflow-orchestrator-workers.md)
- [`workflow-parallel.md`](references/workflow-parallel.md)
- [`workflow-validation-loops.md`](references/workflow-validation-loops.md)

## Example Profiles

- [`example-workflow-process-skill.md`](references/example-workflow-process-skill.md)
- [`example-documentation-skill.md`](references/example-documentation-skill.md)
- [`example-router-skill.md`](references/example-router-skill.md)
- [`example-hook-backed-skill.md`](references/example-hook-backed-skill.md)
- [`example-subagent-fork-skill.md`](references/example-subagent-fork-skill.md)

## Related References

- Claude Code compatibility: [`claude-frontmatter-invocation.md`](references/claude-frontmatter-invocation.md), [`claude-argument-substitutions.md`](references/claude-argument-substitutions.md), [`claude-dynamic-context.md`](references/claude-dynamic-context.md), [`claude-hook-backed.md`](references/claude-hook-backed.md), [`claude-subagent-fork.md`](references/claude-subagent-fork.md)
- Mode selection: [`mode-selection.md`](references/mode-selection.md)
