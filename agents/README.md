---
title: Agent registry
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [agents, routing]
---

# Agent registry

Machine-readable companion to [docs/MODEL_STRENGTHS.md](../docs/MODEL_STRENGTHS.md).

[registry.yaml](registry.yaml) is **routing guidance**, not a scoreboard and not a guarantee. Product behavior changes. The owner override in chat always wins. If YAML and MODEL_STRENGTHS disagree, **MODEL_STRENGTHS wins**, then someone updates the YAML in the same week.

`agent_id` values must match the ids in [AGENTS.md](../AGENTS.md): `grok`, `claude`, `chatgpt`, `gemini`, `human`.

Do not add a fifth model here without a class it uniquely owns and a row in MODEL_STRENGTHS.
