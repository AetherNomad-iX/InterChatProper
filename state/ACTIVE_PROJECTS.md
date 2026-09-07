---
title: Active projects
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [state, index]
---

# Active projects

Index only. Detail lives in `state/projects/`. Order is priority as of `updated`. Owner may reshuffle; models may not promote a hobby over a paying next action without a decision.

Work-state for individual jobs is [tasks/](../tasks/), summarized in [coordination.json](coordination.json). This table is still the **project** index.

| Name | Goal | Status | Blockers | Next action | Owning model | Last touched |
|---|---|---|---|---|---|---|
| [InterChatProper](projects/interchat-proper.md) | Canonical multi-model memory **and** coordination hub | active | Pollers not wired; coordination PR may still be open | Merge coordination protocol; owner sets Grok automation + ChatGPT scheduled task | grok | 2026-09-06 |
| [Meridian Visual Planner](projects/meridian-visual-planner.md) | Spatial planner product; hub holds design coordination only | active | Demo tasks unclaimed | Claim TASK-MVP-001 children (chatgpt A, gemini B, claude C) — **demo, not a ship order** | grok (triage) | 2026-09-06 |
| [InterChat v1 mailbox](projects/interchat-v1-mailbox.md) | Keep the original bus as backup; snapshot this hub onto it | active | None | Re-snapshot `backup/interchat-proper` after this protocol lands on main | grok | 2026-09-06 |
| [Wise Guides](projects/wise-guides.md) | $300/mo web retainers for small businesses; demo-first client acquisition | active | Book of business still thin | Next session: inventory current demo sites and draft a one-page offer Claude can polish | grok (triage) → claude (copy) | 2026-09-06 |
| [Hayden's Tree Service](projects/haydens-tree-service.md) | Field sales keep paying; web presence does not rot | active | Field time vs. build time | Do not start new site work unless the owner names it; log any live site URL when he provides it | human | 2026-09-06 |
| [House Rogers CV](projects/house-rogers-cv.md) | Professional site stays current enough to hand someone | active | Content drift vs. real life | When profile in this hub changes, sync the public CV or file a handoff | claude | 2026-09-06 |

Parked (not active, do not invent work): language study, Merchant Marine paperwork, other city moves, studio-scale ideas. They become rows here only with a next action.

Related public code the hub may *point at* but not absorb: `willis-property-services`, `noahs-ark-lawn`. `meridian` now has its own project file. Product repos stay product repos.
