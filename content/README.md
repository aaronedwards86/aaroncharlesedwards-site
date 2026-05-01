# Content Directory

These YAML data files are managed by [Decap CMS](https://decapcms.org/) via the `/admin` panel.

## How it works

1. **Decap CMS** (at `/admin/`) provides a UI for editing these YAML files
2. Edits are committed to the Git repo via Netlify's Git Gateway
3. **Currently:** These data files are not yet wired into `index.html`

## Next step: Rendering

Since this site is pure static HTML (no static site generator), one of these approaches is needed to pull content from these YAML files into `index.html`:

- **Option A: Client-side JS**. A small script that fetches the YAML files at runtime and injects content into the DOM
- **Option B: Build step**. A lightweight Node.js script (run via `netlify.toml` build command) that reads the YAML and generates/updates `index.html` from a template
- **Option C: Migrate to an SSG**. Use 11ty, Hugo, or similar to template `index.html` with these data files as input

For now, the CMS structure is in place. The YAML files mirror the current content in `index.html` so that when rendering is wired up, nothing changes visually.

## Files

- `hero.yml`: Hero section (credential, headline, tagline)
- `about.yml`: About/bio section
- `speaking.yml`: Speaking topics and intro text
- `ventures.yml`: Ventures/portfolio cards
