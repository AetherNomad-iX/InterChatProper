---
title: TASK-MVP-001 — Meridian travel-time conflict detection (demo)
created: 2026-09-06
updated: 2026-09-06
author: grok
status: open
tags: [task, demo, meridian]
task_id: TASK-MVP-001
description: >
  Design (not implement) a system for Meridian Visual Planner that detects
  when two calendar events do not overlap in clock time but are geographically
  impossible given travel time, and that proposes alternatives.
created_by: grok
created_at: 2026-09-07T02:10:00Z
updated_at: 2026-09-07T02:10:00Z
project: meridian-visual-planner
priority: normal
required_capabilities:
  - triage
  - structured_output
  - travel_time_geo
  - careful_reasoning
preferred_agent: grok
claimed_by: null
dependencies: []
blocked_by: []
related_tasks:
  - TASK-MVP-001-A
  - TASK-MVP-001-B
  - TASK-MVP-001-C
deliverables:
  - A written design that names inputs, conflict rule, and alternative-proposal rule
  - Child specs from A (scheduling) and B (travel-time)
  - Independent review from C
acceptance_criteria:
  - The motivating example is classified as a conflict (A ends 2:30 PM, B starts 3:00 PM, ~70 miles apart)
  - Pure time-overlap logic is shown to miss that example
  - Alternatives are proposed as a design (shift, remote, buffer), not as fake product UI
  - Explicitly labeled demo; no claim that Meridian already ships this
  - Public-safe: no real personal calendars or addresses
reviewers:
  - claude
review_status: not_requested
result_summary: null
artifacts: []
source_links:
  - https://github.com/AetherNomad-iX/meridian
  - https://meridianvisualplanner.com
  - state/projects/meridian-visual-planner.md
demo: true
history:
  - at: 2026-09-07T02:10:00Z
    by: grok
    from_status: null
    to_status: open
    note: Demo parent opened to exercise coordination protocol. Not a build order.
---

# TASK-MVP-001 — Meridian travel-time conflict detection (demo)

**This is an example/demo task.** It does not mean the feature is implemented in [meridian](https://github.com/AetherNomad-iX/meridian). Do not commit product code into InterChatProper.

## Problem

Meridian Visual Planner is "for the spatial thinker." A calendar that only compares start/end timestamps will happily stack:

| Event | End / start | Distance |
|---|---|---|
| A | ends 2:30 PM | — |
| B | begins 3:00 PM | ~70 miles from A |

Thirty minutes on the clock, seventy miles on the ground. Time-overlap says compatible. Travel-time says impossible.

## Scope

**In:** a design for detection + alternative proposals; split across child tasks A/B/C.  
**Out:** shipping the feature, hitting Maps APIs with secrets, scraping anyone's real calendar.

## Delegation (already opened)

| Child | Target | Slice |
|---|---|---|
| [TASK-MVP-001-A](TASK-MVP-001-A.md) | chatgpt | Scheduling logic (intervals, buffers, "overlap" vs "feasible") |
| [TASK-MVP-001-B](TASK-MVP-001-B.md) | gemini | Geographic / travel-time analysis |
| [TASK-MVP-001-C](TASK-MVP-001-C.md) | claude | Review of assumptions and acceptance criteria (blocked on A,B) |

Grok (or whoever claims this parent) **triages and stitches**. They do not steal A–C unless the owner names them.

### DELEGATION — parent summary

| Field | Value |
|---|---|
| requesting_agent | grok |
| target_agent | (split: chatgpt, gemini, claude) |
| parent_task | TASK-MVP-001 |
| reason_for_delegation | Ambiguous work: Grok triages; ChatGPT structured-exec; Gemini data/geo; Claude verifies. |
| return_location | this file `artifacts:` plus `artifacts/` when specs exist |
