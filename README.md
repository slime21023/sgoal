# SGoal Skills

SGoal is a set of Codex skills for turning early project intent into practical planning artifacts. The workflow moves from discovery to delivery planning and writes generated documents under `.sgoal/`.

## Skills

| Skill | Purpose | Output |
| --- | --- | --- |
| `$sgoal-collect` | Clarifies project intent, target users, desired outcomes, scope, constraints, risks, success metrics, and assumptions. | `.sgoal/GOAL.md` |
| `$sgoal-organise` | Converts the project goal into functional modules with clear boundaries, responsibilities, dependencies, and ownership rules. | `.sgoal/MODULE.md` |
| `$sgoal-distill` | Breaks modules into concrete features with acceptance criteria, edge cases, data needs, non-functional requirements, and open questions. | `.sgoal/FEATURE.md` |
| `$sgoal-action` | Prioritizes features, maps dependencies, defines delivery increments, exposes blockers, and identifies immediate next actions. | `.sgoal/ACTION.md` |

## Recommended Workflow

Use the skills in this order:

1. Collect: create `.sgoal/GOAL.md` from project context and user intent.
2. Organise: read `.sgoal/GOAL.md` and create `.sgoal/MODULE.md`.
3. Distill: read `.sgoal/MODULE.md` and `.sgoal/GOAL.md`, then create `.sgoal/FEATURE.md`.
4. Action: read `.sgoal/FEATURE.md`, `.sgoal/MODULE.md`, and `.sgoal/GOAL.md`, then create `.sgoal/ACTION.md`.

Each step can be run independently, but the full sequence preserves traceability from project goals to modules, features, and delivery order.

## Usage

Invoke a skill by name in Codex. Example prompts:

```text
Use $sgoal-collect to clarify this project and create .sgoal/GOAL.md.
```

```text
Use $sgoal-organise to map this project into modules and create .sgoal/MODULE.md.
```

```text
Use $sgoal-distill to break modules into features and create .sgoal/FEATURE.md.
```

```text
Use $sgoal-action to order feature development and create .sgoal/ACTION.md.
```

You can also ask for a combined pass, but the default behavior is to create or update only the artifact owned by the selected skill.

## Project Structure

```text
skills/
  sgoal-collect/
    SKILL.md
    agents/openai.yaml
  sgoal-organise/
    SKILL.md
    agents/openai.yaml
  sgoal-distill/
    SKILL.md
    agents/openai.yaml
  sgoal-action/
    SKILL.md
    agents/openai.yaml

.sgoal/
  GOAL.md
  MODULE.md
  FEATURE.md
  ACTION.md
```

The `skills/sgoal-*` directories define the Codex skills. The `.sgoal/*.md` files are generated planning artifacts for the target project.

## When To Use Each Skill

Use `$sgoal-collect` when the project goal is still unclear or scattered across notes, tickets, README files, or conversation.

Use `$sgoal-organise` when the goal is clear enough to identify major functional areas, module boundaries, shared concerns, and dependencies.

Use `$sgoal-distill` when modules are defined and you need feature-level behavior, acceptance criteria, edge cases, and readiness questions.

Use `$sgoal-action` when features are defined and you need a dependency-aware implementation order, delivery increments, blockers, and immediate next actions.
