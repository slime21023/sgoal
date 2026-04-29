---
name: sgoal-distill
description: Create .sgoal/FEATURE.md for a project using the Distill phase of the SGoal planning workflow. Use when Codex needs to turn .sgoal/MODULE.md into module-level subfeatures, clarify user-visible behavior, acceptance criteria, edge cases, data needs, non-functional requirements, and readiness questions before sequencing implementation. Trigger on requests mentioning Distill, FEATURE.md, feature breakdown, subfeatures, acceptance criteria, module features, or SGoal feature definition.
---

# SGoal Distill

## Overview

Use this skill to convert `.sgoal/MODULE.md` into `.sgoal/FEATURE.md`. Treat Distill as the phase that narrows module responsibilities into concrete features that can later be prioritized and scheduled.

## Workflow

1. Read `.sgoal/MODULE.md` first when it exists. Read `.sgoal/GOAL.md` as supporting context when available.
2. For each module, identify the smallest meaningful features that deliver behavior or enable required system capability.
3. Capture acceptance criteria, edge cases, data needs, and dependencies for each feature.
4. Avoid sequencing work here. Sequencing belongs in `$sgoal-action`.
5. Create or update `.sgoal/FEATURE.md` unless the user specifies another location.

## Feature Definition Rules

- Define features as outcomes or behaviors, not vague tasks.
- Keep implementation tasks out unless they are necessary to explain feature scope.
- Include enabling features when they unblock user-visible or operational features.
- Mark uncertain requirements as questions or assumptions.
- Preserve module ownership from `.sgoal/MODULE.md`.

## .sgoal/FEATURE.md Structure

Use this structure unless the project already has a stronger local convention:

```markdown
# Project Features

## Source Artifacts
- Goal artifact: .sgoal/GOAL.md
- Module artifact: .sgoal/MODULE.md
- Planning date:

## Feature Index
| Feature ID | Module | Feature | User or System Value | Status |
| --- | --- | --- | --- | --- |
| F-001 |  |  |  | Proposed |

## Features by Module

### Module: <name>

#### F-001: <feature name>
Summary:

Value:
- User or system value:
- Goal alignment:

Scope:
- In scope:
- Out of scope:

Acceptance Criteria:
- Given/When/Then or concise check:

Data and Interfaces:
- Inputs:
- Outputs:
- External interfaces:

Edge Cases:
- 

Non-Functional Requirements:
- Performance:
- Security:
- Reliability:
- Accessibility:

Dependencies:
- Requires:
- Enables:

Open Questions:
- 

## Unassigned or Ambiguous Features
- Feature:
- Why ownership is unclear:
- Suggested resolution:
```

## Quality Bar

- Make each feature independently understandable.
- Ensure every feature maps to one primary module.
- Prefer crisp acceptance criteria over broad descriptions.
- Keep feature IDs stable once introduced.
- Do not hide dependencies; unresolved dependencies become inputs to `.sgoal/ACTION.md`.

## Handoff

End with the next recommended step:

- Use `$sgoal-action` after `.sgoal/FEATURE.md` is complete enough to reason about implementation order and dependencies.
- Do not create `.sgoal/ACTION.md` from this skill unless the user explicitly asks for a combined pass.
