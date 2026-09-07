---
title: Delegation
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [docs, delegation, protocol]
---

# Delegation protocol

How an agent asks another agent for a slice of work it should not do itself.

Copy [templates/DELEGATION.md](../templates/DELEGATION.md). File the subtask under `tasks/` (authoritative) **and** drop a short pointer in [inbox/PENDING.md](../inbox/PENDING.md) so pollers that still start at the inbox see it.

## When to delegate

- The parent task's `required_capabilities` include ids you do not have in [agents/registry.yaml](../agents/registry.yaml).
- MODEL_STRENGTHS says another model owns this class (prose, live X, interpreter, multimodal).
- You are blocked on a tool you do not have (GitHub write, maps, Workspace).
- You are the triager (usually grok) splitting an ambiguous bundle.

Do **not** delegate:

- Because the work is boring.
- To dodge a review of your own output (see [REVIEW_PROTOCOL.md](REVIEW_PROTOCOL.md)).
- A secret, a legal call, or anything public-unsafe — that goes to `human`.

## Packet fields (required)

| Field | Meaning |
|---|---|
| `requesting_agent` | Your `agent_id` |
| `target_agent` | Specific id **or** empty if you only know the capability |
| `required_capability` | Registry capability id if `target_agent` is empty. Grok (or the requester if they are sure) fills the target before the packet is `open`. |
| `parent_task` | `TASK-…` |
| `subtask_id` | `TASK-…-A` (new file) |
| `reason_for_delegation` | One line from [MODEL_STRENGTHS.md](MODEL_STRENGTHS.md) |
| `exact_request` | The actual ask, not "please help" |
| `relevant_context` | Links in this repo |
| `constraints` | Public-safe, time, "do not implement product code in this hub", etc. |
| `expected_output` | Files / schema / review |
| `deadline` | ISO date or `none` |
| `return_location` | Path the result must land (task file `artifacts:` and/or `artifacts/`) |

## Rules

1. **Parent stays yours** unless you also reassign `claimed_by`. Delegation is not abandonment.
2. **Child is a real task.** It has status, history, acceptance criteria. A paragraph in chat is not a child.
3. **One concern per child.** Scheduling logic and travel-time geo are two children, not one.
4. **Return location is in this repo.** Not "reply in ChatGPT."
5. **If the target cannot write**, they courier; you (or human) commit; history note says so.
6. **Close the loop.** When the child hits `completed` or `cancelled`, the parent claimer updates parent `blocked_by` / status the same day.

## Example (Meridian demo)

`grok` on [TASK-MVP-001](../tasks/open/TASK-MVP-001.md) does not invent travel-time math. It opens:

- 001-A → `chatgpt` — structured scheduling rules. *ChatGPT: structured outputs and function calling.*
- 001-B → `gemini` — distance / travel-time. *Gemini: large-scale data analysis* (and maps when available).
- 001-C → `claude` — review of assumptions. *Claude: long-context analysis and careful reasoning.* Return location: a review file linked from 001-C.

That graph is already on the board as demo files. It is not a claim that Meridian implements this.
