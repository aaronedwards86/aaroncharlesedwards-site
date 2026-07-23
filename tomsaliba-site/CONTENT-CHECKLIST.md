# Content checklist for tomsaliba.com

The copy is now drawn from Tom's CV (Thomas Alexander Saliba, Merchandising Director — 2026). What remains is mostly assets and confirmations. Each open item has a matching `TODO` comment in `index.html`.

## Still needed before launch

- [ ] **Editorial portrait** — 3:4 crop, at least 1000px wide, saved as `tom-headshot.jpg`. Swap the hero `<img src="tom-headshot-placeholder.svg">` to point at it. The Open Graph/Twitter image tags already expect this filename. This is the single highest-impact item on the page.
- [ ] **LinkedIn URL** — three places: contact section, footer, and a `sameAs` array worth adding to the JSON-LD Person schema in `<head>`.
- [ ] **Confirm the contact email** — currently `saliba_t@hotmail.com` (from the CV), used in the contact link and the form's error message. A `tom@tomsaliba.com` address would look sharper once the domain exists.
- [ ] **Tom's sign-off on the copy** — especially two things. First, the Track Record numbers (revenue turnaround, Bonmarché growth, DSGN Studio forecast) since they're now public claims. Second, the consultant positioning itself: the site presents Tom as a merchandising consultant offering turnarounds, capability builds, and interim leadership, while his CV shows a current permanent role at Boohoo/Debenhams Group — Tom should confirm he's comfortable advertising consulting services publicly before launch.

## Optional polish

- [ ] **Real brand logos** for the scrolling strip (currently styled text wordmarks: boohoo, Debenhams, Bonmarché, Missguided, Topshop, Ivy Park, River Island, ASOS, DSGN Studio). Note: these are employers' marks — text wordmarks avoid any logo-permission questions.
- [ ] **Featured video** — if Tom has a recorded lecture or panel, enable the hidden video block in the Lecturing section (remove `display:none`).
- [ ] **Press section** — ships hidden; enable if Tom collects press features or podcast appearances (remove `display:none`, restore the Press nav link).
- [ ] **Google Search Console** verification tag + sitemap submission after launch.

## Deliberately left off the site

- Phone number (on the CV, but a public website shouldn't carry it — the form and email cover contact).
- Street-level address — only "Greater Manchester" appears.
- Education grades and systems/tools lists — CV material, not personal-brand material.
