# Portfolio — Enhancement Plan

Tracking doc for improvements to the portfolio site (`index.html`), deployed at
<https://omnia-amer.github.io/portfolio/>.

Status legend: ⬜ not started · 🟡 in progress · ✅ done

**Progress:** Phase 1 ✅ (2026-09-01) · Phase 2 ✅ (2026-09-02) · Phase 3 ✅ (2026-09-02) · Phase 4 ⬜ blocked on Omnia · Phase 5 ⬜ blocked on decisions

---

## Summary of findings

| # | Area | Severity | Effort | Blocked on |
|---|------|----------|--------|------------|
| 1 | 47 visible `<mark class="todo">` editor notes on case-study pages | 🟢 Hidden (was 🔴) | S (hide) ✅ / L (fill) ⬜ | Real content from Omnia |
| 2 | No Open Graph / Twitter / canonical / structured data | ✅ Fixed | S | — |
| 3 | 14 MB page — all images, video, CV inlined as base64 | ✅ Fixed (→ 192 KB) | L | — |
| 4 | Missing `robots.txt`, `sitemap.xml`, `404.html` | ✅ Fixed | S | — |
| 5 | Accessibility: contrast, skip link, focus management, focus-visible | ✅ Fixed | M | — |
| 6 | Nice-to-haves: analytics, contact form, favicon-on-dark | 🟢 Opt (favicon ✅) | S–M | Decisions |

Effort: **S** ≈ <30 min · **M** ≈ 1–2 h · **L** ≈ half-day+

---

## Phase 1 — Ship now (no new content required) ✅ DONE — 2026-09-01

One commit. Low risk, immediate polish.

### 1.1 Hide placeholder notes ✅
- **What:** 47 `<mark class="todo">…</mark>` spans render on the live case-study pages
  ("Add a measurable result", "Add your role", "confirm", …).
- **Fix (stopgap):** add to the stylesheet —
  ```css
  .todo{ display:none !important; }
  ```
- **Acceptance:** no highlighted notes visible on any `#/work/case-*` route.
- **Follow-up:** replace with real content in Phase 4, then remove this rule.
- **Verified:** Playwright DOM check — 47/47 `.todo` elements computed `display:none` on every route. ✅

### 1.2 Social / SEO meta ✅
- **What:** add to `<head>` —
  ```html
  <meta name="author" content="Omnia Amer">
  <link rel="canonical" href="https://omnia-amer.github.io/portfolio/">
  <meta name="theme-color" content="#000000">

  <meta property="og:type" content="website">
  <meta property="og:url" content="https://omnia-amer.github.io/portfolio/">
  <meta property="og:title" content="Omnia Amer — Senior UI/UX Designer">
  <meta property="og:description" content="Interface design for government and enterprise products — 15 shipped, 7 national institutions.">
  <meta property="og:image" content="https://omnia-amer.github.io/portfolio/og-image.png">
  <meta property="og:image:width" content="1200">
  <meta property="og:image:height" content="630">
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="Omnia Amer — Senior UI/UX Designer">
  <meta name="twitter:description" content="Interface design for government and enterprise products.">
  <meta name="twitter:image" content="https://omnia-amer.github.io/portfolio/og-image.png">
  ```
- **Acceptance:** passes <https://opengraph.dev> / LinkedIn Post Inspector with a card + image.
- **Note:** `og-image.png` (1200×630) — pulled forward from task 2.1 so this gate isn't left half-done;
  built as a plain PNG (brand mark, name, title, stat line) matching the site's dark/mono aesthetic.
- **Verified:** all 9 meta/OG/Twitter tags + canonical + theme-color render once in the DOM (checked via
  Playwright); `og-image.png` returns HTTP 200 locally. **Not yet verified live** — the LinkedIn/opengraph.dev
  card check needs the real `https://omnia-amer.github.io/portfolio/` URL after you push, since those tools
  can't reach a local file. Worth a 30-second check after deploy.

