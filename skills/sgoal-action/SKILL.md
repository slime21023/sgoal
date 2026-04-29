---
name: sgoal-action
description: Create .sgoal/ACTION.md for a project using the Action phase of the SGoal planning workflow. Use when Codex needs to prioritize features from .sgoal/FEATURE.md, clarify feature dependencies, identify development order, define increments, expose blockers, sequence MVP work, and produce an actionable implementation roadmap. Trigger on requests mentioning Action, ACTION.md, feature priority, development order, dependency mapping, roadmap, sequencing, MVP planning, or SGoal delivery planning.
---

# SGoal Action

## Overview

Use this skill to convert `.sgoal/FEATURE.md` into `.sgoal/ACTION.md`. Treat Action as the delivery planning phase: converge on a practical order of work, explain dependencies, and make the next development moves clear.

## Workflow

1. Read `.sgoal/FEATURE.md` first when it exists. Read `.sgoal/MODULE.md` and `.sgoal/GOAL.md` as supporting context when available.
2. Extract feature dependencies, enabling work, user value, risk, and implementation uncertainty.
3. Build a dependency-aware order. Do not prioritize high-value features ahead of prerequisites unless the dependency can be deliberately mocked or deferred.
4. Define delivery increments that can be built and validated.
5. Create or update `.sgoal/ACTION.md` unless the user specifies another location.

## Prioritization Rubric

Use this rubric unless the user provides another one:

- Dependency: prerequisites before dependents.
- Goal impact: features closest to the project objective move earlier.
- Learning value: risky unknowns move earlier when they can invalidate the plan.
- Delivery value: visible or testable slices beat hidden bulk work.
- Effort: prefer smaller slices when impact and dependency position are similar.

## .sgoal/ACTION.md Structure

Use this structure unless the project already has a stronger local convention:

```markdown
# Project Action Plan

## Source Artifacts
- Goal artifact: .sgoal/GOAL.md
- Module artifact: .sgoal/MODULE.md
- Feature artifact: .sgoal/FEATURE.md
- Planning date:

## Dependency Map
| Feature ID | Feature | Depends On | Enables | Notes |
| --- | --- | --- | --- | --- |
| F-001 |  |  |  |  |

## Priority Order
| Order | Feature ID | Feature | Reason | Risk | Estimated Size |
| --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  |

## Delivery Increments

### Increment 1: <name>
Goal:

Features:
- 

Validation:
- 

Exit Criteria:
- 

### Increment 2: <name>
Goal:

Features:
- 

Validation:
- 

Exit Criteria:
- 

## Blockers and Decisions Needed
- Blocker:
- Impact:
- Owner or decision needed:

## Deferred Features
- Feature ID:
- Reason deferred:
- Revisit trigger:

## Immediate Next Actions
1. 
2. 
3. 
```

## Quality Bar

- Explain why the first three items come first.
- Keep dependency claims traceable to `.sgoal/FEATURE.md`.
- Separate blockers from merely low-priority work.
- Prefer vertical slices that can be validated over broad phase labels.
- Include enough immediate actions for an engineer to start without re-planning.

## Handoff

End with the concrete next development action and the artifact path for `.sgoal/ACTION.md`.
