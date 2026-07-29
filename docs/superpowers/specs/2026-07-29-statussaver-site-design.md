# Status Saver site — Phase 1 design

**Date:** 2026-07-29
**Repo:** `banyanstudio/banyanstudio.github.io` (local clone dir: `banyanstudio-legal`)
**Surface:** `https://banyanstudio.github.io/statussaver/`

---

## 1. Context

The repo is Banyan Studio's GitHub Pages user site. It began life as a legal-docs-only
site (`banyanstudio-legal`), was renamed to `banyanstudio.github.io`, and now serves:

| URL | State before this work |
|---|---|
| `/` | Landing page titled "Banyan Studio — Legal". Lists Status Saver's two docs. |
| `/statussaver/privacy.html` | Live. Analytics disclosure published 2026-07-29. |
| `/statussaver/terms.html` | Live. |
| `/statussaver/privacy.md`, `terms.md` | Live, served as `text/markdown; charset=utf-8`. |
| `/statussaver/` | **404.** `index.html` existed only on the author's machine, untracked. |
| `/statussaver/icon.webp` | **404.** Untracked. |

A complete, well-built landing page (~530 lines) already existed locally but had never
been committed. Phase 1 ships it as part of a coherent three-page site.

### The core defect

The landing page and the legal pages are visually two different websites:

| | Landing (`index.html`) | Legal (`privacy`/`terms.html`) |
|---|---|---|
| Type | DM Serif Display italic + Plus Jakarta Sans | system font stack |
| Palette | forest `#1F4030` / cream `#F1ECDD` / gold `#C9A449` | GitHub blue `#0969da` on white |
| CSS | ~380 lines inline in `<style>` | external `../style.css` |
| Header nav | Studio, Privacy, `#get` — no Terms | Studio, Privacy, Terms — **no link to the app page** |

That last cell is the functional bug, not just a cosmetic one: a user arriving at
`privacy.html` from the Play listing has no route to the product page. The landing page
is also orphaned — zero internal inbound links, which hurts both search crawlers and
AI agents.

---

## 2. Goals

1. `/statussaver/` returns 200 and reads as one site across all three pages.
2. No false or unverifiable privacy claims anywhere in the copy.
3. Organic discovery: correct canonical/OG/JSON-LD, `sitemap.xml`, `robots.txt`.
4. Credibility: coherent brand, no dead ends, visible legal, working contact.
5. AI-agent-crawl-friendly, to the genuine ceiling of a static GitHub Pages host.

## 3. Non-goals (Phase 1)

- Content/SEO article pages, FAQ, guides hub, blog. Deferred by explicit decision.
- Restyling the root `/index.html` or `style.css`.
- Support-desk surface.
- Custom domain.

---

## 4. Locked decisions

| Decision | Choice | Rationale |
|---|---|---|
| Design unification | **Per-app design layer** (new `statussaver/site.css`) | Forest/cream/gold is *Status Saver's* palette, derived from the app theme. Scoping it to `/statussaver/` keeps studio identity neutral for app #2 and leaves the root legal index and future-app template untouched. |
| Page set | Landing + privacy + terms | Explicit user scope-down. |
| Content Signals | `search=yes, ai-input=yes, ai-train=yes` | Content is marketing copy and legal docs. Training exposure costs nothing; upside is the app being named in AI answers. |
| Web fonts | **Self-host** woff2 | Removes two third-party preconnects, closes the Google-Fonts-leaks-visitor-IPs GDPR grey area, improves LCP. Both families are OFL-licensed, so redistribution is permitted. |
| OG image | **Defer** | A 1200×630 card is a real design task; it shouldn't block shipping. Tracked as a known gap. |
| GoatCounter | **Remove** | Drops a third-party request and any web-analytics disclosure obligation for the site. Whether the `banyanstudio.goatcounter.com` account was ever registered was not established — if it wasn't, the script was collecting nothing anyway. No web traffic visibility as a result — accepted. |
| Privacy policy push | **Shipped separately, already live** | Unblocked the Play release without waiting on the site work. Commit `3517d82`. |

---

## 5. Architecture

### 5.1 New `statussaver/site.css` — the shared design layer

Extracted from the landing page's inline `<style>`, holds only what all three pages share:

- **Tokens:** the full light + dark `:root` custom-property set (forest/cream/gold, ink,
  sub, line, card).
- **Typography:** `@font-face` for the two self-hosted families; base `body` rules; the
  **document** `h1`/`h2`/`h3` scale — i.e. the legal-page heading treatment (sans, with
  the `h2` underline rule). The landing page's display `h1` (DM Serif Display italic,
  `clamp()`-sized) is a page-specific override and lives in its inline block, not here.
  Shared layer = document defaults; landing overrides.