### 1.3 JSON-LD structured data ✅
- **What:** add a `<script type="application/ld+json">` `Person` block before `</head>`:
  name, jobTitle, url, `sameAs` (Behance, Dribbble, LinkedIn), address (Alexandria, Egypt).
- **Acceptance:** validates at <https://validator.schema.org>.
- **Verified:** `JSON.parse()` on the extracted block succeeds; schema fields present (name, jobTitle,
  url, sameAs × 3, PostalAddress). Recommend also pasting it into validator.schema.org once live, for
  the official Google-rich-results read.

### 1.4 Font loading ✅
- **What:** fonts currently load via `@import` inside an in-`<body>` `<style>` (render-blocking, serialized).
- **Fix:** delete the `@import` line, add to `<head>`:
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&family=Work+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap">
  ```
- **Acceptance:** fonts still render; no FOIT longer than ~100 ms.
- **Verified:** `@import` line removed from `<style>`; three `<link>` tags present in `<head>` instead
  (same domain as before, so no new third-party dependency — just moved earlier + non-render-blocking).
  Could not confirm actual font-swap timing in this sandbox (outbound fonts.googleapis.com is blocked
  here — `net::ERR_TUNNEL_CONNECTION_FAILED`); this is a sandbox limitation, not a site defect. Please
  do a quick visual check after deploy that the display/body faces still render correctly.

### 1.5 Contrast fix ✅
- **What:** `--ink-faint: rgba(255,255,255,.40)` on `#000` ≈ 3.7:1 — fails WCAG AA for body text.
- **Fix:** `--ink-faint: rgba(255,255,255,.55);` (≈ 5.3:1). Spot-check eyebrow labels / footer.
- **Acceptance:** all text ≥ 4.5:1 (or ≥ 3:1 for ≥ 24 px / 19 px-bold).
- **Verified:** computed WCAG ratio for white-at-.55-alpha over `#000` = **6.25:1** (was 3.7:1) —
  clears the 4.5:1 AA threshold with margin. Applied via the single `--ink-faint` CSS variable, so
  every eyebrow label / footer line / caption using it is fixed at once.

### 1.6 Repo infra files ✅
- `robots.txt`:
  ```
  User-agent: *
  Allow: /
  Sitemap: https://omnia-amer.github.io/portfolio/sitemap.xml
  ```
- `sitemap.xml`: single `<url>` for the site root (hash routes aren't separately crawlable).
- `404.html`: copy of `index.html` (so mistyped deep links still load the app).
- **Acceptance:** all three return HTTP 200; `/portfolio/anything` renders the site.
- **Verified:** all three files created and confirmed HTTP 200 over a local server. `sitemap.xml`
  parses as valid XML. **Note:** `404.html` is a snapshot copy of `index.html` at Phase 1 — refresh
  this copy after Phase 2 changes `index.html`'s structure, or it'll silently drift out of date.

### 1.7 Favicon on dark tabs ✅
- **What:** the all-black favicon square blends into dark browser tab strips.
- **Fix:** change `favicon.svg` background `#000000` → `#111111` with a `1px` `#ffffff22` inner stroke,
  or keep black but enlarge the white tiles. Update both the file and the inline data-URI copy.
- **Acceptance:** icon distinguishable on light and dark tab bars.

**Phase 1 acceptance:** Lighthouse SEO ≥ 95, Best-Practices ≥ 95; social card renders; no visible TODO notes.

### Gate result: ✅ PASS

Lighthouse itself couldn't run in this environment (no network access to install it, no scoring
service reachable), so the gate was validated with direct equivalents instead:

- Playwright, full route sweep (`/`, `/work`, `/about`, `/contact`, `/process`, 3 case-study routes,
  scrolled end-to-end on each): **0 JS console errors, 0 broken/unloaded images**, all `.todo` notes
  confirmed hidden (47/47).
- Meta/OG/Twitter/canonical/theme-color tags: present once each, correct values, `og-image.png` built
  and returns 200.
