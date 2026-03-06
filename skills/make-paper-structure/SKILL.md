---
name: make-paper-structure
description: Interactive dialogue to work out the paper's argumentative structure. Use when the user invokes /make-paper-structure. Expects pipeline files from steps 1 and 2 to exist.
allowed-tools: Read, Write, Glob
disable-model-invocation: true
---

## Startup

This skill works out the paper's argumentative structure — the logical moves the paper needs to make to build a convincing case for the contribution. It also agrees on a working title and suggests a section mapping.

Ready to begin, or is there anything I should know first?

**Wait for the user to respond before proceeding.**

## Preconditions

Before starting, verify:
1. `CLAUDE.md` exists in the working directory.
2. `pipeline/notebook_summary.md` exists.
3. `pipeline/paper_composition.md` exists.

Read all existing `pipeline/*.md` files before beginning, including `pipeline/key_references.md` if it exists.

## Purpose

Work out the paper's argumentative structure through iterative dialogue with the user. The goal is to define the logical flow of the argument — what moves the paper needs to make, in what order, to build a convincing case for the contribution.

This is NOT about choosing a section template. Different papers achieve their arguments through different structures. The argument logic comes first; section organization follows from it.

## Process

### Phase 1 — Argument Flow

Start by proposing a sequence of **argumentative moves** the paper needs to make. Each move is a logical step in the overall argument — something the paper must establish before it can proceed to the next step.

For each move, state:
- What it accomplishes (e.g., "Establishes that current approaches to X fail under condition Y")
- Why it's needed at this point in the argument (e.g., "Without this, the reader has no reason to accept the framing")
- What it draws on (e.g., "literature on X", "notebook findings", "methodological justification")

Work this out iteratively with the user. Moves can be reordered, split, merged, or removed. The sequence is ready when the user agrees that following these moves from start to finish would build a convincing argument for the contribution defined in the paper composition.

### Phase 2 — Working Title

Once the argument flow is agreed, propose a working title for the paper. The title should crystallize the contribution — it's not a description of the topic, but a signal of what the paper argues or achieves. Propose 2–3 alternatives and discuss with the user until one is agreed.

### Phase 3 — Section Mapping

Once the argument flow is agreed, propose one possible way to organize the moves into paper sections. This mapping is a suggestion — explicitly mark it as such. Include:
- A proposed section title for each group of moves
- Which moves fall under each section
- Brief notes on scope and approximate emphasis

The user may reorganize, rename, or restructure freely. Some moves may combine into one section; one move may warrant its own section. Follow the user's judgement.

## Dialogue Style

- Propose concretely, then iterate. Don't ask "what sections do you want?" — propose an argument flow and let the user react.
- Challenge weak links in the argument: "This move assumes the reader already accepts X — do we need to establish that first?"
- Flag when the argument flow doesn't support the contribution claim in the composition, or when the contribution is stronger than the argument currently earns.
- Keep the conversation focused on logic and flow, not on prose or wording.

## Output

Once all phases are agreed, write the result to `pipeline/paper_structure.md`:

```markdown
# Paper Structure

**Generated:** <date>
**Based on:** pipeline/notebook_summary.md, pipeline/paper_composition.md

## Working Title

<agreed title>

## Argument Flow

1. **<Move label>**
   <What it accomplishes. Why it's needed here. What it draws on.>

2. **<Move label>**
   <...>

<...continue for all moves...>

## Suggested Section Mapping

### <Section title>
Covers moves: 1, 2
<Brief notes on scope and emphasis>

### <Section title>
Covers moves: 3, 4
<...>

<...continue for all sections...>
```
