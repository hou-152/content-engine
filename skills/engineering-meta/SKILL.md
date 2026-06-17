---
name: engineering-meta
description: Engineering project meta-skill that routes a project or feature from idea/spec to execution, acceptance, and knowledge cleanup while guarding domain terminology, concept topology, context packs, and learning loops. Use when the user asks to integrate or operate 建站元技能 / First Flight, Conductor, 洁癖 / neat-freak, 工程化元技能, project kickoff, iteration planning, backlog/progress orchestration, phase-based implementation, PM acceptance, end-of-stage handoff cleanup, terminology drift, concept freeze, context loss, Phase 6 retrospective, release README, or domain-contract validation.
---

# Engineering Meta v3

Use this as the project operating entrypoint. The user should not need to understand the whole engineering process. Classify the current project state, select the right module, and ask only for decisions that cannot be inferred from artifacts.

This skill integrates three systems and two guardrails without collapsing their boundaries:

- **Spec Kernel**: First Flight style project definition and iteration specs.
- **Conductor Runtime**: backlog/progress driven execution orchestration.
- **Knowledge Hygiene**: neat-freak style end-of-stage documentation and memory cleanup.
- **Domain Contract Gate**: terminology, hierarchy, topology, and promotion control for mature user systems.
- **Context Pack Gate**: minimum context bundle and Phase 6 learning loop before execution or release.

## Operating Principle

Do not ask the user to learn the framework. Encapsulate the framework and expose a small interaction surface:

1. What state is the project in?
2. What truth sources already exist?
3. What is the next irreversible or high-risk decision?
4. What evidence proves the stage is complete?

Documents serve decisions, not ceremony. If a document will not change what the next agent, teammate, or user does, do not create or expand it.

For user-specific domain systems such as Dontbesilent, protect the domain language and concept topology before optimizing the workflow. A correct-looking route is still wrong if it renames frozen concepts, changes hierarchy, treats connected layers as a flat checklist, or upgrades a candidate field into a system layer.

For publication, release, or handoff work, do not write a polished README first. First extract the hard-won operating lessons, failure modes, gates, and proof artifacts; then write the README as an interface to those mechanics.

## Entry Router

Start every run by classifying the request into exactly one primary path.

| User situation | Primary path | Action |
|---|---|---|
| New project, vague idea, "help me build/start a site/app" | `spec` | Generate or update the project spec set before execution. |
| Existing project, new feature or iteration | `iteration` | Read long-lived docs, create/update iteration PRD, then prepare execution. |
| Backlog/progress exists and work should move forward | `runtime` | Use Conductor Runtime to advance the state machine. |
| User says phase/stage is done, handoff, tidy, sync, cleanup | `hygiene` | Run Knowledge Hygiene after checking actual docs/code. |
| User reports context loss, term drift, or "it became dumb" | `contract` | Run Domain Contract Gate and Context Pack Gate before any execution. |
| User is preparing to publish, ship, or explain the skill | `release` | Extract lessons, evidence, and user-facing README from real runs. |
| User asks to design the process or skill itself | `meta-design` | Discuss architecture first; do not overwrite live skill files unless approved. |

If multiple paths apply, choose the earliest missing layer:

`contract/context -> spec -> iteration -> runtime -> quality gate -> hygiene -> release`

Example: if the user asks "start development" but no PRD or backlog exists, route to `spec` or `iteration`, not `runtime`.

## Domain Contract Gate

Before proposing a plan in a mature user system, check whether there is a frozen concept contract. This is mandatory when the user mentions symptoms like:

- term drift, 术语偏移, 概念漂移
- "变蠢", "上下文瞎弄", "你又忘了上下文"
- a fixed loop/layer/stage/model count
- a candidate that must not be promoted into a contract
- Dontbesilent, 内容系统, 作者表达, 五维材料, 三层拟合, 三维检验, Stack Loops

Run this gate before `Next action`.

### Contract and Topology Extraction

Extract a small glossary and topology map from the latest user instruction and project artifacts:

