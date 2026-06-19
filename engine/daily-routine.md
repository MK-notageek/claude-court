# Claude Court — Daily Routine (runs 07:00 PKT)

You are JARVIS generating Abdul's daily Hormozi concept breakdowns. Run these steps in order.

## 1. Pick today's concepts
- Read `engine/concept-bank.json`. Select the **first 2 concepts with `status: "pending"`**.
- If fewer than 2 are pending, reset every concept's `status` back to `"pending"` (new cycle), then pick the first 2.

## 2. Generate 2 docs
For each selected concept, write a single self-contained HTML file to `concepts/<slug>.html`, following
`engine/DESIGN-SYSTEM.md` exactly — A4 pages, the concept's `palette`, 8–11 pages, **one inline-SVG diagram per
content page**, cover + closing CTA. Match the polish of `concepts/the-value-equation.html` (the gold standard).
Write original educational synthesis of the framework — never reproduce book/transcript text verbatim.

## 3. Update the gallery + bank
- Add a card for each new concept to `index.html` (newest first).
- In `concept-bank.json`: set each generated concept `status: "done"`, add `"date"` (today, YYYY-MM-DD) and
  `"url": "https://mk-notageek.github.io/claude-court/concepts/<slug>.html"`. Set top-level `last_run` to today.

## 4. Publish
```
cd "<repo>"
git add -A && git commit -m "Court: <Title A> + <Title B> (<YYYY-MM-DD>)" && git push
```
GitHub Pages serves them within ~60s at the URLs above.

## 5. Post to Slack (#claude-court)
Post one message to channel `#claude-court` with both links, e.g.:
> 🏛️ *Claude Court — <date>*
> Two Hormozi breakdowns are live, sir:
> • *<Title A>* — <url A>
> • *<Title B>* — <url B>
> Gallery: https://mk-notageek.github.io/claude-court/

Prefer the Slack MCP (`slack_send_message`). If unavailable in this runtime, POST to the webhook URL stored in
`engine/.slack-webhook` (gitignored) via curl as a fallback.

## Notes
- Keep links permanent; never delete old concepts.
- Vary the cover-glyph and palette per concept so the archive stays visually distinct.
