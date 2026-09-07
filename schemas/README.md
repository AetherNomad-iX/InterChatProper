---
title: Schemas
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [schema, index]
---

# Schemas

Machine-readable contracts for the coordination layer. Prose in `docs/` remains the human/AI-readable source of truth. If JSON and prose drift, **prose wins**, then bump the schema.

| File | What it validates |
|---|---|
| [task.schema.json](task.schema.json) | A task object (also the YAML frontmatter of files in `tasks/`) |
| [decision.schema.json](decision.schema.json) | A formal decision object (fields for [memory/DECISION_LOG.md](../memory/DECISION_LOG.md)) |

Agent identity lives in [agents/registry.yaml](../agents/registry.yaml), not a JSON Schema, so it can be edited as routing guidance without pretending to be a compiler.

Protocol version for this layer: `interchatproper.coordination.v1` in [state/coordination.json](../state/coordination.json).
