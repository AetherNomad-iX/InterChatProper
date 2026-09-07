---
name: interchat-router
description: Classify a task and assign the best model on the InterChatProper team. Use whenever work is about to be done or handed off — long analysis, live signal, structured/tool execution, multimodal/Workspace, or anything ambiguous.
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [skill, routing]
---

# InterChat router

You are choosing which model on the owner's team should do a piece of work. Models are not interchangeable. Read [docs/MODEL_STRENGTHS.md](../../../docs/MODEL_STRENGTHS.md) if this session has not. Registry: [agents/registry.yaml](../../../agents/registry.yaml) (guidance). If the unit of work is a board item, also follow [docs/TASK_PROTOCOL.md](../../../docs/TASK_PROTOCOL.md) — classify, then claim or delegate, do not only write an inbox packet.

This skill is for **Grok first** (default triage) but every model may run it before stealing or refusing a task.

## Classify

Pick **one** primary class. If two classes are load-bearing, split the work into two **tasks** (preferred) or two inbox packets.

| Class | Signals | Default model |
|---|---|---|
| `long-analysis` | Many files, long PDF, "read the whole thing," careful reasoning, published prose, high-stakes code review | Claude |
| `live-signal` | News, X, "right now," current events, unfiltered take | Grok |
| `agentic` | GitHub writes, browsers, automations, connected tools in this workspace, speed | Grok |
| `structured-exec` | JSON schema, function calling, Code Interpreter, ChatGPT ecosystem, scheduled GPT tasks | ChatGPT |
| `multimodal` | Image, audio, video as the main input | Gemini |
| `workspace-data` | Google Docs/Sheets/Drive/Gmail/Calendar as the source of truth | Gemini |
| `ambiguous` | Owner did not name a model; the ask mixes two or more classes | Grok triages |

## Routing table (defaults)

- Long-document analysis, careful multi-step reasoning, natural prose, high-stakes code review → **Claude**.
- Real-time events, current social/news signal, fast agentic execution, unfiltered takes → **Grok**.
- Structured outputs, function-calling workflows, Code Interpreter execution, broad app integrations → **ChatGPT**.
- Multimodal (image/audio/video), native Google Workspace data, large-scale data analysis → **Gemini**.
- Anything ambiguous → **Grok triages and routes; Claude verifies; ChatGPT executes tool calls.**

## Escalation

1. If the owner named a model, that model does it. Routing default is overridden. Do not argue unless the named model physically cannot (no eyes on a video, no GitHub token, etc.), in which case say so in one line and re-route.
2. If the work is in the wrong model's hands mid-flight, **stop after the current thin slice**, write a handoff packet, do not finish badly.
3. If two models disagree on a decision, **Claude writes the alternatives**, **Grok writes the unfiltered recommendation**, owner picks. Do not vote.
4. If a packet sits in inbox more than 24 hours with no session, **Grok** pings the owner in the next poll and does not silently reassign unless the owner said "anyone."
5. Secrets, legal, medical, or anything that must not be public → **human**. Models may draft; they do not publish.

## Handoff packet template

Copy into [inbox/PENDING.md](../../../inbox/PENDING.md). Do not invent fields.

```markdown
### HANDOFF-YYYYMMDD-NN — <short task name>

| Field | Value |
|---|---|
| from-model | grok \| claude \| chatgpt \| gemini \| human |
| to-model | grok \| claude \| chatgpt \| gemini \| human |
| task | One sentence. |
| why this model | One line from docs/MODEL_STRENGTHS.md. |
| context | Links to files in this repo (and only those). |
| deadline | ISO date or `none`. |
| status | pending |

Notes:

<what the next model must know that is not already in the linked files>
```

`why this model` is mandatory. If you cannot cite the strengths doc, you have not classified the task.

## Worked micro-examples

- "Rewrite the Wise Guides retainer one-pager so it reads like a human wrote it." → Claude. *Natural prose and instruction-following for publishable writing.*
- "Check X for people in Volusia County asking for tree work this week." → Grok. *Real-time information via X and current events.*
- "Turn the project index into JSON matching schema S." → ChatGPT. *Structured outputs and function calling.*
- "Read these six job-site photos and list hazards." → Gemini. *Multimodal (image/audio/video).*
- "I have a PDF, photos, and I want a proposal plus a live-comp check." → Grok triages into Claude + Gemini + Grok packets.

## After routing

You still have to **do** the part that is yours. Routing is not a way to put work down. If you are the target model, execute, then close the packet to [inbox/ARCHIVE.md](../../../inbox/ARCHIVE.md) and/or complete the task per TASK_PROTOCOL.
