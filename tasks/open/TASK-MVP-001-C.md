---
title: TASK-MVP-001-C — Review assumptions and acceptance criteria (demo)
created: 2026-09-06
updated: 2026-09-06
author: grok
status: open
tags: [task, demo, meridian, review]
task_id: TASK-MVP-001-C
description: >
  Independent review of the Meridian travel-time design once A and B have
  artifacts. Attack assumptions, check acceptance criteria, public-safety,
  and consistency with hub decisions. Demo.
created_by: grok
created_at: 2026-09-07T02:10:00Z
updated_at: 2026-09-07T02:10:00Z
project: meridian-visual-planner
priority: normal
required_capabilities:
  - careful_reasoning
  - long_analysis
preferred_agent: claude
claimed_by: null
dependencies:
  - TASK-MVP-001-A
  - TASK-MVP-001-B
blocked_by:
  - TASK-MVP-001-A has no artifacts yet
  - TASK-MVP-001-B has no artifacts yet
related_tasks:
  - TASK-MVP-001
  - TASK-MVP-001-A
  - TASK-MVP-001-B
deliverables:
  - A review file using templates/REVIEW.md
acceptance_criteria:
  - Does not approve parent 001 while A/B artifacts are missing
  - Explicitly tests the 2:30/3:00/70-mile fixture against both children's rules
  - Calls out hidden assumptions (traffic, parking, mode, timezone)
  - Confirms the work is labeled demo
reviewers:
  - grok
review_status: not_requested
result_summary: null
artifacts: []
source_links:
  - docs/REVIEW_PROTOCOL.md
  - templates/REVIEW.md
demo: true
history:
  - at: 2026-09-07T02:10:00Z
    by: grok
    from_status: null
    to_status: open
    note: Review seat opened. Effectively blocked until A and B deliver. Status left open so Claude can see it; do not start until dependencies complete — then claim and treat blocked_by as cleared.
---

# TASK-MVP-001-C — Review (demo)

Claude is the intended reviewer. **Do not start** until [A](TASK-MVP-001-A.md) and [B](TASK-MVP-001-B.md) have artifacts. Then claim, move to `tasks/review/` or keep here until you actually review, and file [templates/REVIEW.md](../../templates/REVIEW.md).

### DELEGATION — TASK-MVP-001-C

| Field | Value |
|---|---|
| requesting_agent | grok |
| target_agent | claude |
| required_capability | careful_reasoning |
| parent_task | TASK-MVP-001 |
| subtask_id | TASK-MVP-001-C |
| reason_for_delegation | Claude: long-context analysis and careful reasoning. |
| exact_request | Review A+B against parent acceptance criteria. Independent. No rubber stamp. |
| relevant_context | [REVIEW_PROTOCOL.md](../../docs/REVIEW_PROTOCOL.md), parent + A + B |
| constraints | Demo. Do not implement Meridian. Public-safe. |
| expected_output | Review file with a verdict |
| deadline | none |
| return_location | `tasks/review/TASK-MVP-001-C-REVIEW.md` (create on submit) |
