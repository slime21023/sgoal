# SGoal Skills

SGoal is a compact Codex skill set for converging early project intent into lightweight requirement artifacts. It helps teams move from unclear needs to a small, testable specification without producing a heavyweight enterprise SRS.

## Skills

| Skill | Purpose | Output |
| --- | --- | --- |
| `$sgoal-discover` | Clarifies early intent, stakeholders, situations, desired outcomes, scope, constraints, assumptions, risks, and open questions. | `.sgoal/INTAKE.md` |
| `$sgoal-specify` | Turns discovery context into lightweight requirements, stories, behavior, acceptance criteria, non-functional requirements, and interface notes. | `.sgoal/SPEC.md` |
| `$sgoal-review` | Reviews the specification for readiness, quality, priority, traceability, risk, conflict, missing decisions, and change impact. | `.sgoal/REVIEW.md` |

## Recommended Workflow

Use the skills in this order:

1. Discover: inspect project context and create `.sgoal/INTAKE.md`.
2. Specify: read `.sgoal/INTAKE.md` and create `.sgoal/SPEC.md`.
3. Review: read `.sgoal/SPEC.md` and create `.sgoal/REVIEW.md`.

Each skill can be used independently, but the full sequence preserves traceability from early intent to requirements and readiness review.

## Usage

Invoke a skill by name in Codex:

```text
Use $sgoal-discover to clarify this project and create .sgoal/INTAKE.md.
```

```text
Use $sgoal-specify to turn .sgoal/INTAKE.md into a lightweight .sgoal/SPEC.md.
```

```text
Use $sgoal-review to check .sgoal/SPEC.md and create .sgoal/REVIEW.md.
```

By default, each skill creates or updates only the artifact it owns.

## Project Structure

```text
skills/
  sgoal-discover/
    SKILL.md
    agents/openai.yaml
  sgoal-specify/
    SKILL.md
    agents/openai.yaml
  sgoal-review/
    SKILL.md
    agents/openai.yaml

.sgoal/
  INTAKE.md
  SPEC.md
  REVIEW.md
```

The `skills/sgoal-*` directories define the Codex skills. The `.sgoal/*.md` files are generated requirement artifacts for the target project.

## Method Bias

SGoal uses simplified requirements engineering practices that are easy to operate and control:

- Discovery: interviews, 5 Whys, Jobs-to-be-Done, and Impact Mapping.
- Specification: User Story, Job Story, Use Case Slice, BDD/ATDD-style acceptance criteria, and NFR capture.
- Review: INVEST, MoSCoW, Volere fit criterion, traceability, and change impact checks.

These methods are lightweight decision aids, not a mandate to produce large process documents.

## When To Use Each Skill

Use `$sgoal-discover` when the project goal is still unclear, information is scattered across notes or tickets, or requirements are mixed with assumptions and solution ideas.

Use `$sgoal-specify` when the intake is clear enough to describe behavior, boundaries, acceptance criteria, non-functional expectations, and interface needs.

Use `$sgoal-review` when a lightweight specification exists and the team needs to decide whether requirements are ready for implementation, need refinement, or still contain unresolved decisions.
