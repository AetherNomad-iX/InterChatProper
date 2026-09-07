---
title: Logs — decisions
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [logs, decisions, chronological]
---

# Decisions (chronological feed)

Mirror of [memory/DECISION_LOG.md](../memory/DECISION_LOG.md). Newest at the top. When you append a decision, write it in **both** files in the same commit.

---

### 2026-09-07T02:10:00Z — DEC-20260906-05 — multi-agent coordination protocol

- **Decision.** Extend the hub with task lifecycle, registry, delegation, review, `tasks/` board. Preserve memory/routing/inbox.
- **Model.** human + grok
- **Status.** executed
- **Full entry.** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)

### 2026-09-06T23:30:00Z — DEC-20260906-01 — InterChatProper is the canonical hub; InterChat v1 is backup

- **Decision.** This repo is the system of record. `AetherNomad-iX/InterChat` is legacy mailbox + `backup/interchat-proper` snapshot.
- **Model.** grok + human
- **Status.** executed
- **Full entry.** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)

### 2026-09-06T01:54:00Z — DEC-20260906-02 — Public over private for the hub

- **Decision.** Hub repos stay public; secrets never go in them.
- **Model.** grok
- **Status.** accepted
- **Full entry.** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)

### 2026-09-06T19:30:00Z — DEC-20260906-03 — Model-strength routing is first-class

- **Decision.** Claude / Grok / ChatGPT / Gemini defaults; ambiguous work is Grok → Claude → ChatGPT.
- **Model.** human
- **Status.** accepted
- **Full entry.** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)

### 2026-09-06T01:15:00Z — DEC-20260905-01 — InterChat v1 mailbox exists

- **Decision.** Numbered JSON bus for Grok ↔ ChatGPT.
- **Model.** grok
- **Status.** executed (superseded as system of record)
- **Full entry.** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)
