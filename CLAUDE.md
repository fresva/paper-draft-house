# Paper Writing Project

This folder is a paper-writing project built around a Python notebook.
The pipeline produces an academic paper through a sequence of skills and agents,
each generating intermediate markdown files stored in `pipeline/`.

---

## Project Structure

```
/
├── <notebook>.ipynb                 # Source notebook
├── pipeline/                        # Intermediate process files (AI-generated)
│   ├── notebook_summary.md          # Step 1: What the notebook does
│   ├── paper_composition.md         # Step 2: APFRQMC style composition
│   ├── key_references.md            # Step 3: Identified key references
│   ├── paper_structure.md           # Step 5: Agreed paper structure
│   ├── paper_draft.md               # Step 6: Full paper draft (preserved as-is)
│   ├── paper_draft_v2.md            # Step 9: Draft with integrated references
│   ├── citation_report.md           # Step 8: Citation assessment
│   ├── paper_review.md              # Step 10: Independent critical review
│   ├── voice_profile.md             # Step 11: Personal writing style profile
│   └── paper_draft_v3.md            # Step 12: Voice-matched final draft
├── samples/                         # User's own writing samples (for voice profiling)
└── literature/                      # Reference files (manually curated)
    ├── *.pdf                        # Downloaded reference PDFs
    └── *.md                         # PDFs converted to markdown for agent access
```

---

## Pipeline Overview

The pipeline has 12 steps, alternating between automated AI work and manual user actions.
Steps marked **SKILL** are interactive. Steps marked **AGENT** run as background subagents.
Steps marked **MANUAL** require user action outside Claude Code.

| Step | Type   | Command                    | Output                                 |
|------|--------|----------------------------|----------------------------------------|
| 1    | SKILL  | `/analyze-notebook`        | `pipeline/notebook_summary.md`         |
| 2    | SKILL  | `/make-composition`        | `pipeline/paper_composition.md`        |
| 3    | AGENT  | `/find-references`         | `pipeline/key_references.md`           |
| 4    | MANUAL | —                          | `literature/` populated with PDFs      |
| 5    | SKILL  | `/make-structure`          | `pipeline/paper_structure.md`          |
| 6    | AGENT  | `/write-draft`             | `pipeline/paper_draft.md`              |
| 7    | MANUAL | —                          | `literature/` extended with all PDFs   |
| 8    | AGENT  | `/assess-citations`        | `pipeline/citation_report.md`          |
| 9    | SKILL  | `/integrate-references`    | `pipeline/paper_draft_v2.md`           |
| 10   | AGENT  | `/review-draft`            | `pipeline/paper_review.md`             |
| 11   | SKILL  | `/build-voice-profile`     | `pipeline/voice_profile.md`            |
| 12   | AGENT  | `/match-voice`             | `pipeline/paper_draft_v3.md`           |

---

## Orientation

On any invocation, determine project state by checking which files exist in `pipeline/`.
The presence of a file means that step has been completed. Do not assume steps run in
strict order — the user may revisit or skip steps. Always read existing pipeline files
before producing new output, to maintain coherence.

---

## Writing Standards

- **Audience:** Information Systems research community, unless the user specifies otherwise. This affects framing, literature selection, methodological expectations, and contribution language.
- **Citation format:** APA 7th edition unless the user specifies otherwise.
- **Citation placeholders:** When a source has not been verified or is not available in `literature/`, use `[CITE: AuthorYear — reason]`. Never hallucinate citations.
- **Register:** Academic but accessible. Avoid jargon where a plain term works. Prefer active voice.
- **Revision, not accumulation:** When updating a pipeline file, revise the full relevant section to maintain coherence. Do not append fragments.

---

## Agent Behaviour Rules

All agents and skills in this pipeline MUST follow these rules:

1. **Never hallucinate citations.** Use placeholder format above.
2. **Read existing pipeline files** before starting work, to maintain coherence across steps.
3. **Report blockers.** If a required input file is missing or incomplete, stop and notify the user rather than proceeding with assumptions.
4. **Background agents** announce when they begin and when they finish, with a one-line summary of what was produced.
