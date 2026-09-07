---
title: Task protocol
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [docs, tasks, protocol]
---

# Task protocol

How work is discovered, claimed, delegated, reviewed, and closed.

- Schema: [schemas/task.schema.json](../schemas/task.schema.json)
- Board: [tasks/README.md](../tasks/README.md)
- Agents: [agents/registry.yaml](../agents/registry.yaml)
- Strengths (prose, wins on conflict): [MODEL_STRENGTHS.md](MODEL_STRENGTHS.md)
- Inbox remains for **handoffs and messages**. Tasks are the **authoritative work-state**. Do not file a task only as an inbox packet.

## Lifecycle

```
proposed → open → claimed → in_progress → review_requested → approved → completed
                ↘ blocked ↗            ↘ changes_requested ↗
Any non-terminal state may go to cancelled.
approved may skip to completed when artifacts are filed.
```

| Status | Meaning | Who may enter it | Must record |
|---|---|---|---|
| `proposed` | Idea, not yet accepted as work | any agent, human | `created_by`, description, why it exists |
| `open` | Ready to claim | human, or grok triage, or the proposing agent after a thin sanity check | `preferred_agent` and `required_capabilities` if known; project slug if it has one |
| `claimed` | One agent owns it | the claiming agent (must be qualified or owner-named) | `claimed_by`, history row, move file `tasks/open/` → `tasks/active/` |
| `in_progress` | Work has started | `claimed_by` only | history row; optional `result_summary` as it grows |
| `blocked` | Cannot proceed | `claimed_by`, grok triage, or human | `blocked_by` **non-empty**; who can unblock |
| `review_requested` | Deliverables exist, waiting on a reviewer | `claimed_by` | `reviewers` non-empty, `review_status: pending`, artifacts/paths, move to `tasks/review/` |
| `changes_requested` | Reviewer sent it back | a named reviewer | review file + history note pointing at what to change |
| `approved` | Reviewer accepted | a named reviewer (or human) | `review_status: approve` or `approve_with_notes` |
| `completed` | Done, artifacts filed, state updated | `claimed_by` after approval, or human | `result_summary`, artifacts, move to `tasks/completed/`, coordination.json bump |
| `cancelled` | Will not be done | human, or claimed_by with a reason if the owner already agreed in chat | history note; never delete the file |

Terminal states: `completed`, `cancelled`. Do not reopen them in place. File a new task and `related_tasks` the old id.

## Who may transition

- **Owner (`human`)** may force any transition. Record `note: owner override`.
- **Claim.** You may claim `open` work if (a) you are `preferred_agent`, or (b) you have every `required_capabilities` id in [agents/registry.yaml](../agents/registry.yaml), or (c) the owner named you. Otherwise leave it and, if you are grok, re-route.
- **One claim.** If `claimed_by` is set and is not you, **do not work the task**. File a delegation or an inbox packet if you have something useful to add.
- **Self-review is not a review.** `claimed_by` may not be the sole reviewer except for `demo: true` chores the owner marked skip-review. Default: another model, Claude for high-stakes.
- **Blocked.** Only the claimer, grok (triage), or human. Clearing a block returns to `in_progress` or `claimed`, not to `open` (that would invite a double claim).

Every transition appends a `history[]` row: `at`, `by`, `from_status`, `to_status`, `note`.

## How an AI should work

### 1. Inspect open work

After onboarding: read [state/coordination.json](../state/coordination.json), list `tasks/open/` and `tasks/active/`, then [inbox/PENDING.md](../inbox/PENDING.md). Inbox packets that point at a `task_id` are messages about that task, not a second copy of it.

### 2. Determine whether you are qualified

1. Owner named you → you are qualified.
2. Else compare `required_capabilities` and `preferred_agent` to your row in the registry and one line from MODEL_STRENGTHS.
3. If you are missing a capability, **do not claim the whole task**. Either leave it or claim it only to **delegate** the missing slice ([DELEGATION.md](DELEGATION.md)).

Do not claim tool access you do not have. If you cannot commit, you may still claim if you will courier file contents, and you must say so in the history note.

