# 🎤 presentation-prep — Claude Skill

Turns slide source code + rough draft notes into a natural, speakable script. No padding, no AI tone, strictly based on what you wrote.

## How it works

Give it your **slide code** (Markdown / HTML / Rmd / Qmd / LaTeX) and **draft notes** per slide. It outputs a spoken script for every bullet, plot, table, and term — with transitions between slides.

- Never adds content outside your draft
- Asks academic or industry first; if industry, looks up the company's style and adapts
- When a slide's draft is thin, offers concrete expansion options — you decide
- Handles spoken pronunciation of equations, acronyms, and technical terms
- Audience assumed: mixed expert + lay, university level

## Output

```
---
Slide [N]: [Title]

[transition/connection]: "..."
[bullet: ...]: "..."
[plot: ...]: "..."
[transition to next slide]: "..."
---
```

## Installation

1. Download `presentation-prep.skill`
2. In Claude → **Settings → Custom Skills → Install from file**

Triggers on phrases like:
- *"help me present these slides"*
- *"what should I say for this slide"*
- *"prepare a script for my talk"*
- *"presentation notes"* / *"speaking notes"*
- *"how do I explain this slide"*
- pasting slide code + asking for speaking guidance

***
Built with [Claude](https://claude.ai) by Anthropic.
