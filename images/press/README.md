# Press images — drop-in folder

The press cards on the homepage are wired to show real images from this folder.
Cards render exactly as before while a file is missing (the image slot removes itself),
and light up automatically as soon as the file lands here — no HTML changes needed.

## Expected files

| File | Card | Suggested source |
|---|---|---|
| `forbes.jpg` | Forbes — 30 Under 30 (hero grid) | Screenshot of the Forbes profile page |
| `lbb-reinvention.jpg` | LBB Online — Sparking Growth with Reinvention (hero grid) | Screenshot or the article's lead image |
| `founderbrew.jpg` | Founder Brew — The Sibling System (hero grid) | Screenshot or the story's lead photo |
| `cocainenomics.jpg` | D&AD / Webby — Cocainenomics (hero grid) | Campaign still (TCG owns these) |
| `jaguar-fpace.jpg` | Jaguar F-PACE (TV & Video) | Campaign still / frame grab (TCG campaign) |

## Specs

- JPG, 1200×675 (16:9). Any 16:9 crop works; images are `object-fit: cover`.
- Keep files under ~200 KB each (export at quality 70–80) — the site is meant to stay fast.
- Filenames must match exactly (lowercase, as listed).

Note: these couldn't be fetched automatically — the publications' sites aren't reachable
from the build sandbox, and screenshots of their pages are best taken (and rights-checked)
by a human anyway.
