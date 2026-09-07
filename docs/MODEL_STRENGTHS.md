---
title: Model strengths
created: 2026-09-06
updated: 2026-09-06
author: grok
status: active
tags: [docs, routing, models]
---

# Model strengths

Honest map of the current team. Defaults are overridable per task; owner override always wins. The router skill that applies this table is [.grok/skills/interchat-router/SKILL.md](../.grok/skills/interchat-router/SKILL.md). Machine-readable companion (guidance only): [agents/registry.yaml](../agents/registry.yaml). If they drift, **this file wins**.

## Claude

**Strengths.** Long-context analysis. Careful multi-step reasoning. Natural prose. Code quality and high-stakes review. Instruction-following when the spec is dense. Patient synthesis across many files without losing the thread.

**Route here when.** A document or repo needs to be read as a whole. A decision is high-stakes and needs the alternatives written down. Prose that will be published (README, client-facing copy, a letter). A code review where missing a bug is expensive. A handoff packet that arrived messy and needs to be turned into a clean spec.

**Avoid here when.** The answer depends on what happened in the last hour on X or the news. The work is a pile of tool calls (calendar, sheets, interpreter, GitHub click-ops) and no judgment is required. The owner wants an unfiltered take, not a hedged one.

**One-line justifications you may copy.**

- "Claude: long-context analysis and careful reasoning."
- "Claude: natural prose and instruction-following for publishable writing."
- "Claude: high-stakes code review and code quality."

## Grok

**Strengths.** Real-time information via X. Speed. Agentic / tool-use loops in this environment (GitHub, browser, automations). Current events. Unfiltered analysis. Triage — classifying a messy ask and sending it to the right specialist.

**Route here when.** Something is happening *now* (news, X, a live repo, a live preview). The owner wants a direct take, not a committee voice. Work needs GitHub writes, web checks, or other tools Grok already has connected. The task is ambiguous and someone has to route it.

**Avoid here when.** The job is a 80-page close reading. The job is a spreadsheet that wants Code Interpreter. The job is native Google Docs/Sheets/Drive as the system of record. The job is image/audio/video understanding as the primary input.

**One-line justifications you may copy.**

- "Grok: real-time information via X and current events."
- "Grok: speed and agentic/tool-use in the connected workspace."
- "Grok: unfiltered analysis."
- "Grok: default triage for ambiguous work."

## ChatGPT

**Strengths.** Broad ecosystem. Structured outputs (JSON, schemas, strict formats). Function calling. Code Interpreter execution. Integrations across the OpenAI app surface. Familiar to the owner as a daily Plus user.

**Route here when.** The deliverable is structured (JSON schema, table, function-call plan). The work needs a Python/Interpreter pass over a file. The owner wants something that plugs into the ChatGPT side of his life (scheduled tasks, GPTs, connectors). A workflow is "call tools in a strict order and return a schema."

**Avoid here when.** The need is live X signal. The need is a careful adversarial code review of something that will ship. The need is multimodal understanding of a pile of images/video as the main task. The need is a long, careful essay.

**One-line justifications you may copy.**

- "ChatGPT: structured outputs and function calling."
- "ChatGPT: Code Interpreter execution."
- "ChatGPT: broad ecosystem and integrations."

## Gemini

**Strengths.** Multimodal natively (image, audio, video). Native Google Workspace (Docs, Sheets, Drive, Gmail, Calendar) when those connectors are the source of truth. Large-scale data analysis over Workspace-shaped data.

**Route here when.** The primary input is an image, audio, or video. The primary data lives in Google Drive / Docs / Sheets / Gmail / Calendar. A sheet needs to be understood and transformed at scale.

**Avoid here when.** The system of record is this GitHub repo and the tools in play are GitHub-native (Grok or ChatGPT with GitHub already connected will be faster). The owner wants an unfiltered cultural/political take. The work is high-stakes code review.

**One-line justifications you may copy.**

- "Gemini: multimodal (image/audio/video)."
- "Gemini: native Google Workspace data."
- "Gemini: large-scale data analysis."

## Combined-team workflow (example)

Owner: "A client sent a 40-page PDF, a folder of job-site photos, and wants a one-page proposal by morning. Also tell me if anyone on X is complaining about the same kind of vendor this week."

1. **Grok triages.** Classifies the bundle. Writes three packets in [inbox/PENDING.md](../inbox/PENDING.md).
2. **Gemini** takes the photos (multimodal) and drops findings in `research/topics/` plus any extract in `artifacts/`.
3. **Claude** reads the PDF and Gemini's notes, writes the one-page proposal in natural prose, files a decision if pricing policy is involved.
4. **Grok** checks X for live vendor-complaint signal and appends a short current-events note to the research thread.
5. **ChatGPT** turns Claude's proposal plus any numbers into a structured estimate sheet / JSON the owner can paste into a tool, if the owner wants that format.
6. Session close-out in [logs/SESSIONS.md](../logs/SESSIONS.md).

That is the pattern: **Grok triages and routes; Claude verifies and writes the careful artifact; ChatGPT executes structured/tool work; Gemini handles multimodal and Workspace.** Not every task needs all four. Most need one, plus a handoff.

## Override

The owner naming a model is an override. Log it as a decision only if it should stick the next time. Otherwise do the work and move on.