```text
Frozen terms:
- <term>: <allowed meaning>

Hierarchy:
- <system layer> > <runtime step> > <field/candidate>

Topology:
- <source layer> -> <method layer> -> <verification layer> -> <feedback layer>

Forbidden renames/promotions:
- <candidate> must not be called <system layer>
- <runtime stage> must not be called <loop> if loop is already reserved

Acceptance language:
- <what evidence or phrase proves this stage is accepted>
```

For Dontbesilent-style content systems, preserve this topology unless newer project artifacts explicitly override it:

```text
Four architecture layers:
1. 内容资产层：answers "我有什么材料？"
2. 作者表达层：answers "作者怎么判断、推进、表达？"
3. 生产编排层：answers "今天怎么从材料生成一篇稿？"
4. 验收反馈层：answers "这东西能不能用？"

Five content units:
QST / CON / OPI / CAS / SOL are content asset units, not article section templates.

Three-layer fit:
材料拟合 -> 关系拟合 -> 选择拟合.
This is the bridge from content assets to author expression; do not compress it into "style fitting".

Three-dimensional check:
深层判断 / 中层结构 / 表层风格.
These are verification surfaces throughout assembly, not final polish.

Stack Loops:
Only the six system loops may be called loops:
概念冻结 / 工程契约 / 内容资产 / 作者表达 / 生产编排 / 验收反馈.
```

### Contract Check

Before writing a plan, compare proposed wording against the glossary:

- Do not reuse a frozen term for a lower-level execution step.
- Do not convert a runtime stage into a system loop.
- Do not promote a field/candidate into a layer, dimension, or contract unless the user explicitly approves that upgrade.
- Do not collapse baseline/test/candidate/contract into one word like "纳入" without saying which level.
- Do not flatten the topology into a checklist or permutation table. For example, five content units feed author-expression fitting; they are not article sections, and the three-dimensional check is not a final coating step.
- Do not skip the bridge layer. If output goes from `QST / CON / OPI / CAS / SOL` directly to a draft, stop and require `材料拟合 / 关系拟合 / 选择拟合` plus `深层判断 / 中层结构 / 表层风格` evidence.

If the contract is unclear, ask one narrow question:

```text
这里的 <term> 是系统级概念，还是本次执行阶段？我需要先冻结这个词，避免后面污染上下文。
```

### Compact Drift Report

When drift is detected, output at most 6 lines:

```text
Drift: <what changed>
Frozen meaning: <original meaning>
Wrong usage: <bad wording>
Correction: <safe wording>
Decision needed: <only if user must choose>
Next safe action: <what can continue without drift>
```

### Topology Report

When operating a mature content system, include a compact topology line in the normal output:

```text
Domain topology: 四层 checked; 五维=materials; 三层=fit bridge; 三维=continuous check; loops=6 system loops
```

If any part is missing or conflicts, use `Domain contract: conflict` and stop before execution.

## Context Pack Gate

Run this gate when the user reports context loss, when the task is in a mature domain system, or before delegating to another agent.

The goal is not to stuff every file into context. The goal is to preserve the minimum non-lossy context bundle.

### Context Layers

Build a compact context pack with four layers:

```text
Core context:
- frozen concepts, topology, goals, non-goals, acceptance language

Evidence context:
- source files, gold samples, metrics, prior acceptance reports, rejection logs

Engineering context:
- file map, scripts, state files, templates, process docs

Forbidden context:
- phrases or shortcuts that must not be treated as valid conclusions
```

For Dontbesilent-style work, the core context must preserve:

```text
四层架构 / 五维材料 / 三层拟合 / 三维检验 / Phase 6 / Stack Loops
前置知识够了 != 直接 MVP
五维材料 != 文章结构
三维检验 != 最后喷漆
三层拟合不得被省略
低反馈 = 系统变量证据，不是“还没测试”
```

### Agent Split

When delegation is available, split work by failure risk:

```text
Main Agent: maintain concept boundary and final integration.
Search Agent: find evidence only, no conclusions.
Critic Agent: look for concept loss, topology flattening, execution too early.
Writer Agent: write README or release copy only after gates pass.
```

If delegation is unavailable, simulate these roles sequentially and label which role produced each finding.

### Context Loss Check

Before planning or release, answer:

