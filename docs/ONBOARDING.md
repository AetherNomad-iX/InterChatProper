---
title: Onboarding
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [docs, onboarding, required]
---

# Onboarding — first contact

You are a new AI (or a returning AI whose session has zero memory of this repo). Complete this sequence **in order** before you write anything except a readiness statement.

Skip a step only if the file is missing, in which case note the gap in [logs/CHANGES.md](../logs/CHANGES.md) and keep going.

## Sequence

### 1. This file
You are here. The hub is [InterChatProper](https://github.com/AetherNomad-iX/InterChatProper). The owner runs a multi-model team. This repo is the shared memory **and** the coordination protocol. Chat windows die. These files do not.

### 2. [AGENTS.md](../AGENTS.md)
Operating law: read/write conventions, create vs update, conflict resolution, no silent deletes, how to log, how to hand off, how to claim a task, how not to impersonate another model.

### 3. [docs/MODEL_STRENGTHS.md](MODEL_STRENGTHS.md) and [agents/registry.yaml](../agents/registry.yaml)
You are not interchangeable. Internalize the table. Registry is routing guidance, not a guarantee. You will need one line from MODEL_STRENGTHS on every handoff and delegation.

### 4. [docs/TASK_PROTOCOL.md](TASK_PROTOCOL.md)
How work is claimed, delegated, reviewed, and closed. Skim [DELEGATION.md](DELEGATION.md) and [REVIEW_PROTOCOL.md](REVIEW_PROTOCOL.md) so you do not treat the inbox as the task board.

### 5. [memory/USER_PROFILE.md](../memory/USER_PROFILE.md)
Who the owner is, how he works, timezone, current focus. If `current focus` and the inbox or task board disagree, the **task board** wins for named work, the **inbox** wins for pings, and you file a decision if the drift looks real.

### 6. [memory/PREFERENCES.md](../memory/PREFERENCES.md)
Tone, length, structure, what to avoid. Output that ignores this file is a defect, not a style.

### 7. [state/ACTIVE_PROJECTS.md](../state/ACTIVE_PROJECTS.md)
What is live. Follow links into `state/projects/` only for the project you are about to touch.

### 8. Active task state
Read [state/coordination.json](../state/coordination.json), then [tasks/open/](../tasks/open/) and [tasks/active/](../tasks/active/). This is the work-state layer.

### 9. Most recent entry in [logs/DECISIONS.md](../logs/DECISIONS.md)
The last call the team made. Do not reopen it unless the owner asks or the world changed.

### 10. [inbox/PENDING.md](../inbox/PENDING.md)
Packets waiting. If one is addressed to you, that is a **message**. If it names a `task_id`, the task file is still the work. If a packet is addressed to a model that is not you and you are Grok, you may re-route with a justification. If you are not Grok, do not steal the packet.

## Then state readiness

One paragraph, in this shape:

> Onboarded. I am `<id>`. I have read profile, preferences, active projects, coordination.json, open/active tasks, latest decision, and inbox. Highest-priority item I see is `<link to task or packet>`. I will `<claim it | do it | hand it to X because Y from MODEL_STRENGTHS.md>`.

Put that paragraph in the chat with the owner. If you also opened a session on the bus, add a short row to [logs/SESSIONS.md](../logs/SESSIONS.md).

## Do not

- Do not rewrite the profile on first contact.
- Do not create a new project because the owner mentioned a wish. Wishes go in the relevant project's `open questions` until they have a next action.
- Do not greet with a capability dump. He already knows what you are.
- Do not ask him to run git commands, paste logs, or confirm the folder structure. Verify yourself.
- Do not start a task that is already `claimed_by` someone else.
- Do not pretend you have GitHub write, maps, or Workspace if you do not.

## Returning AIs

If your last session on this repo was today and you still have the files in context, you may skip steps 1–3 and jump to profile `updated` date, active projects, **coordination.json / tasks**, and inbox. If anything in those moved, reread what moved.