- JSON-LD: parses as valid JSON with the expected `Person` fields.
- Contrast: `--ink-faint` measured at 6.25:1 (target ≥ 4.5:1).
- `robots.txt` / `sitemap.xml` / `404.html`: all 200, sitemap XML-valid.
- The only network failure seen (`fonts.googleapis.com` → `ERR_TUNNEL_CONNECTION_FAILED`) is this
  sandbox blocking outbound font requests, not a site defect — same domain the old `@import` already
  depended on, just loaded earlier and non-render-blocking now.

**Two checks need the live URL, not a local copy, and are worth 5 minutes after you push:**
1. LinkedIn Post Inspector / opengraph.dev — confirm the social card renders with the new image.
2. A quick look on both a light-tab and dark-tab browser — confirm the new favicon reads clearly on both.

### Suggested edits before Phase 2

- **`og-image.png` was built with a fallback system font** (Liberation Sans — metrically close to
  Outfit/Arial, since Google Fonts wasn't reachable to source the real Outfit weights in this
  environment). It matches the site's dark/mono look but isn't pixel-identical to the on-site
  typography. Happy to regenerate it with the real Outfit font if you'd like — just say so.
- **Phase 2's `assets/img/` externalization will touch every image tag** `og-image.png` and
  `favicon.svg` currently reference — worth re-running this same Playwright sweep after that phase
  specifically, not just trusting the file-size drop.
- **`404.html` will need refreshing** after Phase 2 (see note under 1.6) — flagging so it doesn't
  quietly go stale.

---

## Phase 2 — Assets & performance ✅ DONE — 2026-09-02

Commits `c68dc9f` (externalize) + `c78174c` (dimensions/lazy). **index.html: 14,145,946 → 192,124 bytes.**

### 2.1 Create `og-image.png` ✅ (done in the Phase 1 gate — see 1.2)

### 2.2 Externalise images ✅
- 141 base64 images decoded to `assets/img/NNN.jpg` (+ one `.png`); `src` rewritten to paths. Alt text unchanged.
- **Verified live:** every image loads on home / work grid / about / skills / case-qnl / case-saso; no broken refs, no orphans.

### 2.3 Externalise the case-study video ✅
- webm + mp4 written to `assets/media/clip-01.webm` (520 KB) + `clip-02.mp4` (596 KB); referenced by path. `<video>` already `preload="metadata"`, no autoplay.

### 2.4 Externalise the CV PDF ✅
- `CV_B64` decoded to `assets/Omnia_Amer_CV.pdf` (1.46 MB, valid `%PDF-1.7`). Both Download CV links are now `<a href="assets/Omnia_Amer_CV.pdf" download>`; the Blob/atob `<script>` was deleted.

### 2.5 Image dimensions + lazy-loading ✅
- Intrinsic `width`/`height` on all 141 `<img>` (dimensions read from the files); base `img` rule gains `height:auto` so the attrs only drive aspect ratio.
- `loading="lazy"` added to the 107 that lacked it — all 141 now `loading="lazy"` + `decoding="async"`.
- **Verified:** layout pixel-identical to pre-change on every route tested; no distortion in the `aspect-ratio`/`object-fit` grids.