- **Layout:** reset, `.wrap` (720px max-width).
- **Chrome:** `header.site`, `footer.site`, `.cta`, `:focus-visible`.
- **Document typography** the legal pages need, restyled onto the warm palette but keeping
  the existing well-built structure: `.meta`, `.table-wrap`, `table`/`th`/`td`,
  `blockquote`, list spacing.

Landing-page-only CSS — hero grid, phone mockup, `.mtile`/`.disc`/`.save-pill`, feature
cards, `@keyframes`, `prefers-reduced-motion` overrides — **stays inline** in
`index.html`. It is used by exactly one page; hoisting it would make every legal page
download dead CSS.

Root `style.css` is **not modified**. The root `/index.html` continues to use it.

### 5.2 Fonts

`statussaver/fonts/` containing:

- `plus-jakarta-sans-variable.woff2` — variable font, covers the 400–800 weights in use.
- `dm-serif-display-italic.woff2` — 400 italic only; that is the sole cut used (h1, closing line).
- `OFL.txt` — license text for both families, as OFL redistribution requires.

Latin subset. `@font-face` uses `font-display: swap`. The two
`fonts.googleapis.com`/`fonts.gstatic.com` preconnects and the stylesheet `<link>` are
deleted from `index.html`.

### 5.3 Navigation contract

All three pages share one header and one footer.

**Header:** `Banyan Studio` (→ `../`) · `Status Saver` (→ `./`) · `Privacy` · `Terms` ·
`Get the app`. The current page's link carries `aria-current="page"`.

**Footer:** `Banyan Studio` · `Status Saver` · `Privacy Policy` · `Terms & Conditions` ·
`Contact` (mailto), plus the WhatsApp/Meta non-affiliation disclaimer on **all three**
pages, not just the landing.

This is what closes the Play-listing → `privacy.html` → dead-end trap.

### 5.4 One change outside `/statussaver/`

`/index.html` gains a link to `/statussaver/` so the landing page is not orphaned and the
studio root routes visitors to the product. Link only — no restyle, no palette change.

---

## 6. Copy correction

`index.html` feature card 3 currently claims:

> No account, no analytics, no third-party servers.

This is false as of the 2026-07-18 app release: Status Saver ships Firebase Analytics and
Crashlytics. Replacement:

> **Private by design** — No account, no ads, and your photos and videos never leave your
> device. The app reads only media already on your phone through Android's scoped storage
> — no "all files access" permission. Anonymous usage and crash reporting can be switched
> off in Settings.

Verified against the app source before wording: `settings_section_privacy` = "Privacy" and
`settings_share_analytics` = "Share anonymous usage data"
(`app/src/main/res/values/strings.xml:151-154`), and the toggle gates both
`setAnalyticsCollectionEnabled` and `isCrashlyticsCollectionEnabled`
(`analytics/FirebaseAnalyticsTracker.kt:38-39`). The "switched off in Settings" claim is
therefore accurate, and consistent with §4 of the published privacy policy.

`meta description` and the "No ads · No sign-up" trust line are accurate and unchanged.

---

## 7. SEO layer

Per page:

- `<link rel="canonical">` — the landing has one; **add to both legal pages**.
- `og:title`, `og:description`, `og:type`, `og:site_name`, `og:url`, `og:image`
  (still `icon.webp` — known gap, see §10).
- `twitter:card` = `summary_large_image`.
- `<link rel="alternate" type="text/markdown">` pointing at the `.md` mirror (legal pages).

Structured data (JSON-LD):

- Landing: `SoftwareApplication` — name, `operatingSystem: Android`,
  `applicationCategory: UtilitiesApplication`, `offers` at price `0`, `downloadUrl` = the
  Play listing, `publisher` → `Organization`.
- Landing: `Organization` for Banyan Studio — name, url, contact email.
- Legal pages: `WebPage` with `dateModified` matching the doc's `Last updated`.

Site-wide, at the domain root:

- `sitemap.xml` — all published pages with `lastmod`. Covers root and `/statussaver/`.
- `robots.txt` — with the `Sitemap:` directive.

---

## 8. Agent-readiness layer

Assessed against the five isitagentready.com categories, with an honest verdict per
category for a static GitHub Pages host.

| Category | Verdict |
|---|---|
| **Discoverability** | Partial. `robots.txt` + `sitemap.xml` ✅. Link response headers ❌ — Pages serves a fixed header set with no config. DNS-AID ❌ — `banyanstudio.github.io` is a github.com subdomain; no DNS record control. |
| **Content Accessibility** | Strong. Pages already serves `.md` as `content-type: text/markdown; charset=utf-8` at stable URLs. Header-based `Accept:` negotiation ❌ (no server logic), but parallel markdown at predictable paths + `rel="alternate"` + `llms.txt` gives agents a real machine-readable representation with the correct MIME type. |
| **Bot Access Control** | Full. Explicit AI-bot rules + Content Signals policy in `robots.txt`. |
| **Protocol Discovery** | ❌ Not applicable. No API, no MCP server, no OAuth-protected resource. An MCP Server Card on a three-page brochure site is noise, not a score. |
| **Commerce** | ❌ Not applicable. Free app, nothing transactable. |