### 3. Claim

Set `status: claimed`, `claimed_by: <you>`, history row, move the file to `tasks/active/`, bump `updated_at`, update [state/coordination.json](../state/coordination.json), log [logs/CHANGES.md](../logs/CHANGES.md). One commit if you can.

### 4. Delegate part of the task

Create a child `TASK-<parent>-<letter>` with `dependencies` / `related_tasks` set both ways. Put the delegation packet in the child file **and** copy [templates/DELEGATION.md](../templates/DELEGATION.md) into [inbox/PENDING.md](../inbox/PENDING.md) so the target model sees it on poll. Parent stays `in_progress` or goes `blocked` if the child is on the critical path.

### 5. Request another model

If you have not claimed: do not ping them in chat only. Open or retarget a task / inbox packet with `why this model` from MODEL_STRENGTHS.

### 6. Avoid duplicate work

- If `claimed_by` is set, stop.
- If two `open` tasks are the same job, cancel one (`related_tasks` the survivor) rather than working both.
- Search `task_id` and title words before creating.

### 7. Mark blockers

`status: blocked`, non-empty `blocked_by`, who can unblock, history note. Do not use `blocked` as a parking lot for boredom.

### 8. Submit results

Fill `deliverables` that exist, `result_summary`, `artifacts` paths. Then `review_requested`.

### 9. Request review

Name reviewers (default from [REVIEW_PROTOCOL.md](REVIEW_PROTOCOL.md)). Move the file to `tasks/review/`. Inbox packet to the reviewer is optional but useful if they poll inbox first.

### 10. Respond to requested changes

`changes_requested` → you (claimer) move it back to `tasks/active/`, set `in_progress`, do the work, request review again. Do not argue in the task file; argue in the review file, then change the artifact.

### 11. Complete or hand off

After `approved`: file remaining artifacts, `completed`, move to `tasks/completed/`, update the project `next action` if this was it, session log. If you cannot finish, unclaim only by setting `claimed_by` null **and** `status: open` **and** a history note — and only if no reviewer is mid-review. Prefer delegation over unclaim.

## End-to-end example (demo)

Meridian Visual Planner travel-time conflicts — **demo, not implemented**. Files:

- Parent [TASK-MVP-001](../tasks/open/TASK-MVP-001.md) — design the detector. Preferred triager: grok.
- [TASK-MVP-001-A](../tasks/open/TASK-MVP-001-A.md) — scheduling logic. Preferred: chatgpt (`structured_output`).
- [TASK-MVP-001-B](../tasks/open/TASK-MVP-001-B.md) — geographic / travel-time analysis. Preferred: gemini (`travel_time_geo`).
- [TASK-MVP-001-C](../tasks/open/TASK-MVP-001-C.md) — review of assumptions and acceptance criteria. Preferred: claude. `blocked` on A and B.

Happy path:

1. Grok reads `tasks/open/`, confirms the four files, claims **001** as triager, does not implement A–C.
2. ChatGPT claims **001-A** because structured scheduling rules are its class. Writes a spec/JSON algorithm to `artifacts/` (when actually doing it — not in this demo).
3. Gemini claims **001-B**, states distance/time assumptions (70 miles, 2:30 PM → 3:00 PM is 30 minutes, which is not enough), proposes a travel-time function.
4. Claude, once A and B have artifacts, claims **001-C**, reviews assumptions (traffic, time of day, parking, which routing engine), files [templates/REVIEW.md](../templates/REVIEW.md).
5. Parent 001 goes `review_requested` → `approved` → `completed`. Decision logged if the owner wants this in the product.

Scenario the design must catch: Event A ends 2:30 PM, Event B begins 3:00 PM, locations ~70 miles apart. Time-overlap logic says "fine"; travel-time logic says "impossible."

## Inbox vs tasks

| Layer | Stores | Does not store |
|---|---|---|
| `inbox/` | Handoffs, pings, "please look at TASK-X" | The work itself |
| `tasks/` | Status, claim, criteria, artifacts | Chat |

A poller that only reads inbox will miss open tasks. Onboarding now requires both.
