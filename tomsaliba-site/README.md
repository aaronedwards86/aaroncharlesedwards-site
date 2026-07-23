# tomsaliba.com

Personal site for Tom Saliba, built on the same design system as aaroncharlesedwards.com: a single-page static HTML site (no build step, no framework) designed for Netlify hosting.

**This folder is a staging area.** It lives inside the `aaroncharlesedwards-site` repo only so it could be built and reviewed here. Before launch, move it to its own repository (step 1 below). Do not merge this folder into the main branch of the Aaron site — anything merged there gets deployed to aaroncharlesedwards.com.

## What's in the box

| File | Purpose |
|---|---|
| `index.html` | The entire site: markup, styles, and scripts in one file |
| `tom-headshot-placeholder.svg` | Temporary hero portrait — replace with a real photo |
| `favicon.*`, `apple-touch-icon.png` | "TS" monogram icons, all sizes |
| `netlify.toml` | Netlify config (static publish, deploy previews) |
| `robots.txt`, `sitemap.xml` | SEO basics, already pointed at tomsaliba.com |
| `CONTENT-CHECKLIST.md` | Every placeholder that needs Tom's real content |

## Launch steps

### 1. Move to its own repository

Create a new GitHub repo (e.g. `tomsaliba-site`), then copy the **contents of this folder** to its root and push:

```bash
git clone https://github.com/<your-account>/tomsaliba-site.git
cp -r tomsaliba-site/* tomsaliba-site/.gitignore tomsaliba-site 2>/dev/null  # copy this folder's files in
cd tomsaliba-site && git add -A && git commit -m "Initial site" && git push
```

(Or simply create the repo on GitHub, upload these files through the web UI, and commit.)

### 2. Connect Netlify

1. In Netlify: **Add new site → Import an existing project → GitHub** → pick the new repo.
2. Build command: leave **empty**. Publish directory: `.` (the `netlify.toml` already says this).
3. Deploy. You'll get a `something.netlify.app` URL immediately — use it to review with Tom.

### 3. Point the domain

1. Buy `tomsaliba.com` (Netlify can register it, or use any registrar).
2. In Netlify: **Domain management → Add custom domain** → `tomsaliba.com`.
3. If the domain is at an external registrar, either switch its nameservers to Netlify DNS (easiest) or add the A/CNAME records Netlify shows you.
4. HTTPS is provisioned automatically once DNS resolves.

### 4. Turn on the contact form

The form is already wired for **Netlify Forms** (`data-netlify="true"`). After the first deploy:

1. In Netlify: **Forms** → confirm the `contact` form was detected.
2. **Form notifications** → add Tom's email so submissions land in his inbox.

If the site is ever hosted somewhere other than Netlify, swap the form for a [Formspree](https://formspree.io) endpoint instead.

### 5. Replace the placeholder content

Work through `CONTENT-CHECKLIST.md` — every placeholder is also marked with a `TODO` comment in `index.html`. The big ones:

- **Portrait** — a real editorial photo saved as `tom-headshot.jpg` (3:4 crop, ≥1000px wide), then update the `<img src>` in the hero and keep the OG image path in the `<head>` as is.
- **Hero copy** — positioning line and proof paragraph.
- **Client strip** — real client names (or SVG logos in a `logos/` folder).
- **Ventures cards** — real companies with real links.
- **About** — four short paragraphs.
- **Contact** — real email + LinkedIn URLs (three places: contact links, form error message in the script, footer).

Two sections ship **hidden** until there's real content for them (search `display:none` in `index.html`): the featured video in Speaking, and the entire Press section.

### 6. Post-launch polish

- Add the site to [Google Search Console](https://search.google.com/search-console) and drop the verification meta tag into `<head>`.
- Submit `https://tomsaliba.com/sitemap.xml` there.
- Expand the JSON-LD Person schema in `<head>` with `jobTitle`, `worksFor`, and `sameAs` (LinkedIn) once the facts are final.
- Test on a phone — the layout is responsive, but check the hero photo crop.

## Editing notes

- Everything is in `index.html`. Styles are in the `<style>` block, organized by section with `── Section ──` comment banners.
- Colors and fonts are CSS variables at the top of the `<style>` block (`--bg`, `--text`, `--accent`, etc.) — change the whole palette in one place.
- The scrolling logo strip needs its list of logos duplicated once, back to back, for the seamless loop.
