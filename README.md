# 🎤 presentation-prep — Claude Skill

A Claude skill that turns your raw slide code and rough speaking notes into a natural, speakable presentation script — slide by slide.

No padding. No AI tone. Strictly based on what you actually wrote.

---

## What it does

You give it:
- Your **slide source code** (Markdown, HTML, Rmd, Qmd, LaTeX/Beamer — any format)
- Your **draft notes** per slide (bullet points, rough sentences, keywords — anything)

It gives you back a spoken script for each slide, covering every bullet, plot, table, and term — with natural transitions in and out of each slide.

**What makes it different from just asking Claude to "write a script":**
- It **never invents content** outside your draft — if you didn't write it, it won't say it
- It **asks first**: academic conference or industry? If industry, it looks up the company's communication style and adapts
- When your draft is thin for a slide, it outputs the short version and **offers concrete expansion options** — you decide whether to elaborate
- It tells you how to **pronounce and speak** equations, acronyms, and technical terms out loud
- Audience assumed: **mixed expert + lay, all university level** — it glosses jargon on first use without talking down

---

## Output format

One block per slide:

```
---
Slide [N]: [Title]

[transition/connection]: "..."

[term: XYZ]: "..."
[bullet: bullet text]: "..."
[plot: figure label]: "..."
[table: table label]: "..."

[transition to next slide]: "..."
---
```

Everything in quotes is exactly what you say out loud.

---

## Example

**Input — slide code:**
```markdown
## RMST vs Median Survival
- RMST: area under survival curve up to time τ
- More robust when proportional hazards violated
- [plot: km_curves.png]
```

**Input — your draft notes:**
```
- explain what RMST stands for and the tau thing
- PH assumption fails → RMST still works
- the plot shows two KM curves, shaded area is the RMST difference
- next slide is about trial design
```

**Output:**
```
---
Slide 3: RMST vs Median Survival

[transition/connection]: "Now let's look at the estimand itself — what RMST actually is."

[term: RMST]: "RMST stands for Restricted Mean Survival Time. It's the area under the survival curve up to a fixed time horizon, which we call tau."

[bullet: More robust when proportional hazards violated]: "And the reason we care about it here is that when the proportional hazards assumption fails, RMST still works."

[plot: km_curves.png]: "This plot shows two KM curves. The shaded area between them — that's the RMST difference."

[transition to next slide]: "So with RMST as our estimand, let's see how we build a trial design around it."
---
```

Notice: no content was added beyond the draft. No Cox model, no immunotherapy — because the draft didn't mention them.

---

## Thin draft? It asks, not assumes

When your notes are sparse for a slide, it outputs the short version and offers options:

```
⚠️ Slide 2 draft is thin. Short version above. Possible expansions:
   A) Walk through 1–2 key rows in the table — e.g. sample size, age range
   B) Add one sentence on what the table shows about balance between groups
   C) Keep short — move on
Expand any of these?
```

You pick what to expand. It only adds what you choose.

---

## Supported slide formats

| Format | How slides are detected |
|--------|------------------------|
| Markdown | `---` or `##` headings |
| HTML / reveal.js | `<section>` tags |
| Rmd / Qmd | `---` breaks + chunk delimiters |
| LaTeX / Beamer | `\begin{frame}` blocks |

---

## Installation

1. Download `presentation-prep.skill`
2. In Claude, go to **Settings → Custom Skills → Install from file**
3. Select the `.skill` file

Once installed, trigger it by saying things like:
- *"Help me present these slides"*
- *"Prepare a script for my talk"*
- *"What should I say for each slide?"*
- Or just paste your slide code and draft notes

---

## Made with

Skill designed by @Lillyakasiken with [Claude](https://claude.ai) by Anthropic. Skill format by Anthropic.

Contributions and issues welcome.
