# File Contracts

Use this reference when creating or modifying the standard project documents.

## Document Layers

| Layer | Files | Audience | Update trigger |
|---|---|---|---|
| Long-lived project truth | `BRIEF.md`, `DESIGN.md`, `ARCHITECTURE.md` | future agent, PM, engineering lead | project-level boundary, design, or architecture change |
| Agent entry | `AGENTS.md`, `CLAUDE.md` | Codex/Claude/OpenCode entering the repo | rules, command map, reading order, red lines change |
| Iteration truth | `iterations/vN-slug/PRD.md`, `CONTENT.md` | PM, implementer, reviewer | new version or feature scope |
| Execution state | `iterations/vN-slug/.plan/`, `docs/progress.md` | Conductor and workers | phase/task progress changes |
| Demand source | `docs/backlog.csv` | Conductor, PM | requirement creation/status/blocker changes |
| External docs | `README.md`, `docs/*.md` | humans and downstream systems | usage, integration, architecture, runbook changes |

## Long-Lived Specs

### `BRIEF.md`

Owns:
- project identity and long-term purpose
- target users and value proposition
- permanent boundaries and non-goals
- success criteria that survive multiple iterations

Do not put:
- v2/v3 feature details
- implementation notes
- session history

### `DESIGN.md`

Owns:
- visual language, UX principles, interaction patterns
- components, accessibility targets, tone
- design constraints that affect implementation

Do not put:
- product scope changes
- engineering-only details

### `ARCHITECTURE.md`

Owns:
- tech stack, repo structure, data model, deployment
- integration boundaries and dependency rules
- build/test commands and environment variables

Do not put:
- feature wishlists
- detailed progress logs

### `AGENTS.md` / `CLAUDE.md`

Owns:
- reading order
- hard rules and red lines
- command shortcuts
- where to find detailed docs

Keep concise. These files are maps and rules, not changelogs.

## Iteration Specs

Place each iteration in `iterations/vN-slug/`.

`PRD.md` owns:
- the current iteration goal
- scope and non-scope
- user flows, screens, acceptance criteria
- metrics or validation signals

`CONTENT.md` owns first-launch content when the project is content-heavy. After v1, prefer CMS, JSON, database, or source files unless the user explicitly wants document-based content planning.

When a new feature appears, create a new iteration PRD instead of rewriting old launch PRDs.

## Conductor Files

`docs/backlog.csv` is the demand truth source. Keep it structured. It should answer:
- what requirement exists
- priority, complexity, owner/status
- `pipeline_status`
- blocker reason
- links to PRD/acceptance/workplace

`docs/progress.md` is the runtime dashboard. It should answer:
- what is active now
- what is next
- current plan
- latest handoff
- review/verification evidence

Avoid duplicating full PRD or architecture content into progress. Link to stable docs.

## Phase Plan Files

For complex implementation, create:

```text
iterations/vN-slug/.plan/
├── plan.md
└── phases/
    ├── 01-slug.md
    └── 02-slug.md
```

`plan.md` is the stable route. Phase files are live task state.

Task status marks:

- `[ ]` pending
- `[~]` in progress
- `[x]` complete with evidence
- `[-]` skipped only after user approval
- `[!]` blocked with reason

Every `[x]` needs evidence: file path, command, test result, review note, or commit hash.

## Creation Policy

Do not create the full tree by default. Create the smallest missing artifact needed for the next state transition.

Examples:

- Vague new project: start with `BRIEF.md`/First Flight style spec, not backlog.
- Approved feature in existing repo: create/update iteration `PRD.md`, then backlog/progress.
- Active execution with no docs: create minimal `docs/progress.md` and plan, then backfill docs only as needed.
- Stage done: update docs and handoff; do not invent new PRD scope.
