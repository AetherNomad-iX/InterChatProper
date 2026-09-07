---
title: Project — InterChatProper
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [project, hub]
---

# InterChatProper

Template: [templates/PROJECT.md](../../templates/PROJECT.md)

## Objective

A public GitHub repository that any of the owner's models can read and write, holding the judgment that does not fit in a context window: who he is, how he wants work, what is live, what was decided, and who should do the next thing.

Success looks like: a cold Claude / ChatGPT / Grok / Gemini session can onboard from [docs/ONBOARDING.md](../../docs/ONBOARDING.md) and take a useful action without the owner re-explaining his life.

## Context

- Owner created [AetherNomad-iX/InterChatProper](https://github.com/AetherNomad-iX/InterChatProper) on 2026-09-06 after v1 mailbox ([InterChat](https://github.com/AetherNomad-iX/InterChat)) proved the wire but not the mind.
- v1 is a numbered JSON bus (Grok ↔ ChatGPT). This repo is the knowledge graph and router.
- Public on purpose. See decision "Public over private" in [memory/DECISION_LOG.md](../../memory/DECISION_LOG.md).

## Decisions so far

- Canonical hub = this repo. Backup = InterChat `backup/interchat-proper`.
- Routing table is first-class ([docs/MODEL_STRENGTHS.md](../../docs/MODEL_STRENGTHS.md)).
- No secrets in git.
- Grok writes the foundation; other models extend, they do not fork the tree.
- **DEC-20260906-05:** hub also hosts a formal task/delegation/review protocol. Inbox stays messages; `tasks/` is work-state.

## Open questions

- Cadence of the Grok automation (hourly vs. on `push_to_branch` for this repo). Owner to pick.
- Whether ChatGPT gets GitHub write or stays on the "print JSON / markdown and the owner files it" path.
- Whether to enable GitHub Discussions or Issues as a human-visible channel. Default: **files only**, issues for `struct:` proposals per [CONTRIBUTING.md](../../CONTRIBUTING.md).

## Next steps

1. Land the foundation (done on main).
2. Snapshot onto InterChat backup branch (done once; re-snapshot after coordination merges).
3. Merge `feature/multi-agent-coordination` (task board + registry + protocols).
4. Owner: create Grok Automation with the poll prompt in this file (now also read `tasks/open/` and `state/coordination.json`).
5. Owner: give ChatGPT [docs/ONBOARDING.md](../../docs/ONBOARDING.md) as a scheduled-task prompt, or a Custom GPT instruction pointing at this repo.
6. First non-Grok model to onboard should leave a session row and, if they can write, a tiny correction to the profile rather than a new manifesto.

## Artifacts

- Router skill: [.grok/skills/interchat-router/SKILL.md](../../.grok/skills/interchat-router/SKILL.md)
- Example artifact: [artifacts/routing-table.v1.json](../../artifacts/routing-table.v1.json)
- Coordination index: [state/coordination.json](../coordination.json)
- Task protocol: [docs/TASK_PROTOCOL.md](../../docs/TASK_PROTOCOL.md)
- Poll prompt (Grok) below, also to be copied into the owner's automation product.

### Grok poll prompt (copy)

You are Grok, agent id `grok`, on InterChatProper (`AetherNomad-iX/InterChatProper`). Follow AGENTS.md. On each run: onboard if needed; read inbox/PENDING.md, state/coordination.json, tasks/open/, tasks/active/, and state/ACTIVE_PROJECTS.md; if a packet or unclaimed qualified task is for you, do it; if human work appeared, file it; update logs/SESSIONS.md and logs/CHANGES.md; do not ping the owner on empty polls. Route with the interchat-router skill and TASK_PROTOCOL. Never commit secrets.

### ChatGPT poll prompt (copy)

You are ChatGPT, agent id `chatgpt`. Read https://github.com/AetherNomad-iX/InterChatProper — start at docs/ONBOARDING.md. Process inbox packets addressed to you and any `tasks/open/` item with preferred_agent chatgpt (e.g. demo TASK-MVP-001-A). If you cannot write to GitHub, output full file contents and paths for the owner to commit. Follow docs/MODEL_STRENGTHS.md and docs/TASK_PROTOCOL.md; do not take Claude's prose jobs or Grok's live-X jobs unless the owner named you.
