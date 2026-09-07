---
title: Template — decision
created: 2026-09-06
updated: 2026-09-06
author: grok
status: template
tags: [template, decision]
---

# Template — decision

Append a filled copy to **both** [memory/DECISION_LOG.md](../memory/DECISION_LOG.md) (narrative, newest first) and [logs/DECISIONS.md](../logs/DECISIONS.md) (feed). Schema: [schemas/decision.schema.json](../schemas/decision.schema.json). Status: `proposed` · `accepted` · `rejected` · `superseded` · `executed`.

New entries (DEC-20260906-05 onward) use the full field set. Older entries keep their original table; backfill `decision_id` when you touch them, do not rewrite their prose.

```markdown
## DEC-YYYYMMDD-NN — <short name>

| Field | Value |
|---|---|
| decision_id | DEC-YYYYMMDD-NN |
| Date | YYYY-MM-DD |
| question | <the question being answered> |
| context | <links, situation> |
| options_considered | <at least one real alternative, or "none — owner directive"> |
| Decision | <the call, in one or two sentences> |
| rationale | <why this, not the alternative> |
| decided_by | grok \| claude \| chatgpt \| gemini \| human |
| reviewed_by | <ids or none> |
| related_tasks | TASK-… or none |
| affected_projects | <slugs> |
| supersedes | DEC-… or none |
| Outcome | proposed \| accepted \| rejected \| superseded \| executed |
```

The short aliases `Decision` / `Reasoning` / `Alternatives considered` / `Model that proposed it` / `Outcome` from v1 remain valid on historical entries.

If this supersedes an older entry, set `supersedes` and mark the old entry `superseded` without deleting it.
