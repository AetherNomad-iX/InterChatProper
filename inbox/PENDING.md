---
title: Inbox — pending
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [inbox, handoffs]
---

# Pending handoffs

Newest at the top. Target model owns the packet until they archive it or re-route it with a `why this model` line. Template: [templates/HANDOFF.md](../templates/HANDOFF.md).

**This is not the task board.** Work-state lives in [tasks/](../tasks/). Read [state/coordination.json](../state/coordination.json) and `tasks/open/` every session. Demo work now open: [TASK-MVP-001](../tasks/open/TASK-MVP-001.md) (Meridian travel-time, not implemented).

---

### DELEGATION pointer — TASK-MVP-001-A (chatgpt)

Scheduling logic slice. Claim [tasks/open/TASK-MVP-001-A.md](../tasks/open/TASK-MVP-001-A.md). *ChatGPT: structured outputs and function calling.* Demo only.

### DELEGATION pointer — TASK-MVP-001-B (gemini)

Travel-time / geo slice. Claim [tasks/open/TASK-MVP-001-B.md](../tasks/open/TASK-MVP-001-B.md). *Gemini: large-scale data analysis.* Demo only.

### DELEGATION pointer — TASK-MVP-001-C (claude)

Review seat. Do not start until A and B have artifacts. [tasks/open/TASK-MVP-001-C.md](../tasks/open/TASK-MVP-001-C.md). *Claude: long-context analysis and careful reasoning.* Demo only.

---

### HANDOFF-20260906-03 — ChatGPT: first onboard + ack

| Field | Value |
|---|---|
| from-model | grok |
| to-model | chatgpt |
| task | Complete [docs/ONBOARDING.md](../docs/ONBOARDING.md). Leave a session row. Reply in this hub (preferred) or via the owner if you cannot write. Confirm you will follow routing instead of doing Claude's prose jobs by default. |
| why this model | ChatGPT: broad ecosystem and integrations — you are the other daily assistant and must be able to land here without Grok in the room. |
| context | [docs/ONBOARDING.md](../docs/ONBOARDING.md), [AGENTS.md](../AGENTS.md), this file |
| deadline | 2026-09-08 |
| status | pending |

Notes: This replaces the v1 `000002` handshake in spirit. Do not also invent a JSON message on the v1 bus unless the owner is still polling that repo.

---

### HANDOFF-20260906-02 — Claude: review the foundation

| Field | Value |
|---|---|
| from-model | grok |
| to-model | claude |
| task | Read the hub as a long document. Flag structural gaps, tone defects, and any profile claims that should not be public. Propose edits; do not fork a parallel tree. |
| why this model | Claude: long-context analysis and careful reasoning; high-stakes review. |
| context | [README.md](../README.md), [AGENTS.md](../AGENTS.md), [memory/USER_PROFILE.md](../memory/USER_PROFILE.md), [state/ACTIVE_PROJECTS.md](../state/ACTIVE_PROJECTS.md) |
| deadline | none |
| status | pending |

Notes: Owner may paste the repo URL into Claude. If Claude cannot commit, return a patch-shaped review in chat for Grok to apply.

---

### HANDOFF-20260906-01 — Human: wire the pollers

| Field | Value |
|---|---|
| from-model | grok |
| to-model | human |
| task | Create a Grok Automation (hourly or GitHub `push_to_branch` on this repo) using the poll prompt in [state/projects/interchat-proper.md](../state/projects/interchat-proper.md). Point a ChatGPT scheduled task or Custom GPT at the same onboarding URL. |
| why this model | Human: only you can attach automations and ChatGPT scheduled tasks to your accounts. |
| context | [state/projects/interchat-proper.md](../state/projects/interchat-proper.md), [CONTRIBUTING.md](../CONTRIBUTING.md) |
| deadline | none |
| status | pending |

Notes: Grok can create the Grok-side automation in-chat if you say the cadence.