```text
What concept is most likely to be compressed away?
Which file proves the current meaning?
What phrase would be a dangerous shortcut?
What evidence shows this is ready for execution or publication?
What must be written to Phase 6 if this fails?
```

If any answer is missing, stop and search before continuing.

## Learning Loop

Every mature-system run must end with a small learning loop, even when the execution succeeds.

Record:

```text
agent_mistake:
concept_drift:
context_loss:
command_gap:
evidence:
next_rule:
kb_destination:
```

Do not write emotional apologies. Write a next rule that prevents the same failure.

Examples:

```text
Wrong: 下次注意不要叫错。
Right: Only the six system Stack Loops may be called loops; runtime sequences must be called stages, steps, runs, or passes.
```

Use the learning loop to decide whether to update:

- the project docs,
- the skill rules,
- the release README,
- or only the handoff.

## Minimal Startup Checklist

Before acting, inspect the project artifacts. Prefer real files over conversation memory.

1. List root files and `docs/` if present.
2. Check for long-lived specs: `BRIEF.md`, `DESIGN.md`, `ARCHITECTURE.md`, `AGENTS.md`, `CLAUDE.md`.
3. Check for iteration specs: `iterations/v*/PRD.md`, `iterations/v*/CONTENT.md`, `iterations/v*/.plan/`.
4. Check for Conductor artifacts: `docs/backlog.csv`, `docs/progress.md`, `docs/process/*.md`, requirement directories.
5. Check for handoff/knowledge docs: `README.md`, `docs/*.md`, memory files if the platform exposes them.
6. Check for a domain contract: glossary, loop/layer definitions, forbidden promotions, acceptance language, or the latest user correction.
7. Check for context-pack docs: retrospectives, context compression notes, search strategy, acceptance reports, rejection rules, metrics.

When artifacts conflict, use this precedence:

`explicit latest user instruction -> current project files -> backlog/progress -> long-lived specs -> memory -> prior chat`.

## Module Boundaries

Keep the modules deep and separate.

### Spec Kernel

Use for product discovery, 0-to-1 project shaping, and iteration spec writing.

Owns:
- project purpose, users, value, non-goals
- first-version or iteration scope
- information architecture, design direction, technical constraints
- AI entry docs and phase planning handoff

Does not own:
- live task execution
- code review
- final acceptance
- stale documentation cleanup outside spec sync

### Conductor Runtime

Use for moving approved work through a delivery state machine.

Owns:
- `docs/backlog.csv` as demand truth source
- `docs/progress.md` as runtime dashboard
- `pipeline_status` transitions
- worker delegation, review orchestration, quality gates
- PM authorization and acceptance pauses

Does not own:
- changing product truth without PM/user approval
- doing implementation details itself when worker delegation is available
- turning progress notes into long-lived docs

### Knowledge Hygiene

Use after a phase, requirement, session, or milestone reaches a stable stopping point.

Owns:
- reconciling README, `AGENTS.md`/`CLAUDE.md`, `docs/`, and memory against code
- deleting or compressing stale/duplicate knowledge
- writing handoff state for the next agent
- preventing documentation bloat

Does not own:
- inventing new requirements
- changing BRIEF/PRD product truth
- preserving historical narrative in root agent docs

## State Machine

Use the Conductor state machine once a requirement exists:

```text
draft -> designing -> planning -> executing -> acceptance -> done
```

Hard pauses:

- `planning -> executing`: require PM/user authorization unless the user already gave explicit "start/execute/开干" approval for the current scoped plan.
- `acceptance -> done`: require PM/user acceptance.
- Product contract change, scope tradeoff, BRIEF boundary conflict, destructive knowledge deletion: stop and ask.
- Terminology contract conflict: stop, correct the wording, and do not continue with polluted terms.
- Context pack missing for a mature system: stop and retrieve the core/evidence/engineering/forbidden layers.
- Release/publish request without evidence or failure modes: stop and extract lessons before writing.

Fast path:

- Small S-size tasks may go `draft -> executing -> acceptance -> done` if they are bounded, low-risk, and have explicit acceptance criteria.

Read `references/state-machine.md` when operating backlog/progress or role delegation.

