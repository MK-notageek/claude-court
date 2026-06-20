# 🏛️ Claude Court

Alex Hormozi's frameworks, redrawn one a day in Vibeera's house design system —
print-grade, self-contained HTML visual breakdowns with hand-authored SVG diagrams.

**Live:** https://mk-notageek.github.io/claude-court/

## How it works
A daily routine (07:00 PKT) picks the next 2 unused concepts from `engine/concept-bank.json`,
generates two HTML breakdowns into `concepts/`, updates the gallery (`index.html`), commits,
pushes (GitHub Pages serves them), and posts the links to Slack `#claude-court`.

- `engine/concept-bank.json` — the rotating concept list + done/pending state
- `engine/DESIGN-SYSTEM.md` — the exact design spec + palettes
- `engine/daily-routine.md` — the step-by-step the daily agent follows
- `concepts/` — every published breakdown (permanent)

Each doc is a transformative educational synthesis of a public framework — never verbatim book text.

<!-- deploy check: 2026-06-20T08:29Z -->
