---
name: analyze-notebook
description: Reads the source notebook in the project root and produces a structured summary. Use when the user invokes /analyze-notebook. Expects a paper-writing project (CLAUDE.md and pipeline/ must exist).
allowed-tools: Read, Glob, Write, mcp__ide__executeCode
disable-model-invocation: true
---

## Startup

This skill reads the source notebook and produces a structured summary — covering context, purpose, data, methods, findings, and notable aspects. The summary becomes the foundation for all later pipeline steps.

Before starting: is there anything I should know — particular aspects of the notebook to focus on, context about the project that might not be in the notebook, or anything else? If not, just say go.

**Wait for the user to respond before proceeding.**

## Preconditions

Before starting, verify:
1. A `CLAUDE.md` exists in the working directory (confirms this is a paper project).
2. A `pipeline/` directory exists.
3. Exactly one `.ipynb` file exists in the project root. If zero or more than one, ask the user which notebook to analyze.

If any precondition fails, stop and tell the user what is missing.

## Task

Read the notebook and produce a factual summary of what it contains. Describe what is there — do not interpret significance or propose framings. The summary should be detailed enough that someone who has not seen the notebook can understand what was done and what was found.

Use `mcp__ide__executeCode` if needed to inspect dataframes, variable shapes, or outputs that are not visible from the notebook source alone.

## Context Gathering

The notebook documents what was done analytically, but often omits the bigger picture: the organizational setting, the motivation for the study, the backstory that makes the analysis meaningful.

After reading the notebook, check whether it contains contextual information — markdown cells, comments, or introductory text that explain the setting and motivation. Capture whatever is there in the Context section of the output.

Then assess what's missing. If any of the following are unclear or absent from the notebook, ask the user to fill in the gaps before writing the summary:

- **Setting:** What organization, project, or phenomenon was studied? What is the real-world context?
- **Motivation:** Why was this analysis undertaken? What triggered it?
- **Scope:** What time period, population, or boundary conditions define the study?
- **Role of the researcher:** How does the analyst relate to the setting — insider, external observer, consultant, participant?

Ask targeted questions based on what you've seen in the notebook, not generic prompts. For example: "The notebook analyzes meeting transcripts from three teams — what organization is this, and what motivated the study?" is better than "Please describe the study context."

Keep this brief — a few focused questions, not an interview. The goal is to capture enough context that later pipeline steps (especially the style composition) have the full picture.

## Output structure

Write the summary to `pipeline/notebook_summary.md` using this structure:

```markdown
# Notebook Summary

**Source:** <filename.ipynb>
**Generated:** <date>

## Context
The organizational or research setting, the motivation for the study,
and the researcher's relationship to the setting. Drawn from the notebook
where available, supplemented by the user's responses.

## Purpose
What the notebook sets out to do. One or two paragraphs.

## Data
What data sources are used, how they are loaded, and what preprocessing
or cleaning is applied. Note sample sizes, time periods, and key variables.

## Methods
What analytical or computational steps are performed, in the order they appear.
Name specific techniques, models, or algorithms. Note parameter choices where visible.

## Key Findings
What results the notebook produces: tables, figures, statistical outcomes, metrics.
Report them factually — e.g., "Model X achieves accuracy of 0.83" rather than
"Model X performs well."

## Outputs
What artifacts the notebook generates: saved files, exported data, visualizations.

## Notable Aspects
Observations about what is distinctive, surprising, or methodologically interesting
about the work. Not a framing proposal — seeds for creative thinking in later steps.
Examples: unusual data combinations, unexpected results, novel method applications.
```

## Rules

- Do not add interpretation, contribution claims, or framing suggestions. That belongs in step 2.
- If the notebook is incomplete or has errors, describe what is present and note where it breaks.
- If outputs or figures are not rendered in the notebook, say so rather than guessing what they show.
