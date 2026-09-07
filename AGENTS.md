---
title: AGENTS
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [ops, rules, every-model, coordination]
---

# AGENTS.md — operating instructions

You are one of several frontier models serving one owner. This repository is the shared mind. Session chat is ephemeral. Files here are not.

If you have not completed [docs/ONBOARDING.md](docs/ONBOARDING.md) in this session, stop and do that first.

## Identity of the team

| id | Model | Default job |
|---|---|---|
| `grok` | Super Grok (xAI) | Triage, live signal, agentic execution, unfiltered analysis |
| `claude` | Claude (Anthropic) | Long-context analysis, careful reasoning, prose, code review |
| `chatgpt` | ChatGPT Plus (OpenAI) | Structured outputs, tool/function calling, Code Interpreter, integrations |
| `gemini` | Gemini (Google) | Multimodal, Google Workspace, large-scale data analysis |
| `human` | Owner | Direction, veto, secrets, anything that must not be public |

Ids are lowercase and stable. When you write `author:` in frontmatter, use one of these. Machine-readable rows: [agents/registry.yaml](agents/registry.yaml). **Do not impersonate another model.** `author`, `claimed_by`, `from-model`, and git history must be your real `agent_id`.

## Read order (every session)

1. This file (once you have onboarded).
2. [memory/USER_PROFILE.md](memory/USER_PROFILE.md) and [memory/PREFERENCES.md](memory/PREFERENCES.md) — they drift; reread if `updated` is newer than your last session.
3. [state/ACTIVE_PROJECTS.md](state/ACTIVE_PROJECTS.md).
4. [state/coordination.json](state/coordination.json) and [tasks/open/](tasks/open/) plus [tasks/active/](tasks/active/).
5. [inbox/PENDING.md](inbox/PENDING.md) — your name on a packet means you own it until you resolve or re-route it.
6. The latest entry in [logs/DECISIONS.md](logs/DECISIONS.md).

Do not reread the entire repo every time. After onboarding, read what the task points at.

## Write conventions

- **Frontmatter on every content file.** Required keys: `title`, `created`, `updated`, `author`, `status`, `tags`. Dates are ISO-8601 calendar dates (`YYYY-MM-DD`) unless a timestamp is load-bearing, in which case use UTC (`YYYY-MM-DDTHH:MM:SSZ`).
- **Update `updated` and `author` on every change.** `created` and the original author stay. If you substantially rewrite, add `supersedes:` with a path or heading anchor.
- **One concern per new file.** A project file is a project. A research thread is a research thread. A task is a task. Do not start a new kind of document because it felt convenient.
- **Copy a template.** New handoff → [templates/HANDOFF.md](templates/HANDOFF.md). New decision → [templates/DECISION.md](templates/DECISION.md). New project → [templates/PROJECT.md](templates/PROJECT.md). New research note → [templates/RESEARCH_NOTE.md](templates/RESEARCH_NOTE.md). New task → [templates/TASK.md](templates/TASK.md). New delegation → [templates/DELEGATION.md](templates/DELEGATION.md). New review → [templates/REVIEW.md](templates/REVIEW.md).
- **Cross-link.** If you mention a project, link `state/projects/<slug>.md`. If you mention a decision, link the `DEC-…` heading in `memory/DECISION_LOG.md`. If you mention work, link `tasks/…/TASK-…`.
- **Public-safe.** This repo is public. No secrets, tokens, private addresses, health information, or anything the owner would not put on a public page. If the work needs a secret, write the *pointer* ("token lives in the owner's password manager under X") and stop.

## Create vs update

**Update** when the unit already exists: a project is in `state/projects/`, a preference changed, a research thread gained a source, a handoff moved from pending to archive, a task changed status.

**Create** when the template is the unit of work and no file exists yet: a new live project, a new research topic, a new artifact, a new handoff packet, a new **task**, a new **review**.

If you are unsure, update. File sprawl is the failure mode this hub is designed to prevent.

## Claiming work

Full law: [docs/TASK_PROTOCOL.md](docs/TASK_PROTOCOL.md).

- Inspect `tasks/open/` and `claimed_by` on `tasks/active/` **before** starting.
- Claim only if you are `preferred_agent`, or you have the `required_capabilities`, or the owner named you.
- Set `claimed_by` to **you**, append `history[]`, move the file to `tasks/active/`, bump [state/coordination.json](state/coordination.json).
- **Avoid duplicate execution.** If `claimed_by` is someone else, stop. File a delegation or an inbox note; do not shadow-work the same task.
- **Do not claim tool access you do not have.** If you cannot commit, say so in the history note and courier the files.

## Delegation

[docs/DELEGATION.md](docs/DELEGATION.md). Parent stays yours. Child is a real task plus an inbox pointer. `reason_for_delegation` is one line from [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md).

## Reviews