**Phase 2 gate: ✅ PASS** — HTML 192 KB (was 14 MB), so social scrapers now fetch it (LinkedIn's ~3 MB limit was the blocker). Run real Lighthouse once for the Perf/LCP/CLS numbers.
**Follow-up:** `404.html` is now a tiny hash-preserving redirect, not a copy of index.html — no longer drifts.

---

## Phase 3 — Accessibility & UX ✅ DONE — 2026-09-02

Commit `c3370c5`.

### 3.1 Skip link ✅
- `<a class="skip-link" href="#main-content">Skip to content</a>` is the first body element, hidden until focused. `applyRoute()` stamps `id="main-content"` on whichever `<main>` is currently shown.
- **Verified live:** link present, resolves to `#main-content`.

### 3.2 SPA focus management ✅
- `applyRoute(isNav)` now: tags the shown page `#main-content` + `tabindex="-1"`, and **on navigation only** (not initial load) moves focus to its `<h1>`/`<h2>`. A visually-hidden `#route-status` `aria-live="polite"` region announces the heading text.
- `focus({preventScroll:true})` so the existing `scrollTo(0,0)` still wins.
- **Verified live:** route changes render + keep working; no regression in the router.

### 3.3 focus-visible coverage ✅
- Added `a / button / [tabindex="0"] / summary :focus-visible { outline: 2px solid var(--ink); outline-offset: 3px }`; suppressed the ring on the programmatically-focused `main`/headings.
- **Verified live:** visible focus ring on buttons (seen on "View Case Studies").

### 3.4 Reduced-motion audit ✅
- Global `@media (prefers-reduced-motion:reduce)` already kills all transitions/animations and forces `.reveal` visible. The one `<video>` is `controls`, no autoplay — nothing else to gate.

**Phase 3 gate: ✅ PASS** — skip link + focus rings verified live; router intact across home/work/about/skills/case-study routes; only console noise is from browser extensions, not the site. A full screen-reader pass is still worth doing manually.

---

## Phase 4 — Content (Omnia)

Replace each `<mark class="todo">` with real detail, then delete the `.todo{display:none}` rule.
Per case study, fill:

- [ ] **Role** — your exact title on the project
- [ ] **Agency / employer** it was delivered through (if any)
- [ ] **Year(s)**
- [ ] **The brief / constraints** you were given
- [ ] **Your process** — research method, stakeholder sign-off, IA work, testing
- [ ] **A measurable result** — adoption, completion rate, tickets reduced, funds raised, sign-off

Case studies needing this: QNL, GAMA, GRSIA (Daman), QU, SASO, MCIT, MECC, Jood Eskan (web + kiosk),
Optimum Vision, TRAGS, Me7rab, QPMC, CCQ, Surah.

Also resolve the 3 `confirm` markers (fact-checks on specific claims).

---

## Phase 5 — Optional

| Item | Notes | Decision |
|------|-------|----------|
| Custom domain (e.g. `omniaamer.com`) | `CNAME` file + DNS; nicer on a CV | ⬜ |
| Privacy-friendly analytics | Plausible or GoatCounter — no cookie banner | ⬜ |
| Working contact form | Formspree/Web3Forms instead of `mailto:` only | ⬜ |
| Light theme | Large effort; site is dark-only by design | ⬜ probably skip |

---

## Execution order (recommended)

1. **Phase 1** — one commit, ship today.
2. **Phase 2** — one branch, review the visual diff carefully, merge.
3. **Phase 3** — one commit.
4. **Phase 4** — ongoing, as Omnia supplies content; ship per-case-study.
5. **Phase 5** — pick individually.

## Verification checklist (run after each phase)

- [ ] `https://omnia-amer.github.io/portfolio/` loads, all routes render
- [ ] Lighthouse (mobile): Perf / SEO / Best-Practices / a11y scores recorded below
- [ ] Social card renders (LinkedIn Post Inspector)
- [ ] Download CV returns a valid PDF
- [ ] No console errors
- [ ] Keyboard-only pass of nav + one case study

| Date | Phase | Perf | A11y | SEO | BP | Notes |
|------|-------|------|------|-----|----|-------|
| _tbd_ | baseline | | | | | before any changes |
| 2026-09-01 | Phase 1 | — | — | — | — | Lighthouse unavailable in the build environment (no network to install/score). Substituted: 0 console errors, 0 broken images across all routes, contrast 6.25:1, all meta/JSON-LD present and valid, 47/47 todo notes hidden. Run real Lighthouse once live and fill this row in. |
| 2026-09-02 | Phase 2 | — | — | — | — | index.html 14 MB → 192 KB; 141 imgs + video + CV externalised, all load live; width/height + lazy on all imgs; LinkedIn scraper unblocked. Lighthouse Perf/LCP/CLS still to be run live. |
| 2026-09-02 | Phase 3 | — | — | — | — | Skip link + SPA focus mgmt + focus rings, verified live; router intact. Manual screen-reader pass still recommended. |
