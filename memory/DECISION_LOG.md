---
title: Decision log
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [memory, decisions, append-only]
---

# Decision log

Append-only audit trail of the owner's judgment (and the calls models made in his name). Chronological **newest at the top**. Mirror each entry into [logs/DECISIONS.md](../logs/DECISIONS.md). Field contract for new entries: [schemas/decision.schema.json](../schemas/decision.schema.json). Template: [templates/DECISION.md](../templates/DECISION.md).

Status is one of: `proposed` · `accepted` · `rejected` · `superseded` · `executed`.

---

## DEC-20260906-05 — Evolve the hub into a formal multi-agent coordination protocol

| Field | Value |
|---|---|
| decision_id | DEC-20260906-05 |
| Date | 2026-09-06 |
| question | Should InterChatProper stay a shared-memory wiki, or also become the place models claim work, delegate, review, and close tasks? |
| context | Foundation (memory, onboarding, routing, inbox, logs) was already live. Owner issued a follow-on spec for task lifecycle, schemas, registry, board, reviews, and an example Meridian task. |
| options_considered | (a) Keep inbox-only coordination — rejected; handoffs are messages, not work-state, and duplicate execution is too easy. (b) Replace the foundation with a new tree — rejected; owner ordered preserve-and-extend. (c) Issues-only GitHub project board — rejected as system of record; files stay auditable in git. (d) Extend in place with `tasks/`, schemas, registry, protocols — **accepted**. |
| Decision | Extend InterChatProper with a formal task lifecycle, agent registry, delegation, peer review, and a `tasks/` board. Inbox remains handoffs. Memory, routing, and logs stay. |
| rationale | Shared memory without claim/review is how two models do the same job and neither records the call. A board with `claimed_by` and independent review is how a team compounds. Meridian travel-time demo proves the graph (chatgpt scheduling, gemini geo, claude review, grok triage) without pretending the feature ships. |
| decided_by | human (spec) + grok (encode) |
| reviewed_by | none yet (open for Claude as HANDOFF-20260906-02) |
| related_tasks | TASK-MVP-001, TASK-MVP-001-A, TASK-MVP-001-B, TASK-MVP-001-C |
| affected_projects | interchat-proper, meridian-visual-planner |
| supersedes | none |
| Outcome | `executed` on branch `feature/multi-agent-coordination` |

## DEC-20260906-01 — InterChatProper is the canonical hub; InterChat v1 is backup

| Field | Value |
|---|---|
| decision_id | DEC-20260906-01 |
| Date | 2026-09-06 |
| Decision | Build [InterChatProper](https://github.com/AetherNomad-iX/InterChatProper) as the production shared-memory hub. Keep [InterChat](https://github.com/AetherNomad-iX/InterChat) as legacy mailbox + backup snapshot. |
| Reasoning | v1 proved GitHub can be a wire (numbered JSON, inboxes, cursor) but it is a chat bus, not a mind. The owner needs profile, preferences, projects, decisions, and model routing to survive session resets. A second repo named for that job is cleaner than overloading v1. |
| Alternatives considered | (a) Grow v1 in place — rejected because the mailbox layout (inbox/grok, messages/000001.json) collides with a knowledge graph. (b) Notion/Drive as the hub — rejected; GitHub is already connected to Grok and is versioned. (c) Private repo — rejected after v1's private visibility 404'd for the owner and blocked ChatGPT; public with a public-safe rule is the working compromise. |
| Model that proposed it | grok (v1 mailbox) then human (created InterChatProper and issued the architect prompt) |
| Outcome | `executed` — foundation written this session. |

## DEC-20260906-02 — Public over private for the hub

| Field | Value |
|---|---|
| decision_id | DEC-20260906-02 |
| Date | 2026-09-06 |
| Decision | Hub repos stay **public**. Secrets never go in them. |
| Reasoning | Private InterChat was invisible to the owner on the wrong GitHub session and to ChatGPT without a connector. The whole point is multi-model access. Public-safe writing is cheaper than access theater. |
| Alternatives considered | Private + every model gets a PAT — operationally heavy, fails the "ChatGPT Plus this afternoon" test. |
| Model that proposed it | grok, after the owner reported GitHub could not see InterChat |
| Outcome | `accepted` |

## DEC-20260906-03 — Model-strength routing is first-class

| Field | Value |
|---|---|
| decision_id | DEC-20260906-03 |
| Date | 2026-09-06 |
| Decision | Tasks are classified and assigned (Claude / Grok / ChatGPT / Gemini) instead of treating the models as clones. Ambiguous work: Grok triages, Claude verifies, ChatGPT executes tool calls. |
| Reasoning | The owner already runs more than one frontier model. Routing to strength is the only way the team compounds instead of fighting. |
| Alternatives considered | "Whoever is in the chat does everything" — the status quo, loses memory and quality. |
| Model that proposed it | human (architect prompt) |
| Outcome | `accepted` — encoded in [docs/MODEL_STRENGTHS.md](../docs/MODEL_STRENGTHS.md) and the router skill. |

## DEC-20260905-01 — InterChat v1 mailbox exists

| Field | Value |
|---|---|
| decision_id | DEC-20260905-01 |
| Date | 2026-09-05 |
| Decision | Create `AetherNomad-iX/InterChat` as a GitHub-backed mailbox so Super Grok and ChatGPT Plus can pass numbered messages. |
| Reasoning | The two products do not share a session. A repo both can poll is the thinnest wire. |
| Alternatives considered | Email, a custom app, a shared Google Doc — all worse at versioning and at Grok's existing GitHub tool surface. |
| Model that proposed it | grok, on the owner's request |
| Outcome | `executed` — superseded as *system of record* by InterChatProper the next day; still valid as a bus. |