### 8.1 `robots.txt`

At the domain root. Contains:

- A `Content-Signal: search=yes, ai-input=yes, ai-train=yes` declaration.
- `Allow: /` for `*`.
- Named-agent groups explicitly allowed: `GPTBot`, `OAI-SearchBot`, `ChatGPT-User`,
  `ClaudeBot`, `Claude-User`, `Claude-SearchBot`, `PerplexityBot`, `Perplexity-User`,
  `Google-Extended`, `CCBot`, `Applebot-Extended`, `meta-externalagent`.
  Named explicitly rather than relying on the `*` wildcard, because several of these
  crawlers only honour directives addressed to them by name.
- `Sitemap:` pointing at the absolute sitemap URL.

### 8.2 `/llms.txt`

Domain root, studio-level, so it covers both the root and `/statussaver/`. Follows the
llms.txt convention: an `# H1` site name, a `>` blockquote summary, then `##` sections of
annotated links. Enumerates the landing page, both legal pages, **and the `.md` mirrors**,
each with a one-line description of what an agent will find there. Includes the Play
listing URL and the non-affiliation fact, so an agent summarising the app states the
relationship correctly.

### 8.3 `statussaver/index.md`

A markdown mirror of the landing page — same product facts, no decorative markup —
matching the existing `privacy.md`/`terms.md` pattern, linked via `rel="alternate"` and
listed in `llms.txt`.

### 8.4 `.nojekyll`

Added at the domain root. Pages currently builds with `build_type: legacy` (Jekyll).
Nothing in the repo uses Jekyll — no `_config.yml`, no front matter, no layouts — and the
`.md` files only serve raw because they happen to lack front matter. `.nojekyll` makes
that deterministic and removes a class of future surprise (e.g. a `.md` file gaining front
matter and silently clobbering its sibling `.html`).

---

## 9. Verification

Not "it should work" — each of these is a command with an expected result.

1. `/statussaver/`, `/statussaver/icon.webp` return **200** (both are 404 today).
2. All three pages, both legal `.md` mirrors, `robots.txt`, `sitemap.xml`, `llms.txt`,
   `index.md` return 200.
3. No page requests `fonts.googleapis.com`, `fonts.gstatic.com`, or `gc.zgo.at`
   (grep the served HTML).
4. Both self-hosted woff2 files return 200 with a `font/woff2` content-type.
5. `grep -c "no analytics"` on the served landing page = **0**.
6. Every header and footer link on all three pages resolves to 200 — no dead ends.
   Specifically: `privacy.html` → `./` reaches the landing page.
7. JSON-LD on each page parses as valid JSON and has the expected `@type`.
8. Rendered in the browser pane at mobile (375) and desktop (1280) widths, in both light
   and dark colour schemes — legal pages must visibly share the landing page's palette
   and typefaces.
9. `sitemap.xml` parses as XML; every `<loc>` in it returns 200.

---

## 10. Known gaps / follow-ups

- **OG image** is the square `icon.webp`; link previews will render poorly until a
  1200×630 card exists. Deliberately deferred.
- **No web analytics** after GoatCounter removal. Play Console install data only.
- Repo `README.md` and `CLAUDE.md` still document the pre-rename
  `/banyanstudio-legal/` URLs and describe the repo as legal-docs-only. Both need
  updating as part of this work.
- `banyanstudio-legal/` redirect stubs (commit `1e99dc3`) stay as-is; still needed for
  any old links in the wild.
- Phase 2 candidates, explicitly out of scope now: FAQ page, how-to guides hub, studio
  root homepage rebuild, custom domain behind Cloudflare (which is what would unlock the
  header-dependent and DNS-dependent agent-readiness categories).

---

## 11. Risks

| Risk | Mitigation |
|---|---|
| Restyling live legal pages could damage readability of dense legal text. | The document typography rules carry over structurally; only the palette and typefaces change. Verified at two widths and both colour schemes before push. |
| Self-hosted font subset missing a glyph used in the legal copy (e.g. `—`, `’`, `₹`). | Latin subset includes these; verification step 8 is a visual read of the legal pages, which is where the long-form copy lives. |
| `.nojekyll` changing how something is served. | Nothing in the repo depends on Jekyll. Verification step 2 re-checks every URL after the change. |
| `ai-train=yes` is hard to walk back once content is trained on. | Accepted deliberately; content is marketing copy and public legal docs only. |
