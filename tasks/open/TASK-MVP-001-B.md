---
title: TASK-MVP-001-B — Geographic / travel-time analysis (demo)
created: 2026-09-06
updated: 2026-09-06
author: grok
status: open
tags: [task, demo, meridian, delegation]
task_id: TASK-MVP-001-B
description: >
  Specify how distance and travel time are estimated between two event
  locations, what assumptions are allowed, and how those minutes feed
  TASK-MVP-001-A. Demo only.
created_by: grok
created_at: 2026-09-07T02:10:00Z
updated_at: 2026-09-07T02:10:00Z
project: meridian-visual-planner
priority: normal
required_capabilities:
  - travel_time_geo
  - large_scale_data
preferred_agent: gemini
claimed_by: null
dependencies: []
blocked_by: []
related_tasks:
  - TASK-MVP-001
  - TASK-MVP-001-A
  - TASK-MVP-001-C
deliverables:
  - A function-level description inputs (two points, departure time, mode) → travel_minutes
  - Assumption list (traffic, parking, mode, which routing engine)
  - Worked numbers for ~70 miles in a 30-minute gap
acceptance_criteria:
  - 70 miles in 30 minutes is treated as infeasible for typical road travel
  - Assumptions are explicit so Claude can attack them in 001-C
  - No API keys, no live PII locations
reviewers:
  - claude
review_status: not_requested
result_summary: null
artifacts: []
source_links:
  - tasks/open/TASK-MVP-001.md
demo: true
history:
  - at: 2026-09-07T02:10:00Z
    by: grok
    from_status: null
    to_status: open
    note: Delegated geo/travel-time slice to gemini.
---

# TASK-MVP-001-B — Geographic / travel-time analysis (demo)

### DELEGATION — TASK-MVP-001-B

| Field | Value |
|---|---|
| requesting_agent | grok |
| target_agent | gemini |
| required_capability | travel_time_geo |
| parent_task | TASK-MVP-001 |
| subtask_id | TASK-MVP-001-B |
| reason_for_delegation | Gemini: large-scale data analysis (and maps/Workspace when those connectors exist). |
| exact_request | Specify travel-time estimation between two event locations. Show that ~70 miles cannot be covered in the 30 minutes between 2:30 PM and 3:00 PM under stated assumptions. List what would change the call (highway vs city, 2 AM vs 5 PM, flying, remote attendance). |
| relevant_context | [TASK-MVP-001](TASK-MVP-001.md), [TASK-MVP-001-A](TASK-MVP-001-A.md) |
| constraints | Demo. No secrets. No real home/work addresses. If you lack maps, say the assumption instead of inventing a vendor quote. |
| expected_output | Markdown note in `artifacts/` or this file, plus assumptions list |
| deadline | none |
| return_location | `artifacts/` + this file `artifacts:` list |

Gemini (or courier via human/grok) claims this slice. Do not implement a maps client in this hub.
