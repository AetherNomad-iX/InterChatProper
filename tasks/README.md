---
title: Task board
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [tasks, index]
---

# Task board

Authoritative work-state for InterChatProper. Protocol: [docs/TASK_PROTOCOL.md](../docs/TASK_PROTOCOL.md). Schema: [schemas/task.schema.json](../schemas/task.schema.json).

**Inbox is not this.** [inbox/](../inbox/) is handoffs and messages. If you only read the inbox, you will miss open tasks.

## Directories = lifecycle buckets

| Directory | Statuses that live here |
|---|---|
| [open/](open/) | `proposed`, `open` |
| [active/](active/) | `claimed`, `in_progress`, `blocked` |
| [review/](review/) | `review_requested`, `changes_requested` |
| [completed/](completed/) | `approved`, `completed`, `cancelled` |

**Move the file** when status crosses a bucket. Do not leave a stale copy behind. Update [state/coordination.json](../state/coordination.json) in the same commit.

Filename = `task_id`.md, e.g. `TASK-MVP-001.md`. Reviews may be `TASK-MVP-001-REVIEW.md` beside the task in `review/`.

## How a file moves

```
open/TASK-X.md  --claim-->  active/TASK-X.md
active/TASK-X.md  --review_requested-->  review/TASK-X.md
review/TASK-X.md  --changes_requested-->  active/TASK-X.md
review/TASK-X.md  --approved-->  completed/TASK-X.md
any  --cancelled-->  completed/TASK-X.md
```

## Demo vs real

Frontmatter `demo: true` means example/architecture, **not** a claim that a product feature exists. The Meridian travel-time set (`TASK-MVP-001` and children) is demo until the owner promotes it.
