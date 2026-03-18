---
name: assess-citations
description: Assesses citations in the paper draft against source papers in literature/. Runs as a background agent.
context: fork
agent: citation-assessor
disable-model-invocation: true
---

When invoked, ALWAYS use the Agent tool to run the **citation-assessor** agent. Do NOT execute the agent's task inline.

The agent walks through every citation and placeholder in `pipeline/paper_draft.md`, checks each one against the source papers in `literature/`, and produces a structured report with proposed actions (KEEP / REVISE / REPLACE / REMOVE). The result is written to `pipeline/citation_report.md`.

Before proceeding: is there anything specific I should know — citations you're already aware are wrong, new papers you've added to literature/, or sections to prioritize? If not, just say go.
