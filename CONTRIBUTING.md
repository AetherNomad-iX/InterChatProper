---
title: Contributing
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [ops, git, humans, ais]
---

# Contributing

This repo is a memory hub. Humans and AIs both commit. The rules are the same.

Canonical remote: `https://github.com/AetherNomad-iX/InterChatProper`

Backup remote: [AetherNomad-iX/InterChat](https://github.com/AetherNomad-iX/InterChat) (`backup/interchat-proper` branch). Do not treat the backup as writable except when snapshotting.

## Branches

- `main` is the system of record. Keep it green and readable.
- Branch naming:
  - `ai/<model>/<topic>` — e.g. `ai/grok/wise-guides-handoff`
  - `feature/<topic>` — protocol / structural landings (e.g. `feature/multi-agent-coordination`)
  - `human/<topic>`
  - `backup/<snapshot-name>` — snapshots only
- Short-lived branches. Merge or delete. Do not accumulate personal long-lived forks of memory.

## Commits

- Imperative, specific, scoped. `memory: record retainer pricing decision` not `update files`.
- One concern per commit when you can. A session that touches profile + a project + logs may be two or three commits, not one ball of mud.
- Never commit secrets. If you find one, do not `git add` it. Tell the owner. History rewrite is a last resort and never a force-push to `main` from an AI.
- AIs set author to the GitHub identity they are using and name themselves in the commit body (`author: grok`).

## `main` protections (policy)

Even if GitHub branch protection is not on yet, behave as if it is:

- No force-push to `main`.
- No deleting `main`.
- No rewriting published decision-log history.
- Structural changes (new top-level folders, renaming `memory/` etc.) go through a GitHub **issue** first, titled `struct: …`, so the next model can see the proposal. The owner may waive this in chat; note the waiver in [logs/DECISIONS.md](logs/DECISIONS.md).
- **Waiver 2026-09-06:** owner directed the multi-agent coordination tree (`tasks/`, `schemas/`, `agents/`, protocol docs) in chat. Encoded as [DEC-20260906-05](memory/DECISION_LOG.md). No separate `struct:` issue required for that landing.

## How to propose a structural change

1. Open an issue. Explain what is missing, what you want to add or rename, and which files would break.
2. Do not silently invent a parallel tree (`Memory/` vs `memory/`, `projects/` at root vs `state/projects/`).
3. Wait for the owner or a `grok` triage note unless the owner already said "just do it."

## File-level rules

Covered in [AGENTS.md](AGENTS.md). Recap:

- Frontmatter on content files.
- Templates for new units of work.
- Append-only decision log.
- No deleting another AI's entry without a supersession note.

## Review

Claude is the default reviewer for high-stakes prose and code-like configs. Grok is the default reviewer for "is this current" and "did we actually write the logs." The owner is the only approver who matters.

## Backup snapshot

When `main` on this repo moves in a way you would not want to lose:

```text
git fetch origin
git push git@github.com:AetherNomad-iX/InterChat.git origin/main:backup/interchat-proper
```

Log the snapshot in [logs/CHANGES.md](logs/CHANGES.md).
