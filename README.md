---
title: InterChatProper
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [hub, index, onboarding, coordination]
---

# InterChatProper

Persistent shared memory and collaboration layer for a multi-model assistant team.

Repo: [AetherNomad-iX/InterChatProper](https://github.com/AetherNomad-iX/InterChatProper)

This is the single source of truth that survives model switches, session resets, and context-window limits. Grok, Claude, ChatGPT, Gemini, and any later model that the owner admits are interchangeable personal assistants — **this repo is not**. Files here are the owner's externalized long-term memory and the coordination surface for the team.

Any AI with repo access may read, write, and update files. Content may be prose, structured data, or binary artifacts other AIs can fully consume. Value compounds: every model that touches the repo leaves reasoning, decisions, and artifacts the next model inherits.

The v1 GitHub mailbox that started this experiment lives at [AetherNomad-iX/InterChat](https://github.com/AetherNomad-iX/InterChat). That repo is now the **backup / legacy bus**. This repo is canonical.

## What this is not

Not a chat log. Not a code repository. Not a secret vault. Do not dump API keys, passwords, private addresses, health details, or anything the owner would not put on a public page. Conversation debris belongs in a session, not here. Source code for shipped products belongs in the product repo. This hub stores *judgment*: who the owner is, what is in flight, what was decided, what to do next, and which model should do it.

## Coordination (what the hub now supports)

Shared memory was the foundation. The hub also runs a **multi-agent coordination protocol**:

- **Shared memory** — profile, preferences, projects, logs
- **Capability-based routing** — [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md) + [agents/registry.yaml](agents/registry.yaml)
- **Task claiming** — [docs/TASK_PROTOCOL.md](docs/TASK_PROTOCOL.md) + [tasks/](tasks/)
- **Delegation** — [docs/DELEGATION.md](docs/DELEGATION.md)
- **Peer review** — [docs/REVIEW_PROTOCOL.md](docs/REVIEW_PROTOCOL.md)
- **Decision memory** — [memory/DECISION_LOG.md](memory/DECISION_LOG.md) + [schemas/decision.schema.json](schemas/decision.schema.json)
- **Multi-agent project coordination** — [state/coordination.json](state/coordination.json)

```text
Human or Agent creates task
        ↓
best-suited agent claims it
        ↓
work is performed (delegate slices if needed)
        ↓
another agent reviews it
        ↓
revisions if needed
        ↓
approved result
        ↓
decision / artifact / task state recorded
```

Inbox ([inbox/](inbox/)) is still **handoffs and messages**. [tasks/](tasks/) is the **authoritative work-state**. Read both.

## How any AI onboards (read this order)

Exact sequence is in [docs/ONBOARDING.md](docs/ONBOARDING.md). Condensed:

1. [docs/ONBOARDING.md](docs/ONBOARDING.md)
2. [AGENTS.md](AGENTS.md)
3. [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md) and [agents/registry.yaml](agents/registry.yaml)
4. [docs/TASK_PROTOCOL.md](docs/TASK_PROTOCOL.md)
5. [memory/USER_PROFILE.md](memory/USER_PROFILE.md)
6. [memory/PREFERENCES.md](memory/PREFERENCES.md)
7. [state/ACTIVE_PROJECTS.md](state/ACTIVE_PROJECTS.md)
8. [state/coordination.json](state/coordination.json) and [tasks/open/](tasks/open/)
9. Latest entry in [logs/DECISIONS.md](logs/DECISIONS.md)
10. [inbox/PENDING.md](inbox/PENDING.md)

Then state readiness in one paragraph and either claim a task, take an inbox packet, or file a handoff.

## Model-strength routing (summary)

Full map: [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md). Skill: [.grok/skills/interchat-router/SKILL.md](.grok/skills/interchat-router/SKILL.md). Registry: [agents/registry.yaml](agents/registry.yaml) (guidance, not gospel).

| Route here | Model |
|---|---|
| Long-document analysis, careful multi-step reasoning, natural prose, high-stakes code review | **Claude** |
| Real-time events, current social/news signal, fast agentic execution, unfiltered takes, triage | **Grok** |
| Structured outputs, function-calling workflows, Code Interpreter, broad app integrations | **ChatGPT** |
| Multimodal (image/audio/video), native Google Workspace, large-scale data analysis | **Gemini** |
| Ambiguous work | **Grok triages → Claude verifies → ChatGPT executes tool calls** |

Every handoff packet **must** name the target model and justify the routing with one line drawn from `MODEL_STRENGTHS.md`. Copy [templates/HANDOFF.md](templates/HANDOFF.md). Task work uses [templates/TASK.md](templates/TASK.md) and [templates/DELEGATION.md](templates/DELEGATION.md).

## Contribution rules (short)

Humans and AIs follow [CONTRIBUTING.md](CONTRIBUTING.md) and [AGENTS.md](AGENTS.md).

- Prefer **update** over create. Create a new file only when the template says the unit of work is a new file (project, research thread, artifact, **task**, review).
- Append-only: [memory/DECISION_LOG.md](memory/DECISION_LOG.md), [logs/](logs/).
- Never delete another AI's entry without an explicit supersession note naming the old entry, the new one, and why.
- No force-push to `main`.
- Log every mutation in [logs/CHANGES.md](logs/CHANGES.md).
- One agent claims a task. Do not impersonate another `agent_id`. Do not claim tool access you do not have.

## Map

| Path | Role |
|---|---|
| [AGENTS.md](AGENTS.md) | Operating instructions for every AI |
| [docs/](docs/) | Onboarding, strengths, task / delegation / review protocols |
| [agents/](agents/) | Machine-readable registry (routing guidance) |
| [schemas/](schemas/) | Task and decision JSON Schema |
| [tasks/](tasks/) | Authoritative work-state board |
| [memory/](memory/) | Who the owner is, how he wants work done, why past calls were made |
| [state/](state/) | Live projects + coordination.json index |
| [research/](research/) | Findings, topic threads, raw dumps |
| [inbox/](inbox/) | Handoffs waiting / resolved |
| [logs/](logs/) | Decisions, sessions, file mutations |
| [artifacts/](artifacts/) | Files other AIs fully consume |
| [templates/](templates/) | Skeletons for new entries |
| [legacy/](legacy/) | Pointer and snapshot notes for InterChat v1 |

## First action after onboarding

If [tasks/open/](tasks/open/) has a task you are qualified to claim, claim it. Else if [inbox/PENDING.md](inbox/PENDING.md) has a packet addressed to you, take it. Else read [state/ACTIVE_PROJECTS.md](state/ACTIVE_PROJECTS.md) and advance the highest-priority `next action`. Do not open a status-only session that writes nothing useful.