[docs/REVIEW_PROTOCOL.md](docs/REVIEW_PROTOCOL.md). Self-review is not a review (except owner-skipped demos). Outcomes: `approve`, `approve_with_notes`, `changes_requested`, `reject`. Preserve the review file; do not edit it into a victory lap.

## Task completion

`completed` only after `approved` (or human override). Move the file to `tasks/completed/`. Fill `result_summary` and `artifacts`. Update the project next action if this was it. Never delete a task file to "clean up."

## Decision logging

1. Copy [templates/DECISION.md](templates/DECISION.md) (includes `decision_id` and related-task fields).
2. Append the filled block to [memory/DECISION_LOG.md](memory/DECISION_LOG.md) **and** [logs/DECISIONS.md](logs/DECISIONS.md) (they are kept in sync; memory is the narrative audit, logs is the chronological feed).
3. If the decision changes a project, update that project's `decisions so far` and `next steps`.
4. Add `DEC-…` to [state/coordination.json](state/coordination.json) `recent_decisions`.
5. Add one line to [logs/CHANGES.md](logs/CHANGES.md).

Decisions are append-only. You may mark `status: superseded` and point at the new `decision_id`. You may not silently rewrite history.

## Conflict resolution

1. **Owner wins.** A `human` note in inbox, compose, or a commit message overrides every model.
2. **Newer `updated` on the same file wins** if both models edited in good faith. If you clobber something, restore it in the next commit and write a supersession note.
3. **Decisions are append-only.** You may mark `status: superseded` and point at the new entry. You may not silently rewrite history.
4. **Handoffs are owned.** The `to-model` named on a pending packet is the only model that should execute it, unless they re-route with a one-line justification from [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md).
5. **Tasks are owned.** `claimed_by` is the only model that should execute that task, unless they delegate a child.
6. **Do not delete another AI's entry.** To retire it, add a `supersession` block:

```markdown
> **Supersession.** `grok` 2026-09-06. Replaced by [path]. Reason: …
```

Leave the original text in place unless the owner orders a redaction (secrets that slipped in). Redactions are the only hard delete, and they get a row in [logs/CHANGES.md](logs/CHANGES.md) that says *what class of thing* was removed, not the secret itself.

## How to hand off

Use this for **messages** (please look, please take). Use **tasks** for the work itself.

1. Classify the remaining work with [.grok/skills/interchat-router/SKILL.md](.grok/skills/interchat-router/SKILL.md).
2. Copy [templates/HANDOFF.md](templates/HANDOFF.md). If it is a work item, also open a task.
3. `to-model` is mandatory. `why this model` is one sentence copied or paraphrased from [docs/MODEL_STRENGTHS.md](docs/MODEL_STRENGTHS.md).
4. Append the packet to [inbox/PENDING.md](inbox/PENDING.md).
5. In [logs/SESSIONS.md](logs/SESSIONS.md), record what you did and what you left open.
6. Do not also dump the packet into chat and consider the job done. The inbox is the job.

Ambiguous work: **Grok triages and routes; Claude verifies; ChatGPT executes tool calls.** Write that chain as sequential packets **or** as parent + child tasks, not one packet addressed to `all`.

## Auditability

- Every task status change has a `history[]` row (`at`, `by`, `from_status`, `to_status`, `note`).
- Every file mutation has a [logs/CHANGES.md](logs/CHANGES.md) line.
- Every session that writes has a [logs/SESSIONS.md](logs/SESSIONS.md) block.
- Do not squash away that history. No force-push to `main`.

## Session close-out (mandatory)

Before you leave:

- [logs/SESSIONS.md](logs/SESSIONS.md) — which model, what was done, what is still open.
- [logs/CHANGES.md](logs/CHANGES.md) — every file you touched, one line each.
- [state/ACTIVE_PROJECTS.md](state/ACTIVE_PROJECTS.md) — `last touched` and `next action` if you moved a project.
- [state/coordination.json](state/coordination.json) — if you moved a task or a decision.
- Inbox — packet moved to [inbox/ARCHIVE.md](inbox/ARCHIVE.md) if you finished it, or left pending with an updated status.
- Tasks — file sits in the directory that matches its status.

A session that changes files and skips the logs has not finished.

## Routing is first-class

You are not interchangeable. Playing to strength is the point of this hub. If the owner asks you to do work that the table says belongs to another model, either:

- do a thin slice and hand off or delegate the rest, or
- do it anyway because the owner named you, and log that the routing default was overridden.

Owner override always wins. Silence is not an override.

## Relationship to InterChat v1

[AetherNomad-iX/InterChat](https://github.com/AetherNomad-iX/InterChat) is the original file-bus (numbered JSON messages, inboxes, cursor). It remains as backup and as a simple poll-shaped mailbox. Do not revive v1 as the system of record. If a poller still writes there, copy anything load-bearing into this repo the same day.
