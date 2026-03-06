---
name: paper-writer
description: Writes a full first draft of the paper based on the pipeline files. Runs as a background agent.
context: fork
agent: paper-writer
disable-model-invocation: true
---

This will launch the **paper writer** agent, which reads all pipeline files and writes a complete first draft following the agreed argument flow. Citations are drawn from training knowledge where confident; otherwise placeholders are used. The result is written to `pipeline/paper_draft.md`.

Before proceeding: is there anything specific I should know — particular emphasis, length constraints, sections to handle differently, or anything else? If not, just say go.
