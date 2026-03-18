---
name: make-composition
description: Interactive dialogue to define the paper's scholarly identity using the APFRQMC framework. Use when the user invokes /make-composition. Expects pipeline/notebook_summary.md to exist.
allowed-tools: Read, Write, Glob
disable-model-invocation: true
---

## Startup

This skill is an interactive dialogue to define the paper's scholarly identity — working through area of concern, problem, framing, research question, method, and contribution. It's a creative conversation, not a form to fill in.

Ready to begin, or is there anything I should know first?

**Wait for the user to respond before proceeding.**

## Preconditions

Before starting, verify:
1. `CLAUDE.md` exists in the working directory.
2. `pipeline/notebook_summary.md` exists. If not, tell the user to run `/analyze-notebook` first.

Read `pipeline/notebook_summary.md` before beginning.

## Purpose

Guide the user toward a paper composition through open-ended creative dialogue. The conversation should feel like a research meeting between colleagues — exploratory, iterative, building toward clarity over multiple exchanges. NOT a form to fill in.

The framework draws loosely on Mathiassen, Chiasson, and Germonprez (2012), adapted for general use beyond action research.

## Process

### Phase 1 — Open Exploration

Start here. Do NOT propose framework components yet. Instead, have a conversation to understand the user's thinking. Ask questions like:

- What do you find most interesting in the data?
- Was there anything surprising or unexpected?
- Do you have a hunch about what story this tells?
- Is there a theoretical angle or body of literature you're already thinking about?
- Is there a target venue or audience in mind?
- What would you want a reader to take away from this paper?

Ask ONE or TWO questions at a time. Wait for the response. Follow up on what the user says. Don't rush to categorize — listen for what energizes them, what they keep coming back to, what they're uncertain about.

This phase may take several exchanges. That's fine. The quality of the composition depends on the quality of this exploration.

### Phase 2 — Shaping

As themes emerge from the conversation, begin informally mapping them to the APFRQMC components. Don't present a full framework yet — instead, reflect the user's thinking back through the framework's lens:

- "It sounds like your area of concern is somewhere around X — does that feel right?"
- "That hunch about Y could become your conceptual framing."
- "The gap you're describing sounds like it could sharpen into a research question about Z."

Work one or two components at a time, following wherever the conversation naturally leads. Some components will crystallize early; others will stay fuzzy until late. That's normal — the components are interdependent, and movement on one often unlocks another.

Keep pushing for specificity: "That's a broad area — what part of it does your data actually speak to?" And flag tensions: "That framing pulls the paper in a different direction from what you said about the contribution — which one do you want to follow?"

### Phase 3 — Crystallizing

Once the thinking has converged enough that most components have a rough shape, draft precise formulations. Each component should be 2–4 sentences — tight enough to be useful, not so long that it becomes fuzzy.

Present the full composition and check coherence:
- Does RQ connect P to F?
- Does C respond directly to RQ?
- Is C grounded in what the notebook actually shows?
- Does M support the kind of claim C makes?

Push back on weak spots. Iterate until the user confirms they are satisfied with the whole composition.

## The APFRQMC Components

These are the six components the conversation should eventually produce. They are reference definitions, not a script to follow.

**A — Area of Concern:** The broad domain or body of literature the paper addresses. What scholarly conversation does this paper enter?

**P — Problem:** The concrete, real-world problem motivating the work. Not the research gap — the practical challenge that makes this work matter.

**F — Conceptual Framing:** The theoretical lens or framework used to interpret the problem and structure the analysis. What concepts does the paper think with?

**RQ — Research Question:** The precise question the paper answers. Should connect P (why it matters) to F (how we approach it) and point toward C (what we learn).

**M — Method:** The research approach used. Should be specific enough to evaluate — not just "qualitative study" but the concrete design.

**C — Contribution:** What the paper adds to knowledge. Can be theoretical, practical, or methodological. Should respond directly to RQ and be grounded in what the notebook actually shows.

## Dialogue Style

- Be a thinking partner, not a scribe. Challenge weak ideas, but also search for golden nuggets in fuzzy thinking and help develop them.
- Ask short questions. Give short responses. Match the user's energy and pace.
- Do NOT dump multiple component proposals at once. One thought, one question, one exchange at a time.
- When the user is stuck, try a different angle rather than pressing harder on the same one.

## Output

Once all six components are agreed, write the result to `pipeline/paper_composition.md` using this structure:

```markdown
# Paper Composition

**Generated:** <date>
**Based on:** pipeline/notebook_summary.md

## Area of Concern (A)
<agreed text>

## Problem (P)
<agreed text>

## Conceptual Framing (F)
<agreed text>

## Research Question (RQ)
<agreed text>

## Method (M)
<agreed text>

## Contribution (C)
<agreed text>
```
