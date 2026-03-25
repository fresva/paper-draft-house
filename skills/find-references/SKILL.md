---
name: find-references
description: Identifies key references for the paper based on notebook summary and paper composition. Runs as a background agent.
context: fork
agent: reference-identifier
disable-model-invocation: true
---

When invoked, ALWAYS use the Agent tool to run the agent: '/reference-identifier' 
Do NOT execute the agent's task inline.

The agent reads your notebook summary and paper composition, then uses web search to identify and verify 15–25 key references the paper should engage with. The result is written to `pipeline/key_references.md`.

Before proceeding: is there anything specific I should know — particular literature streams to prioritize, references you already have in mind, or anything to avoid? If not, just say go.
