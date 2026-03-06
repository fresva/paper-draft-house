---
name: build-voice-profile
description: Interactive dialogue to build a personal writing style profile from the user's own writing samples. Use when the user invokes /build-voice-profile.
allowed-tools: Read, Write, Glob, Grep
disable-model-invocation: true
---

## Startup

This skill builds a personal writing style profile by analyzing samples of your own writing. The profile captures your sentence patterns, vocabulary, tone, and other stylistic habits — which the voice matcher agent then uses to reshape the paper draft to sound like you wrote it.

Ready to begin?

**Wait for the user to confirm before proceeding.**

## Existing Profile Check

Before doing anything else, ask the user: **Have you already built a voice profile in another project?**

If yes, ask them to copy their existing `voice_profile.md` into `pipeline/voice_profile.md`. Once they confirm the file is in place, read it, show a brief summary, and ask if they want to use it as-is or refine it for this project. If as-is, the skill is done. If refine, proceed to the interview process below with the existing profile as a starting point.

If no, proceed with building a new profile from scratch.

## Preconditions

Verify:
1. `CLAUDE.md` exists in the working directory (or `.claude/CLAUDE.md`).
2. `pipeline/` directory exists.

Check whether a `samples/` folder exists in the project root. If not, ask the user to create it and drop one or two pieces of their own published or polished writing into it — academic papers, book chapters, or similar. Then re-invoke this skill.

## Handling Samples

Once `samples/` contains files, list what's there and assess the material:

**Multiple documents:** Ask the user which document best represents their writing style. Don't analyze all of them by default — the user knows which text sounds most like them.

**Long documents:** Ask the user which sections or pages to focus on. Different parts of a paper have different registers — a literature review reads differently from a discussion section. The user should point you to the parts that feel most authentically *theirs*, not the most formulaic sections.

**Short or single documents:** Proceed directly.

Read only the selected material before beginning the interview.

## Process

### Phase 1 — Initial Analysis

Read the selected sample material and extract initial observations across the profile dimensions listed below. Present these as a draft profile — concrete, specific observations, not generic descriptions.

For each dimension, show:
- What you observe in the samples (with brief examples or quotes)
- A proposed profile rule

Keep it concise — one or two bullet points per dimension, not paragraphs.

### Phase 2 — Interactive Refinement

Walk through the draft profile with the user, dimension by dimension. For each one:
- Ask whether the observation is characteristic or incidental
- Ask whether they want to modify, extend, or remove it
- Let the user add patterns you missed — they know their own voice

Some dimensions may not be visible in the samples. That's fine — ask the user directly: "I don't see a clear pattern for how you handle transitions — is that because you vary them, or because the sample didn't show it?"

Don't rush this. The quality of the voice matching depends entirely on the specificity of this profile.

## Profile Format

The profile must be **terse and actionable** — a style sheet, not an essay. Each dimension should produce 2–5 bullet points of concrete rules that a copyeditor could follow mechanically. The total profile should fit in under 80 lines.

Good: `- Default 12–20 words. Use 25–35 for analytical points only.`
Good: `- Preferred contrast transitions: "However," "Yet," "Rather than." Avoid: "On the other hand," "Conversely."`
Bad: `The author tends to write relatively short sentences, typically in the range of 12–20 words, though longer sentences appear when making analytical points...`

If a rule requires interpretation to apply, it's not specific enough. Rewrite it until it's actionable. Include short lists of examples (preferred words, characteristic phrases, patterns to avoid) where the rule would be ambiguous without them — especially for vocabulary, transitions, and patterns to avoid.

## Profile Dimensions

Analyze and interview across these dimensions. Not all will apply to every writer — skip dimensions that genuinely don't produce useful distinctions.

**Sentence construction**
- Typical sentence length range (short, long, mixed)
- How rhythm varies — do short sentences cluster? Are long sentences used for specific purposes?
- Characteristic sentence openings

**Claim introduction**
- How are arguments introduced and positioned?
- Front-loaded conclusions ("We argue that X") vs. build-up ("Given A, B, and C, it follows that X")?
- How much hedging? What kind?

**Citation integration**
- Front-loaded attribution ("Smith (2015) argues...") or woven into argument ("...as demonstrated in prior work (Smith 2015)")?
- How are citation clusters handled?
- How deeply are sources engaged — summary, critique, synthesis?

**Transitions and flow**
- Characteristic transition words or phrases
- Frequency — every paragraph, only at major turns, rarely?
- How are paragraph boundaries handled — explicit transitions or implicit logical flow?

**Punctuation and structure**
- Use of em-dashes, colons, semicolons, parenthetical asides
- Any distinctive punctuation habits
- **Important:** Flag to the user that LLMs systematically overuse em-dashes and colons in academic prose — far more than most human authors. Show examples from the samples of how the user actually handles these, and ask explicitly: do you want em-dashes and colons used freely, used sparingly, or suppressed almost entirely? This is one of the most visible markers of AI-generated text, so getting it right matters.

**Vocabulary tendencies**
- Characteristic verbs, adjectives, or analytical terms
- Compound constructions or distinctive phrasing
- Words or phrases the author returns to across different texts

**Tone and register**
- Scholarly distance vs. direct address
- Use of "we" vs. "I" vs. passive constructions
- Level of formality — where on the spectrum from conversational to formal?

**Paragraph structure**
- How do paragraphs typically open and close?
- How does argument build within a paragraph?
- Typical paragraph length

**Patterns to avoid**
- Any AI-isms or generic phrases the user specifically wants eliminated
- Any patterns the user recognizes as *not* their voice (e.g., "I never use em-dashes" or "I hate the word 'leverage'")

## Output

Once the profile is agreed, write it to `pipeline/voice_profile.md`:

```markdown
# Voice Profile

**Generated:** <date>
**Based on:** <list of sample files and sections used>

## Sentence Construction
<agreed rules>

## Claim Introduction
<agreed rules>

## Citation Integration
<agreed rules>

## Transitions and Flow
<agreed rules>

## Punctuation and Structure
<agreed rules>

## Vocabulary Tendencies
<agreed rules>

## Tone and Register
<agreed rules>

## Paragraph Structure
<agreed rules>

## Patterns to Avoid
<agreed rules>
```
