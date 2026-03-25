---
name: write-draft
description: Writes a full first draft of the paper based on the pipeline files. Runs as a background agent.
context: fork
agent: paper-writer
disable-model-invocation: true
---

When invoked, ALWAYS use the Agent tool to run the agent: '/paper-writer'
Do NOT execute the agent's task inline.

The agent is instructed to read all pipeline files and writes a complete first draft following the agreed argument flow. Citations are drawn from training knowledge where confident; otherwise placeholders are used. The result is written to `pipeline/paper_draft.md`.

**Before proceeding**, always ask: Is there anything specific I should consider — particular emphasis, length constraints, sections to handle differently, complementary, or something else? Otherwise, just say go.
