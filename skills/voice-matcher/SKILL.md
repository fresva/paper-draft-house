---
name: voice-matcher
description: Reshapes the paper draft to match the user's authentic prose style. Runs as a background agent.
context: fork
agent: voice-matcher
disable-model-invocation: true
---

This will launch the **voice matcher** agent, which reshapes the prose in `pipeline/paper_draft.md` to match your personal writing style as defined in `pipeline/voice_profile.md`. The result is written to `pipeline/paper_draft_v3.md`.

Before proceeding: is there anything specific I should know — sections to leave untouched, particular style concerns, or anything else? If not, just say go.
