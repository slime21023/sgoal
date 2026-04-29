---
name: sgoal-collect
description: Create .sgoal/GOAL.md for a project using the Collect phase of the SGoal planning workflow. Use when Codex needs to clarify project intent, gather discovery context, define outcomes, users, constraints, risks, success metrics, assumptions, and non-goals before module or feature planning. Trigger on requests mentioning Collect, SGoal, GOAL.md, project goals, discovery, product goal definition, or early project scoping.
---

# SGoal Collect

## Overview

Use this skill to turn scattered project intent into a concise `.sgoal/GOAL.md`. Treat Collect as the discovery phase: expand context first, then converge on a clear goal artifact that downstream skills can use.

## Workflow

1. Inspect existing project files if available, especially product notes, requirements, README files, tickets, or prior planning docs.
2. Ask only for blocking missing information. If the user wants momentum, proceed with explicit assumptions.
3. Separate observations from decisions. Do not invent hard requirements without marking them as assumptions.
4. Create or update `.sgoal/GOAL.md` unless the user specifies another location.
5. Keep `.sgoal/GOAL.md` stable enough for `$sgoal-organise` to derive modules from it.

## .sgoal/GOAL.md Structure

Use this structure unless the project already has a stronger local convention:

```markdown
# Project Goal

## Objective
One concise paragraph describing what the project is trying to achieve.

## Target Users
- User group:
- Primary need:
- Current pain:

## Desired Outcomes
- Outcome:
- Why it matters:
- How to observe success:

## Scope
### In Scope
- 

### Out of Scope
- 

## Constraints
- Technical:
- Product:
- Time or delivery:
- Operational:

## Success Metrics
- Metric:
- Baseline or target:
- Measurement source:

## Assumptions
- 

## Risks and Unknowns
- Risk or unknown:
- Impact:
- Validation needed:

## Decision Log
- YYYY-MM-DD: Decision and reason.
```

## Quality Bar

- Make the objective specific enough to support module decomposition.
- Keep scope and non-goals explicit.
- Prefer measurable outcomes over vague aspirations.
- Mark uncertain claims as assumptions or unknowns.
- Avoid feature lists except where they are necessary to explain scope.

## Handoff

End with the next recommended step:

- Use `$sgoal-organise` after `.sgoal/GOAL.md` is complete enough to identify major project modules.
- Do not create `.sgoal/MODULE.md`, `.sgoal/FEATURE.md`, or `.sgoal/ACTION.md` from this skill unless the user explicitly asks for a combined pass.
