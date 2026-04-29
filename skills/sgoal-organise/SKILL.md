---
name: sgoal-organise
description: Create .sgoal/MODULE.md for a project using the Organise phase of the SGoal planning workflow. Use when Codex needs to convert .sgoal/GOAL.md or project goals into functional modules, define module boundaries, responsibilities, interfaces, ownership areas, exclusions, shared concerns, and cross-module dependencies. Trigger on requests mentioning Organise, MODULE.md, module planning, system decomposition, module boundaries, responsibility mapping, or SGoal project structure.
---

# SGoal Organise

## Overview

Use this skill to convert `.sgoal/GOAL.md` into `.sgoal/MODULE.md`. Treat Organise as the phase that clusters goals and constraints into coherent project modules with clear boundaries.

## Workflow

1. Read `.sgoal/GOAL.md` first when it exists. If it does not exist, infer from available project context and mark assumptions.
2. Identify functional domains, user journeys, data boundaries, integration points, and operational concerns.
3. Group related responsibilities into modules. Avoid creating modules around implementation layers only, unless the project is infrastructure-first.
4. Define what each module owns and what it must not own.
5. Create or update `.sgoal/MODULE.md` unless the user specifies another location.

## Module Boundary Rules

- Give every module one primary reason to change.
- Define external interfaces and dependencies explicitly.
- Keep shared concerns visible. Do not hide auth, persistence, observability, or configuration work inside unrelated modules.
- Split a module when it has multiple unrelated user goals or data lifecycles.
- Merge modules when their boundaries require constant bidirectional coordination.

## .sgoal/MODULE.md Structure

Use this structure unless the project already has a stronger local convention:

```markdown
# Project Modules

## Source Goal
- Goal artifact: .sgoal/GOAL.md
- Planning date:
- Assumptions:

## Module Map
| Module | Purpose | Owns | Does Not Own | Key Dependencies |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

## Module Details

### Module: <name>
Purpose:

Responsibilities:
- 

Boundaries:
- Owns:
- Does not own:

Inputs:
- 

Outputs:
- 

Dependencies:
- Upstream:
- Downstream:
- Shared services:

Risks and Open Questions:
- 

## Cross-Cutting Concerns
- Authentication and authorization:
- Data model and persistence:
- Integrations:
- Observability:
- Configuration:
- Error handling:

## Boundary Decisions
- Decision:
- Reason:
- Impact:
```

## Quality Bar

- Make module boundaries testable by asking whether a feature clearly belongs in one module.
- Keep responsibilities at module granularity, not feature granularity.
- Surface ambiguous ownership as an open question instead of forcing a weak answer.
- Preserve traceability from modules back to `.sgoal/GOAL.md`.

## Handoff

End with the next recommended step:

- Use `$sgoal-distill` after `.sgoal/MODULE.md` is complete enough to derive module-level features.
- Do not create `.sgoal/FEATURE.md` or `.sgoal/ACTION.md` from this skill unless the user explicitly asks for a combined pass.