## Quality Gate

Before moving to `acceptance`, require evidence. Missing evidence counts as failure.

Minimum evidence:
- feature scope complete against PRD/current plan
- tests or a clear reason tests are not applicable
- typecheck/lint/build where relevant
- code review findings resolved or recorded
- architecture review for structural changes
- UX review for user-facing changes
- domain contract check for mature user systems with frozen terminology
- context pack check when mature domain systems, delegation, publication, or long-horizon handoff is involved
- learning loop entry for mature-system failures and important successes
- known limitations written into `acceptance.md` or handoff

Do not mark work complete because an agent said it is complete. Completion needs artifact evidence.

## Knowledge Gate

After acceptance, phase completion, or a long session, run the hygiene gate:

1. Re-read changed code and docs.
2. Update external-facing docs before agent-facing docs.
3. Keep `AGENTS.md`/`CLAUDE.md` as rules and pointers, not changelogs.
4. Remove stale, duplicate, or relative-time facts.
5. Write a short handoff with current status, next step, blockers, and verification evidence.

Read `references/knowledge-hygiene.md` for the detailed cleanup checklist.

## Interaction Rules

Ask only at decision gates. Do not interrogate the user about the whole framework.

Good questions:
- "Is this a new project, an iteration, or a cleanup?"
- "Can I treat this PRD as approved and start execution?"
- "This changes the BRIEF boundary. Do you want to change the product direction or narrow the request?"
- "The acceptance package is ready. Do you accept this as done?"

Bad questions:
- asking the user to explain all six knowledge categories
- asking for every document field before inspecting existing artifacts
- asking for approval on reversible implementation details
- asking whether to clean obvious stale docs after the user requested cleanup
- asking broad conceptual questions when one frozen term is the only ambiguity

## File Contracts

Read `references/file-contracts.md` before creating or modifying the standard project documents.

Core contract:

```text
project/
├── BRIEF.md
├── DESIGN.md
├── ARCHITECTURE.md
├── AGENTS.md
├── CLAUDE.md
├── docs/
│   ├── backlog.csv
│   ├── progress.md
│   └── process/
└── iterations/
    └── vN-slug/
        ├── PRD.md
        ├── CONTENT.md        # v1 only unless explicitly needed
        └── .plan/
```

Do not force every project to have every file. Create only what the current state needs.

## Failure Modes

Watch for these failures and correct course immediately:

- **Ceremony creep**: adding docs or approvals that do not change decisions.
- **Truth-source confusion**: backlog used as both demand source and execution log.
- **Role collapse**: Conductor becomes PM, Dev, and reviewer at once.
- **Spec drift**: code changes without updating the right spec or docs.
- **Terminology drift**: frozen system terms are reused for runtime steps or candidate fields.
- **Hierarchy promotion**: a test field/candidate is accidentally called a layer, loop, dimension, or contract.
- **Topology flattening**: connected layers are treated as a flat checklist or permutation table.
- **Context compression loss**: an important bridge concept disappears, such as three-layer fitting between materials and expression.
- **Execution too early**: the agent jumps from "knowledge is enough" to MVP, batch generation, or publication before concept freeze.
- **Release without lessons**: README explains features but not gates, failure modes, or evidence from real usage.
- **Memory rot**: root agent docs accumulate history instead of reusable rules.
- **Over-asking**: user is asked to understand the process instead of making key decisions.

## Output Shape

For non-trivial runs, report:

```text
Current state: <spec | iteration | runtime | acceptance | hygiene>
Truth sources found: <files>
Domain contract: <none | checked | conflict: exact term>
Domain topology: <none | checked | conflict: exact layer/edge>
Context pack: <none | checked | missing: exact layer>
Next action: <what will happen now>
Decision needed: <none | exact question>
Evidence required: <what will prove completion>
```

For release work, report:

```text
Release surface: <README | skill package | docs | handoff>
Lessons extracted: <source files>
Failure modes covered: <short list>
Smoke cases: <short list>
Publish status: <draft | ready | blocked>
```

For meta-design work, produce a proposed skill structure first and wait before installing or overwriting live skills unless the user explicitly says to execute.
