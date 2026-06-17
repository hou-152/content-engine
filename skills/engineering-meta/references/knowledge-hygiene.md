# Knowledge Hygiene

Use this reference after acceptance, phase completion, long sessions, or explicit cleanup requests.

## Purpose

Keep knowledge useful for the next human or agent. Act as an editor, not a recorder.

## Audience Split

| Location | Audience | Content |
|---|---|---|
| memory system | future agent across sessions | durable preferences and non-obvious project facts |
| `AGENTS.md` / `CLAUDE.md` | agent entering this repo | rules, red lines, command map, reading order |
| `README.md` / `docs/` | humans and downstream systems | setup, usage, architecture, integration, runbooks |
| `docs/progress.md` / handoff | next session | current state, next step, blockers, evidence |

Do not mix audiences. A setup command belongs in README/runbook; an agent red line belongs in AGENTS; a temporary blocker belongs in progress/handoff.

## Cleanup Order

1. Inspect size and drift.
2. Read changed code and current docs.
3. Update external docs first.
4. Update agent entry docs second.
5. Update memory last, only if durable and supported by the platform.
6. Remove stale/duplicate facts.
7. Write handoff.

## Anti-Bloat Rules

- Root agent docs should not grow by more than about 30 lines per cleanup.
- Do not add blockquote histories like "On 2026-06-13 we shipped X".
- Do not copy architecture details into `AGENTS.md`; link to the architecture doc.
- Delete completed temporary TODOs instead of archiving them forever.
- Use absolute dates, never "today", "recently", or "last week".

## What to Update

Common mappings:

| Change | Update |
|---|---|
| new command or env var | README/runbook and AGENTS command map |
| new API or integration | integration guide, architecture, runbook |
| new data model/table | architecture data model and migration notes |
| new product capability | PRD/acceptance and user-facing docs |
| new architecture rule | ARCHITECTURE and AGENTS red-line pointer |
| changed setup flow | README and handoff |
| completed phase | progress/handoff, not long-lived docs unless facts changed |

## Handoff Template

Use this concise shape:

```markdown
## Latest Handoff

- Status: <where the work stands>
- Completed: <evidence-backed bullets>
- Next: <single next action>
- Blockers/Risks: <none or explicit>
- Verification: <commands/results or manual checks>
```

## Final Self-Check

Before reporting cleanup complete:

- Every touched file has a reason.
- No stale relative-time phrases remain.
- README setup still matches reality.
- AGENTS/CLAUDE contain rules, not session narrative.
- Links/paths mentioned in docs exist.
- Handoff lets a fresh agent continue without reading the whole chat.
