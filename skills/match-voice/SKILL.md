---
name: match-voice
description: Reshapes the paper draft to match the user's authentic prose style. Runs as a background agent.
context: fork
agent: voice-matcher
disable-model-invocation: true
---

When invoked, ALWAYS use the Agent tool to run the **voice-matcher** agent. Do NOT execute the agent's task inline.

The agent reshapes the prose in `pipeline/paper_draft.md` to match your personal writing style as defined in `pipeline/voice_profile.md`. The result is written to `pipeline/paper_draft_v3.md`.

Before proceeding: is there anything specific I should know — sections to leave untouched, particular style concerns, or anything else? If not, just say go.
