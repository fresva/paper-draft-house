# PaperDraftHouse

An AI-augmented academic paper writing pipeline for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and the Claude Desktop app. Takes a Jupyter notebook through 12 structured steps — from analysis to a voice-matched draft — alternating between interactive dialogue, background AI agents, and manual curation.

## Why this exists

Academic writing is changing. AI tools are increasingly capable of supporting research processes, from literature discovery to drafting prose. However, as a research community, we are not in consensus on how these tools should be used. This pipeline is created to explore what AI-augmented paper writing looks like in practice: what works, what doesn't, where human judgement is irreplaceable, and where AI support is genuinely useful.

By making the process structured and transparent — with every intermediate step producing a reviewable artifact — the pipeline is also meant to provoke discussion. The technology is here. Ignoring it won't make it go away. Exploring it openly seems more productive than pretending the question doesn't exist.

## What it does

The pipeline guides you through turning a data analysis notebook into an academic paper. Each step produces a markdown file in `pipeline/` — a working draft for you to review and edit before moving on. The quality of the final paper depends on your engagement with each intermediate output.

| Step | What happens | Output |
|------|-------------|--------|
| 1 | **Analyze notebook** — interactive dialogue to summarize data, methods, and findings | `notebook_summary.md` |
| 2 | **Compose scholarly identity** — interactive dialogue to define area, problem, framing, RQ, method, contribution | `paper_composition.md` |
| 3 | **Identify references** — AI scouts 15–25 key references via web search | `key_references.md` |
| 4 | **Curate literature** — you collect and add the actual PDFs | `literature/` |
| 5 | **Structure the argument** — interactive dialogue to work out logical flow and section mapping | `paper_structure.md` |
| 6 | **Draft the paper** — AI writes a complete first draft | `paper_draft.md` |
| 7 | **Extend literature** — you add remaining source PDFs | `literature/` |
| 8 | **Assess citations** — AI checks every citation against your source papers | `citation_report.md` |
| 9 | **Integrate references** — interactive walk-through, resolving citations one by one | `paper_draft_v2.md` |
| 10 | **Critical review** — AI produces an independent peer review | `paper_review.md` |
| 11 | **Build voice profile** — interactive analysis of your writing samples | `voice_profile.md` |
| 12 | **Match voice** — AI adapts the draft to match your personal writing style | `paper_draft_v3.md` |

## Your role in the pipeline

This is not an automated paper generator. Each step produces an intermediate markdown file — a starting point for your judgement, not a finished output. You shape these into a paper worth publishing.

Before moving to the next step, open the file and review it critically. Fix factual errors. Sharpen vague formulations. Remove claims you don't stand behind. Add context the AI couldn't know. Do your job as a researcher! Each step builds on the output of previous steps, so problems left unaddressed will carry forward and compound.

The interactive steps (1, 2, 5, 9, 11) involve direct dialogue — the AI asks questions and you make decisions together. The agent steps (3, 6, 8, 10, 12) run autonomously and produce drafts that need your judgement afterward. Neither kind of step produces finished output. The pipeline gives you a scaffold; the paper is yours to build.

## Installation

Open a terminal, navigate to your paper project folder (ideally containing your `.ipynb` notebook), and clone this repo as the `.claude` directory:

```bash
cd /path/to/my-paper-project
git clone https://github.com/fresva/paper-draft-house .claude
```

That's it. Open the project folder in Claude Code or the Claude Desktop app and start with `/analyze-notebook`.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI) or Claude Desktop app (use the **Code** tab, not Cowork)
- A Jupyter notebook (`.ipynb`) in the project root

## How it works

The pipeline uses two mechanisms from Claude Code:

- **Skills** (`/slash-commands`) — interactive dialogues that run in your main conversation. You and the AI work through decisions together.
- **Agents** — background subagents that run autonomously on well-defined tasks (drafting, reviewing, citation checking).

All intermediate files are stored in `pipeline/` as markdown. Each step reads previous outputs to maintain coherence. The pipeline is designed to be non-linear — you can revisit, re-run, or skip steps as needed.

## License

MIT
