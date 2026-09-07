---
title: Template — delegation
created: 2026-09-06
updated: 2026-09-06
author: grok
status: template
tags: [template, delegation]
---

# Template — delegation

Protocol: [docs/DELEGATION.md](../docs/DELEGATION.md).

1. Create the child task from [TASK.md](TASK.md).
2. Paste the block below into the child task body **and** a short pointer into [inbox/PENDING.md](../inbox/PENDING.md).

```markdown
### DELEGATION — <subtask_id>

| Field | Value |
|---|---|
| requesting_agent | grok \| claude \| chatgpt \| gemini \| human |
| target_agent | grok \| claude \| chatgpt \| gemini \| human \| (empty) |
| required_capability | <registry id if target_agent empty> |
| parent_task | TASK-… |
| subtask_id | TASK-…-A |
| reason_for_delegation | <one line from docs/MODEL_STRENGTHS.md> |
| exact_request | <the actual ask> |
| relevant_context | <links> |
| constraints | <public-safe, time, do not implement in this hub, …> |
| expected_output | <files / schema / review> |
| deadline | YYYY-MM-DD \| none |
| return_location | <path in this repo> |
```
