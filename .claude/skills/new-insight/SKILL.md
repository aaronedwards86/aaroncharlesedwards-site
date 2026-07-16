---
name: new-insight
description: Draft and publish a new Insights article in Aaron's voice, end to end — pick a theme from the backlog (or take a supplied topic), calibrate against the voice guide and recent articles, draft, self-edit, build the page, wire the index/sitemap, and prepare a LinkedIn post. Use when asked to write a new blog/insights article, run the content loop, or work the article backlog.
---

# New Insight — the content engineering loop

Publish one article per invocation. Everything the loop needs lives in `content-engine/`.

## Inputs

- **With an argument** (`/new-insight <topic or backlog #>`): use that topic. If it matches a
  backlog row, adopt its angle; otherwise treat as a new idea and add it to `BACKLOG.md` first.
- **Without an argument**: pick the top `ready` item in `content-engine/BACKLOG.md`.

## Step 1 — Calibrate (do not skip)

Read, in order:
1. `content-engine/VOICE.md` — sentence mechanics, structural moves, banned patterns, hard boundaries
2. `content-engine/THEMES.md` — the pillar for this piece, the facts bank, the approved link library
3. The **two most recently published** articles under `insights/` (see the Published table in
   `BACKLOG.md`) — read the full body text to load the voice

Mark the backlog item `drafting`.

## Step 2 — Research

- Only facts from the THEMES facts bank or sources you verify live this session.
- Verify every external URL you intend to link (WebFetch or curl; some domains are blocked by
  network policy — a link already in the approved library may be used even if unreachable from
  the sandbox, since it was verified when added; anything NEW must be verified now or left out).
- **Never fabricate** press links, client names, campaign results, metrics, or quotes.
- Check the hard rules in `THEMES.md` before outlining. If the angle brushes against them
  (M&A, financials, internal tech), reshape the angle or stop and ask.

## Step 3 — Draft

- 1,000–1,800 words. Structure per VOICE.md: cold open on the real question → thesis as
  mechanism → 3–5 H2 sections → an honest-account passage → kicker under 20 words.
- 2–5 external links, 1–2 internal cross-links to earlier insights, final link to `/#press`.
- Write the 3 FAQ items (SEO-oriented, no double quotes in answers — they go into JSON-LD).
- Choose exactly 2 tags, reusing existing ones where possible.

## Step 4 — Self-edit

Run the checklist at the bottom of `VOICE.md`. Cut 10%. Re-verify zero em dashes, zero
banned words, honest-account present, kicker lands.

## Step 5 — Build the page

1. `mkdir insights/<slug>/` — slug: short, kebab-case, keyword-bearing.
2. Copy `content-engine/TEMPLATE.html` → `insights/<slug>/index.html`; fill every `{{TOKEN}}`
   (token list is documented at the top of the template).
3. Hero: if a photo is provided use `hero.jpg`; otherwise create a minimal SVG in the site's
   established style (720×360, `#fafafa` ground, `#111` ink, Inter, letter-spaced small caps —
   see the SVGs in `insights/4-months-down-the-ai-engineering-hole/` and
   `insights/the-sibling-system/`).
4. Read time = round(words / 200).

## Step 6 — Wire

Follow the publishing checklist in `content-engine/README.md`:
- Card at the TOP of the grid in `insights/index.html` (copy an existing `.article-card`).
- `sitemap.xml`: new `<url>` (priority 0.7, monthly) + bump `/insights/` `<lastmod>`.
- QA: `grep -rn "{{" insights/<slug>/` must return nothing; validate all three JSON-LD blocks
  (`python3` + `json.loads` on the extracted script bodies); click-check internal paths exist.
- Move the backlog row to `published` with today's date.

## Step 7 — Distribute + ship

- Draft a LinkedIn post (Aaron's distribution channel): 80–150 words, same voice, no hashtag
  soup (0–3 hashtags), ends with the article URL. Include it in your final message — it does
  not go on the site.
- Commit on a feature branch with a descriptive message; push and open a **draft PR**.
  The loop never merges its own work — Aaron reviews and merges.
