---
title: Logs — changes
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [logs, changelog]
---

# Changes

Every file mutation, actor, reason. Newest at the top. One line per file is enough; group a foundation pass as a batched block.

---

## 2026-09-06 — grok — multi-agent coordination protocol (DEC-20260906-05)

| File | Actor | Reason |
|---|---|---|
| README.md | grok | Coordination section, workflow diagram, map, onboarding list, first action |
| AGENTS.md | grok | Claim, duplicate-work, delegation, review, completion, impersonation, tool-access, auditability |
| CONTRIBUTING.md | grok | tasks/ is an allowed tree; owner waived struct-issue for this spec |
| docs/ONBOARDING.md | grok | Registry, task protocol, coordination.json, open/active tasks |
| docs/MODEL_STRENGTHS.md | grok | Pointer to agents/registry.yaml |
| docs/TASK_PROTOCOL.md | grok | **new** lifecycle, transitions, e2e Meridian example |
| docs/DELEGATION.md | grok | **new** packet contract |
| docs/REVIEW_PROTOCOL.md | grok | **new** review lifecycle |
| .grok/skills/interchat-router/SKILL.md | grok | Pointer to task protocol after classify |
| agents/README.md | grok | **new** |
| agents/registry.yaml | grok | **new** grok/claude/chatgpt/gemini/human as guidance |
| schemas/README.md | grok | **new** |
| schemas/task.schema.json | grok | **new** |
| schemas/decision.schema.json | grok | **new** |
| templates/TASK.md | grok | **new** |
| templates/DELEGATION.md | grok | **new** |
| templates/REVIEW.md | grok | **new** |
| templates/DECISION.md | grok | Extended with decision_id and related fields; kept v1 aliases |
| tasks/README.md | grok | **new** board rules; inbox vs tasks |
| tasks/open/TASK-MVP-001.md | grok | **new** demo parent |
| tasks/open/TASK-MVP-001-A.md | grok | **new** chatgpt scheduling slice |
| tasks/open/TASK-MVP-001-B.md | grok | **new** gemini geo slice |
| tasks/open/TASK-MVP-001-C.md | grok | **new** claude review slice |
| tasks/active/README.md | grok | **new** bucket |
| tasks/review/README.md | grok | **new** bucket |
| tasks/completed/README.md | grok | **new** bucket |
| state/coordination.json | grok | **new** manual index |
| state/ACTIVE_PROJECTS.md | grok | Meridian row; InterChatProper next action |
| state/projects/meridian-visual-planner.md | grok | **new** slug for the demo task |
| state/projects/interchat-proper.md | grok | Note coordination layer |
| memory/DECISION_LOG.md | grok | DEC-20260906-05; backfilled decision_id on older entries |
| logs/DECISIONS.md | grok | Mirror DEC-20260906-05 |
| logs/SESSIONS.md | grok | This session |
| logs/CHANGES.md | grok | This block |
| inbox/PENDING.md | grok | Inbox vs tasks distinction; pointer to demo tasks |
| artifacts/README.md | grok | Link schemas |

---

## 2026-09-06 — grok — foundation pass

| File | Actor | Reason |
|---|---|---|
| README.md | grok | Purpose, onboarding, routing summary, not-this |
| AGENTS.md | grok | Operating law |
| CONTRIBUTING.md | grok | Git rules for humans and AIs |
| .gitignore | grok | Standard noise + env |
| docs/ONBOARDING.md | grok | First-contact sequence |
| docs/MODEL_STRENGTHS.md | grok | Honest capability map |
| .grok/skills/interchat-router/SKILL.md | grok | Classifier + handoff packet |
| memory/USER_PROFILE.md | grok | Public-safe owner profile |
| memory/PREFERENCES.md | grok | v1 preferences |
| memory/DECISION_LOG.md | grok | Initial four decisions |
| state/ACTIVE_PROJECTS.md | grok | Index |
| state/projects/*.md | grok | Five live projects |
| research/** | grok | Index, three threads, two raw dumps |
| inbox/PENDING.md | grok | Three open packets |
| inbox/ARCHIVE.md | grok | Foundation packet closed |
| logs/* | grok | Decisions, sessions, this file |
| templates/* | grok | Four skeletons |
| artifacts/* | grok | Consumer-file rules + routing-table JSON |
| legacy/README.md | grok | Pointer to v1 |

Later snapshots to InterChat backup belong as their own row once pushed.
