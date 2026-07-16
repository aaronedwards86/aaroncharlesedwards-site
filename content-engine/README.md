# Content Engine

A repeatable engineering loop for publishing Insights articles on aaroncharlesedwards.com,
written in Aaron's voice, grounded in his established themes.

## The Loop

```
IDEATE ──► SELECT ──► CALIBRATE ──► DRAFT ──► EDIT ──► BUILD ──► WIRE ──► DISTRIBUTE
   │                                                                        │
   └────────────────────── BACKLOG.md tracks state ─────────────────────────┘
```

1. **Ideate** — new article ideas go into `BACKLOG.md`, tagged to a theme pillar from `THEMES.md`.
2. **Select** — pick the top `ready` item from the backlog (or a topic supplied directly). Mark it `drafting`.
3. **Calibrate** — re-read `VOICE.md` plus the two most recently published articles before writing a word.
4. **Draft** — write the piece per `VOICE.md`. Facts and links come only from the facts bank in
   `THEMES.md` or from sources verified during the session. Never invent press links, client names,
   metrics, or quotes.
5. **Edit** — run the self-edit checklist at the bottom of `VOICE.md`. Cut 10% on the second pass.
6. **Build** — copy `TEMPLATE.html` to `insights/<slug>/index.html` and fill every `{{TOKEN}}`.
   Create a hero (photo `hero.jpg` if one exists, otherwise a minimal SVG in the established style —
   see `insights/4-months-down-the-ai-engineering-hole/ai-engineering-journey.svg` and
   `insights/the-sibling-system/sibling-system.svg`).
7. **Wire** — see the publishing checklist below.
8. **Distribute** — produce a LinkedIn post draft (LinkedIn is Aaron's distribution channel).
   It ships in the session output, not on the site.

The `/new-insight` skill (`.claude/skills/new-insight/SKILL.md`) runs steps 2–8 end to end.

## Publishing checklist (the Wire step)

- [ ] `insights/<slug>/index.html` exists, no `{{` tokens remain (`grep -rn "{{" insights/<slug>/`)
- [ ] All three JSON-LD blocks parse (extract and validate with `python3 -m json.tool`)
- [ ] Add the article card to `insights/index.html` — newest first, matching card markup
      (meta line, 2 topic tags, title, excerpt, "Read more →")
- [ ] Add a `<url>` entry to `sitemap.xml` and bump `<lastmod>` on `/insights/`
- [ ] Every external link verified reachable during the session; internal links resolve to real paths
- [ ] Share URLs (LinkedIn / X / Email) point at the new slug with the title URL-encoded
- [ ] Move the backlog item to `published` in `BACKLOG.md` with the publish date
- [ ] Commit with a descriptive message on a feature branch; open a draft PR — Aaron approves
      before anything merges. The loop never publishes to `main` on its own.

## Files

| File | Purpose |
|---|---|
| `VOICE.md` | How Aaron writes — sentence mechanics, structural moves, banned patterns, edit checklist |
| `THEMES.md` | Theme pillars, canonical facts bank, approved link library, hard rules |
| `BACKLOG.md` | Idea queue with states: `idea → ready → drafting → published` |
| `TEMPLATE.html` | The article page shell with `{{TOKEN}}` placeholders |

## Cadence

The loop is designed to be invoked, not scheduled. Target cadence is one article every 2–4 weeks —
frequent enough to compound SEO, infrequent enough that every piece earns its slot. If a scheduled
version is ever wanted, wire the `/new-insight` skill to a Routine that opens a draft PR; keep the
human approval gate.
