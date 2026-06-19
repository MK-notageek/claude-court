# Claude Court — Design System

Every concept doc is a **single self-contained HTML file** (no JS, no external assets) that renders
identically on screen and as print/PDF. It is modelled exactly on `the-value-equation.html` and
`the-context-gap.html`. Reproduce that structure precisely; only swap the palette tokens.

## Non-negotiable structure
- A4 pages: `.page { width:794px; height:1123px; padding:74px 70px 70px; page-break-after:always; }`
- `html,body{ margin:0; background:<palette.backdrop>; }` and `@page{ size:A4; margin:0; }`
- `*{ -webkit-print-color-adjust:exact; print-color-adjust:exact; box-sizing:border-box; }`
- Fonts: `--display:'Futura','Helvetica Neue','Arial Black',Arial,sans-serif;` `--body:'Georgia','Iowan Old Style','Times New Roman',serif;`
- Each page has: `.rhead` (running head L=concept name, R=section), `.rule` (2px bar), `.folio` (page number).
- **8–11 pages.** Page 1 = cover (`.byline` "adapted from Alex Hormozi · <source>", giant `.cover-glyph`, `h1.title`, `.cover-sub`). Last page = a `.cta` block pointing to acquisition.com + a `.closer` line.
- **Every content page carries ONE hand-authored inline `<svg viewBox>` diagram** (~654 wide) with a `.caption`. This is the signature — fraction layouts, 2×2 quadrants, before/after panels, bar comparisons, flow arrows. Never use an image; draw it in SVG.
- Tone: declarative, concrete, Hormozi-style. Short sentences. Real numbers. One idea per page. Original synthesis — never paste book text verbatim.

## Shared CSS tokens (identical across palettes)
Reuse the full `<style>` block from `the-value-equation.html` verbatim, changing only the `:root` color vars below.

## Palettes (swap only these `:root` values)
| palette  | backdrop | paper   | ink     | ink-soft | muted   | line    | accent  | accent-deep | accent-soft | accent-fill | cover-glyph fill |
|----------|----------|---------|---------|----------|---------|---------|---------|-------------|-------------|-------------|------------------|
| violet   | #d8cdf0  | #FFFFFF | #1C1235 | #473A63  | #8C7BA8 | #E5DCF6 | #7C3AED | #4C1D95     | #C9B8F5     | #EDE7FB     | #F3EEFC |
| ember    | #cdbfa8  | #F8F3EA | #1A1510 | #3A2E24  | #8C6F58 | #D8C7B2 | #E2622B | #B23E14     | #F0A06A     | #F6E7D8     | #EFE2CF |
| teal     | #b9d6d2  | #FFFFFF | #0E2A2A | #234746  | #6E908E | #D2E6E3 | #0E9488 | #075E55     | #8FD4CC     | #DCF2EF     | #EAF6F4 |
| amber    | #e6d4a8  | #FFFDF7 | #2A1F08 | #4A3A14  | #9A8552 | #E8DBB6 | #D98A0B | #9A5E04     | #F0CE7E     | #FBF0D6     | #F6ECD2 |
| indigo   | #c3c8ee  | #FFFFFF | #14163A | #2E335E  | #7A7FA6 | #DADCF2 | #4F46E5 | #312C9C     | #A9A8F0     | #E6E5FB     | #EEEEFB |
| emerald  | #b6dcc2  | #FFFFFF | #0C2A18 | #21452F  | #6B9078 | #D0E9D8 | #059669 | #045C42     | #88D2A6     | #DBF2E4     | #E9F7EE |
| crimson  | #e8c4c4  | #FFFDFD | #340F12 | #5E2328  | #A66A6F | #F0D6D8 | #DC2626 | #991218     | #F0A0A0     | #FBE0E0     | #FBEDED |

Map: `--paper`,`--ink`,`--ink-soft`,`--muted`,`--line` direct; `--violet`→accent, `--violet-deep`→accent-deep,
`--violet-soft`→accent-soft, `--violet-fill`/`--violet-fill`→accent-fill. Keep the secondary "destroy/negative"
tone (`--plum*`) as a desaturated tint of the same hue. Set `html,body background` to **backdrop** and
`.cover-glyph` color to the cover-glyph fill. In SVG, hardcode the same hex values (SVG can't read CSS vars).

## Per-concept choices
- **cover-glyph**: one giant character that symbolises the idea (`$`, `÷`, `4`, `∞`, `→`, `%`, `★`).
- Pick the palette from `concept-bank.json` (`palette` field).
- 8–11 pages depending on the concept's natural number of moving parts.

## Quality bar
Match the density and polish of `the-value-equation.html`: pull-quotes (`.pull`), comparison rows
(`.cmp .bad/.good`), accent bands (`.band`), and a strong closing CTA. If a page has no diagram, it's not done.
