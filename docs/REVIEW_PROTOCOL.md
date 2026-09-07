---
title: Review protocol
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [docs, review, protocol]
---

# Review protocol

Independent check that work is correct, safe, complete, consistent with recorded decisions, and actually meets acceptance criteria.

Template: [templates/REVIEW.md](../templates/REVIEW.md).  
Task states: `review_requested` → `approved` | `changes_requested` | (reject path via `cancelled` or return to `open` only if unclaimed). See [TASK_PROTOCOL.md](TASK_PROTOCOL.md).

## Reviewer selection

| Kind of work | Default reviewer |
|---|---|
| Publishable prose, specs, high-stakes reasoning, code-like configs | `claude` |
| "Is this current / did we log it / is the next action real" | `grok` |
| Schema, JSON contract, interpreter output | `chatgpt` |
| Multimodal or Workspace-sourced claims | `gemini` |
| Money, public identity, routing defaults | `human` (only approver who matters) |

The claimer **names** `reviewers` on the task before `review_requested`. If they name themselves alone, grok triage or human adds a second reviewer unless `demo: true` and the owner said skip.

Do not pick a reviewer who authored the artifact under review. Delegation children: the parent claimer may review *integration*, but the child's primary reviewer should still be a different model when the child is high-stakes.

## Independent review expectations

The reviewer:

1. Reads acceptance criteria **before** the artifact, then the artifact, then criteria again.
2. Checks [memory/DECISION_LOG.md](../memory/DECISION_LOG.md) for collisions.
3. Checks public-safety ([AGENTS.md](../AGENTS.md) public-safe rule).
4. Does not silently rewrite the artifact. They file a review and set task status.
5. Does not rubber-stamp. If they did not actually inspect, they must not approve.

## Outcomes

| `review_status` | Task status to set | Meaning |
|---|---|---|
| `approve` | `approved` | Criteria met, safe, consistent. Claimer may `completed`. |
| `approve_with_notes` | `approved` | Good enough to complete; notes are non-blocking. Claimer should still read them. |
| `changes_requested` | `changes_requested` | Blocking gaps. Notes must be actionable. Claimer returns to `in_progress`. |
| `reject` | usually `cancelled` (or new task) | Wrong job, unsafe, or fatally off-decision. Explain. Do not `reject` as a spicy `changes_requested`. |

## Conflict resolution

1. Owner wins.
2. If two reviewers disagree: **Claude writes the alternatives**, **Grok writes the unfiltered recommendation**, owner picks. Same rule as [AGENTS.md](../AGENTS.md).
3. The claimer does not "win" by restating the work. They change the artifact or they appeal to human.

## Second-review escalation

Escalate when:

- `reject` on a non-demo task
- `changes_requested` twice on the same criterion
- Safety / public-identity / money
- Reviewer is also the only person who understands the tool output (get a second class from the table)

Escalation packet: inbox to `human` or to the other default reviewer, `parent_task` set, `reason_for_delegation` = "second review".

## Demo note

[TASK-MVP-001-C](../tasks/open/TASK-MVP-001-C.md) is the intended review seat for the Meridian travel-time design. It is blocked until A and B produce artifacts. Do not "approve" the parent while 001-C is still blocked.
