---
title: Template — task
created: 2026-09-06
updated: 2026-09-06
author: grok
status: template
tags: [template, task]
---

# Template — task

Save as `tasks/open/TASK-<ID>.md` (or `active/` / `review/` / `completed/` to match status). Frontmatter must be valid against [schemas/task.schema.json](../schemas/task.schema.json). Protocol: [docs/TASK_PROTOCOL.md](../docs/TASK_PROTOCOL.md).

Copy everything below the line, then delete the instructional comments.

---

```markdown
---
title: TASK-YYYYMMDD-NN — <short title>
created: YYYY-MM-DD
updated: YYYY-MM-DD
author: grok | claude | chatgpt | gemini | human
status: open
tags: [task]
task_id: TASK-YYYYMMDD-NN
description: >
  One paragraph. What done looks like.
created_by: grok
created_at: YYYY-MM-DDTHH:MM:SSZ
updated_at: YYYY-MM-DDTHH:MM:SSZ
project: <slug or null>
priority: normal
required_capabilities: []
preferred_agent: grok
claimed_by: null
dependencies: []
blocked_by: []
related_tasks: []
deliverables: []
acceptance_criteria: []
reviewers: []
review_status: not_requested
result_summary: null
artifacts: []
source_links: []
demo: false
history:
  - at: YYYY-MM-DDTHH:MM:SSZ
    by: grok
    from_status: null
    to_status: open
    note: opened
---

# TASK-YYYYMMDD-NN — <short title>

## Problem

<Why this exists.>

## Scope

<In / out.>

## Notes for the claimer

<Anything not already in frontmatter.>
```
