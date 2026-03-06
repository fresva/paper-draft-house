# PaperDraftHouse

An AI-augmented academic paper writing pipeline for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and the Claude Desktop app. Takes a Jupyter notebook through 12 structured steps — from analysis to a voice-matched draft — alternating between interactive dialogue, background AI agents, and manual curation.

## What it does

The pipeline guides you through turning a data analysis notebook into an academic paper:

1. **Analyze** your notebook — structured summary of data, methods, and findings
2. **Compose** the paper's scholarly identity — area, problem, framing, research question, method, contribution
3. **Identify references** — AI scouts 15–25 key references via web search
4. **Curate literature** — you collect the actual PDFs
5. **Structure the argument** — work out the logical flow and section mapping
6. **Draft the paper** — AI writes a complete first draft
7. **Extend literature** — add remaining source PDFs
8. **Assess citations** — AI checks every citation against your source papers
9. **Integrate references** — walk through citations one by one, resolving placeholders
10. **Critical review** — AI produces an independent peer review
11. **Build voice profile** — analyze your writing samples to capture your style
12. **Match voice** — AI adapts the draft to match your personal writing style

Each step produces a markdown file in `pipeline/`. These are working drafts for you to review and edit — the quality of the final paper depends on your engagement with each intermediate output.

## Installation

Navigate to your paper project folder (ideally containing your `.ipynb` notebook), then clone this repo as the `.claude` directory:

```bash
cd /path/to/my-paper-project
git clone https://github.com/fresva/paper-draft-house .claude
```

That's it. Open the project in Claude Code or the Claude Desktop app and start with `/analyze-notebook`.

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
