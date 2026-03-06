# PaperDraftHouse

An AI-augmented academic paper writing pipeline for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and the Claude Desktop app. Takes a Jupyter notebook through 12 structured steps — from analysis to a voice-matched draft — alternating between interactive dialogue, background AI agents, and manual curation.

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

## Installation

Open a terminal, navigate to your paper project folder (ideally containing your `.ipynb` notebook), and clone this repo as the `.claude` directory:

```bash
cd /path/to/my-paper-project
git clone https://github.com/fresva/paper-draft-house .claude
```

That's it. Open the project folder in Claude Code or the Claude Desktop app and start with `/analyze-notebook`.

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI) or Claude Desktop app
- A Jupyter notebook (`.ipynb`) in the project root

## How it works

The pipeline uses two mechanisms from Claude Code:

- **Skills** (`/slash-commands`) — interactive dialogues that run in your main conversation. You and the AI work through decisions together.
- **Agents** — background subagents that run autonomously on well-defined tasks (drafting, reviewing, citation checking).

All intermediate files are stored in `pipeline/` as markdown. Each step reads previous outputs to maintain coherence. The pipeline is designed to be non-linear — you can revisit, re-run, or skip steps as needed.

## License

MIT
