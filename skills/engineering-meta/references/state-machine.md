# State Machine and Roles

Use this reference when operating the Conductor Runtime.

## Pipeline

```text
draft -> designing -> planning -> executing -> acceptance -> done
```

## Status Meanings

| Status | Meaning | Exit condition |
|---|---|---|
| `draft` | demand exists but scope is not shaped | enough clarity to write or point to PRD |
| `designing` | product discovery/spec work | PRD exists and product scope is approved |
| `planning` | technical design and execution plan | design/review complete, plan ready, PM authorizes execution |
| `executing` | implementation and verification | all phase tasks done and quality gates pass |
| `acceptance` | PM/user review | PM/user accepts or sends back to execution/planning |
| `done` | accepted and cleaned up | handoff/docs/memory aligned |

## Required Pauses

Pause for PM/user decision when:

- moving `planning -> executing`
- moving `acceptance -> done`
- changing product contract or BRIEF boundary
- making scope tradeoffs
- deleting or rewriting non-obviously stale knowledge
- automatic repair loops exceed 2 attempts

## Roles

| Role | Owns | Must not own |
|---|---|---|
| PM/user | product decisions, authorization, acceptance | low-level implementation details unless requested |
| Conductor | state, delegation, quality gates, handoff | product truth or direct implementation details |
| Architect | technical design, risk review, architecture consistency | PM scope decisions |
| Dev | implementation, tests, self-check evidence | acceptance decision |
| UX Evaluator | UX/design review for user-facing changes | product scope expansion |
| code-reviewer | code quality findings | implementation fixes |
| architecture-guard | global architecture violations | product tradeoff decision |

If subagents are unavailable, simulate the roles sequentially but keep their outputs and responsibilities separate.

## Planning Runtime

For M/L requirements:

1. Read PRD, architecture, current code surface.
2. Produce or update `tech-design.md`.
3. Identify `impact_scope`:
   - `ux_surface`
   - `product_contract_change`
   - `structural_change`
   - `scope_tradeoff`
4. Trigger UX design review if `ux_surface: yes`.
5. Pause for PM if `product_contract_change` or `scope_tradeoff`.
6. Create phase/task plan in `docs/progress.md` or iteration `.plan/`.
7. Ask for execution authorization.

S-size requirements can skip formal technical design if the change is local and reversible.

## Execution Runtime

For each phase:

1. Assign tasks to Dev or implement directly when delegation is unavailable.
2. Require Dev self-check: tests, typecheck, lint, build, or reason not applicable.
3. Review phase diff before moving on.
4. Fix blocker findings.
5. Mark phase complete only with evidence.

Do not let "agent completed" replace review evidence.

## Final Quality Gate

Before `acceptance`, check:

- current plan complete
- acceptance criteria covered
- code review has no critical/high blockers
- architecture guard has no blockers when triggered
- UX has no blockers when triggered
- tests/typecheck/build evidence present or explicitly waived
- known limitations are visible in `acceptance.md` or handoff

Missing evidence is a failed gate.

## Acceptance Package

When entering `acceptance`, present:

- requirement id/name
- scope completed
- changed files/surfaces
- verification commands and results
- review summary
- known limitations
- exact ask: accept as done, request changes, or reopen planning
