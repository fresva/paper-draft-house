---
name: integrate-references
description: Walks the user through the citation report, resolving each citation one at a time. Use when the user invokes /integrate-references. Expects pipeline/citation_report.md and pipeline/paper_draft.md to exist.
allowed-tools: Read, Edit, Write, Glob, Grep
disable-model-invocation: true
---

## Startup

This skill walks you through the citation report one entry at a time — for each citation, you'll see the assessment and proposed action, then decide whether to keep, revise, replace, or remove it. Changes are applied to a new file (`pipeline/paper_draft_v2.md`) so the original draft from the paper-writer is preserved for traceability.

Before starting: is there anything I should know — citations you already know are wrong, new papers you've added to literature/, or sections to prioritize? If not, just say go.

**Wait for the user to respond before proceeding.**

## Preconditions

Before starting, verify:
1. `CLAUDE.md` exists in the working directory.
2. `pipeline/citation_report.md` exists.
3. `pipeline/paper_draft.md` exists.

If either is missing, stop and tell the user which file is needed.

Read `pipeline/citation_report.md` in full before beginning. Do NOT read all of `literature/` — source papers are read selectively during the process.

Then copy `pipeline/paper_draft.md` to `pipeline/paper_draft_v2.md`. All edits during this skill are made to the cited copy — never modify `pipeline/paper_draft.md`.

## Process

Work through the citation report entry by entry, in the order they appear. For each entry:

1. **Show the citation in context.** Quote the relevant passage from the draft so the user can see how it's currently used.

2. **Show the assessment.** Present the citation assessor's verdict and proposed action (KEEP / REVISE / REPLACE / REMOVE).

3. **Ask the user what to do.** The user may:
   - **Approve** the proposed action as-is
   - **Modify** — accept the direction but adjust the specifics
   - **Override** — reject the proposal and give a different instruction
   - **Skip** — leave this citation unchanged for now
   - **Inspect source** — if the user wants to check the assessor's reading, look up the relevant passage in `literature/` using Glob and Grep. Read only the specific source, not the entire folder.

4. **Apply the change.** Edit `pipeline/paper_draft_v2.md` to implement the agreed action. For REVISE or REPLACE, rewrite the surrounding sentence or passage to integrate the new or revised citation naturally — don't just swap a name.

### Placeholder Citations

For `[CITE: AuthorYear — reason]` placeholders, the process is the same but the options differ:
- **Resolve** — replace with a real citation (from the assessor's suggestion or the user's choice)
- **Keep placeholder** — the user hasn't found a suitable source yet
- **Remove** — the argument doesn't actually need a citation here

## Pacing

Don't rush. Present one citation at a time and wait for the user's response before moving to the next. If the report is long, offer to pause and resume later — the user can re-invoke the skill to continue where they left off.

## After Completion

When all entries have been addressed, summarize what was done: how many citations were kept, revised, replaced, removed, and how many placeholders remain unresolved.
