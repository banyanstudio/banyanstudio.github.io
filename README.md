# banyanstudio.github.io

Public website for **Banyan Studio**: product pages and legal documents for the apps we
publish.

Hosted via GitHub Pages at **https://banyanstudio.github.io/**

> The repo was originally named `banyanstudio-legal` and served only legal documents. It
> was renamed to `banyanstudio.github.io` so it serves from the domain root. Redirect stubs
> for the old `/banyanstudio-legal/…` paths are kept in `banyanstudio-legal/` for any links
> still in the wild. Some local clones are still in a directory named `banyanstudio-legal`;
> that's just the folder name, not the remote.

## Structure

```
.
├── index.html                     ← studio landing page, lists apps + their docs
├── style.css                      ← stylesheet for the studio landing page
├── robots.txt                     ← crawl rules, AI-bot rules, content signals, sitemap ref
├── sitemap.xml                     ← canonical HTML pages
├── llms.txt                       ← structured summary for AI agents
├── .nojekyll                      ← serve files verbatim, no Jekyll processing
├── banyanstudio-legal/            ← redirect stubs for the pre-rename URLs
├── nodi/                      ← same layout as statussaver/ (own site.css, icon.svg, no fonts)
└── statussaver/
    ├── index.html                 ← Status Saver product page
    ├── index.md                   ← markdown mirror
    ├── site.css                   ← shared design layer for every /statussaver/ page
    ├── icon.webp                  ← app icon (favicon, hero mark, OG image)
    ├── fonts/                     ← self-hosted woff2 + OFL.txt
    ├── privacy.html / privacy.md
    └── terms.html   / terms.md
```

Each app gets its own subdirectory. Data practices, permissions, and governing-law clauses
differ per app, so legal copy is never shared or DRY-extracted across apps.

## Published URLs

| Page | URL |
|---|---|
| Studio home | https://banyanstudio.github.io/ |
| Status Saver | https://banyanstudio.github.io/statussaver/ |
| Status Saver — Privacy Policy | https://banyanstudio.github.io/statussaver/privacy.html |
| Status Saver — Terms & Conditions | https://banyanstudio.github.io/statussaver/terms.html |
| Nodi | https://banyanstudio.github.io/nodi/ |
| Nodi — Privacy Policy | https://banyanstudio.github.io/nodi/privacy.html |
| Nodi — Terms & Conditions | https://banyanstudio.github.io/nodi/terms.html |

The Play Store listing and the app's in-app links point at the privacy and terms URLs
above. **Do not move or rename those two files.**

## Styling

Two stylesheets, deliberately separate:

- `style.css` — the studio landing page only. Neutral, so it doesn't tie studio identity to
  any one app's palette.
- `statussaver/site.css` — the shared design layer for every page under `/statussaver/`:
  theme tokens (light + dark), the two self-hosted typefaces, the shared header/footer, and
  the document typography the legal pages use.

Page-specific CSS stays inline in the page that needs it. The Status Saver landing page's
hero, phone mockup and feature cards live in a `<style>` block in its own `index.html`,
because no other page uses them.

Fonts are self-hosted from `statussaver/fonts/` (latin subsets, woff2). Nothing on the site
requests a third-party asset — no font CDN, no analytics, no tracking.

## Editing

- The `.html` files are what Pages serves — edit these.
- The `.md` files are mirrors, served as `text/markdown` and advertised via
  `<link rel="alternate">` and `llms.txt`. **When you change one, mirror the change** so the
  two stay in sync.
- Bump the `Last updated:` date inside a legal doc whenever its substantive content
  changes, and update the matching `dateModified` in that page's JSON-LD block and the
  `lastmod` in `sitemap.xml`.
- Pages under `statussaver/` link the stylesheet as `site.css` and the studio root as `../`.

## Adding a new app

1. `mkdir <appname>` at the repo root.
2. Copy `statussaver/privacy.html` and `statussaver/terms.html` in as templates, along with
   `site.css` if the new app wants the same visual language (or write its own).
3. Edit for the new app: name, description, permissions table, governing law, contact,
   `Last updated`, canonical URL, OG tags, JSON-LD.
4. Add a section in the root `index.html` linking the new app's pages.
5. Add the new pages to `sitemap.xml` and `llms.txt`.
6. Commit and push to `main` — Pages redeploys automatically.

## Previewing locally

There is no build step. Serve the repo root with any static file server:

```bash
python3 -m http.server 4321
```

Then open http://localhost:4321. Note that `python3 -m http.server` may serve `.md` files
as `text/plain`; GitHub Pages serves them as `text/markdown`.

## Contact

`banyanstudio.dev@gmail.com`
