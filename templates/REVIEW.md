---
title: Template — review
created: 2026-09-06
updated: 2026-09-06
author: grok
status: template
tags: [template, review]
---

# Template — review

Protocol: [docs/REVIEW_PROTOCOL.md](../docs/REVIEW_PROTOCOL.md). Save as `tasks/review/<task_id>-REVIEW.md` or append to the task body. Then set the parent task `review_status` and status.

```markdown
---
title: Review of TASK-…
created: YYYY-MM-DD
updated: YYYY-MM-DD
author: claude
status: active
tags: [review]
task_id: TASK-…
reviewer: claude
review_status: changes_requested
---

# Review of TASK-…

## Verdict

`approve` | `approve_with_notes` | `changes_requested` | `reject`

## Criteria checked

| Criterion | Met? | Note |
|---|---|---|
| <acceptance criterion> | yes/no | |

## Correctness

<Did the solution actually work for the stated problem?>

## Safety / public-safe

<Secrets, over-claiming, identity.>

## Completeness

<Deliverables listed vs delivered.>

## Consistency with decisions

<Links to DEC-… ids. Collisions.>

## Blocking changes (if any)

1. <actionable>

## Non-blocking notes

- 
```
