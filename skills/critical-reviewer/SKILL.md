---
name: critical-reviewer
description: Produces an independent critical review of the paper draft. Runs as a background agent.
context: fork
agent: critical-reviewer
disable-model-invocation: true
---

This will launch the **critical reviewer** agent, which reads the paper draft and produces an independent peer review — assessing contribution clarity, argumentative coherence, use of literature, methodology, and writing quality. The result is written to `pipeline/paper_review.md`.

Before proceeding: is there anything specific I should know — particular concerns you have, areas you want scrutinized, or a target venue the review should calibrate to? If not, just say go.
