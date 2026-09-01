# Portfolio — Enhancement Plan

Tracking doc for improvements to the portfolio site (`index.html`), deployed at
<https://omnia-amer.github.io/portfolio/>.

Status legend: ⬜ not started · 🟡 in progress · ✅ done

---

## Summary of findings

| # | Area | Severity | Effort | Blocked on |
|---|------|----------|--------|------------|
| 1 | 47 visible `<mark class="todo">` editor notes on case-study pages | 🔴 High | S (hide) / L (fill) | Real content from Omnia |
| 2 | No Open Graph / Twitter / canonical / structured data | 🟠 Med | S | `og-image.png` |
| 3 | 14 MB page — all images, video, CV inlined as base64 | 🟠 Med | L | — |
| 4 | Missing `robots.txt`, `sitemap.xml`, `404.html` | 🟡 Low | S | — |
| 5 | Accessibility: contrast, skip link, focus management, focus-visible | 🟡 Low | M | — |
| 6 | Nice-to-haves: analytics, contact form, favicon-on-dark | 🟢 Opt | S–M | Decisions |

Effort: **S** ≈ <30 min · **M** ≈ 1–2 h · **L** ≈ half-day+

---

## Phase 1 — Ship now (no new content required)

One commit. Low risk, immediate polish.

### 1.1 Hide placeholder notes ⬜
- **What:** 47 `<mark class="todo">…</mark>` spans render on the live case-study pages
  ("Add a measurable result", "Add your role", "confirm", …).
- **Fix (stopgap):** add to the stylesheet —
  ```css
  .todo{ display:none !important; }
  ```
- **Acceptance:** no highlighted notes visible on any `#/work/case-*` route.
- **Follow-up:** replace with real content in Phase 4, then remove this rule.

### 1.2 Social / SEO meta ⬜
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
- **Note:** `og-image.png` (1200×630) is produced in task 2.1.

### 1.3 JSON-LD structured data ⬜
- **What:** add a `<script type="application/ld+json">` `Person` block before `</head>`:
  name, jobTitle, url, `sameAs` (Behance, Dribbble, LinkedIn), address (Alexandria, Egypt).
- **Acceptance:** validates at <https://validator.schema.org>.

### 1.4 Font loading ⬜
- **What:** fonts currently load via `@import` inside an in-`<body>` `<style>` (render-blocking, serialized).
- **Fix:** delete the `@import` line, add to `<head>`:
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&family=Work+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap">
  ```
- **Acceptance:** fonts still render; no FOIT longer than ~100 ms.

### 1.5 Contrast fix ⬜
- **What:** `--ink-faint: rgba(255,255,255,.40)` on `#000` ≈ 3.7:1 — fails WCAG AA for body text.
- **Fix:** `--ink-faint: rgba(255,255,255,.55);` (≈ 5.3:1). Spot-check eyebrow labels / footer.
- **Acceptance:** all text ≥ 4.5:1 (or ≥ 3:1 for ≥ 24 px / 19 px-bold).

### 1.6 Repo infra files ⬜
- `robots.txt`:
  ```
  User-agent: *
  Allow: /
  Sitemap: https://omnia-amer.github.io/portfolio/sitemap.xml
  ```
- `sitemap.xml`: single `<url>` for the site root (hash routes aren't separately crawlable).
- `404.html`: copy of `index.html` (so mistyped deep links still load the app).
- **Acceptance:** all three return HTTP 200; `/portfolio/anything` renders the site.

### 1.7 Favicon on dark tabs ⬜
- **What:** the all-black favicon square blends into dark browser tab strips.
- **Fix:** change `favicon.svg` background `#000000` → `#111111` with a `1px` `#ffffff22` inner stroke,
  or keep black but enlarge the white tiles. Update both the file and the inline data-URI copy.
- **Acceptance:** icon distinguishable on light and dark tab bars.

**Phase 1 acceptance:** Lighthouse SEO ≥ 95, Best-Practices ≥ 95; social card renders; no visible TODO notes.

---

## Phase 2 — Assets & performance (mechanical, larger diff)

### 2.1 Create `og-image.png` ⬜
- 1200×630, black background, "Omnia Amer / Senior UI/UX Designer" + the logo mark, matching site type.
- Save to repo root.

### 2.2 Externalise images ⬜
- **What:** 138 `<img src="data:image/jpeg;base64,…">` (~12 MB) inlined.
- **Fix:** decode each to `assets/img/NN.jpg`, rewrite `src` to the file path. Script-assisted.
- Keep alt text unchanged.
- **Acceptance:** `index.html` < 300 KB; every image still loads; visual diff clean.

### 2.3 Externalise the case-study video ⬜
- **What:** one `<video>` has both webm + mp4 inlined as base64.
- **Fix:** write `assets/video/jood-kiosk.webm` + `.mp4`; reference by path; add `preload="none"`
  and a `poster` image.

### 2.4 Externalise the CV PDF ⬜
- **What:** `CV_B64` (~1.9 MB base64) inlined in a `<script>`.
- **Fix:** save `assets/Omnia_Amer_CV.pdf`; change the Download CV handler to a plain
  `<a href="assets/Omnia_Amer_CV.pdf" download>` (drop the Blob/atob code entirely).
- **Acceptance:** button downloads a valid PDF; no JS needed for it.

### 2.5 Image dimensions + lazy-loading ⬜
- Add `width`/`height` (or `style="aspect-ratio:…"`) to every `<img>` to kill layout shift (CLS).
- Add `loading="lazy"` + `decoding="async"` to all below-the-fold images (currently 34 / 138).
- Mark the hero / LCP image `fetchpriority="high"`, `loading="eager"`.
- **Acceptance:** Lighthouse CLS < 0.1; Performance ≥ 90 on mobile.

**Phase 2 acceptance:** first load < 500 KB HTML, LCP < 2.5 s on simulated 4G, Lighthouse Perf ≥ 90.

---

## Phase 3 — Accessibility & UX

### 3.1 Skip link ⬜
- `<a href="#main" class="skip-link">Skip to content</a>` as first body child; visible on focus;
  `id="main"` on the active `<main>`.

### 3.2 SPA focus management ⬜
- **What:** route change does `scrollTo(0,0)` only — keyboard/SR users lose their place.
- **Fix:** after `applyRoute()`, set focus to the new page's `<h1>` (`tabindex="-1"`), and add a
  visually-hidden `aria-live="polite"` region announcing the new page name.

### 3.3 focus-visible coverage ⬜
- Extend the single `:focus-visible` rule to links, buttons, the Download CV control, phone/email
  CTAs, and FAQ accordions. Ensure a visible ring (not just `transform: scale`).

### 3.4 Reduced-motion audit ⬜
- Confirmed a global `prefers-reduced-motion` rule exists — verify the reveal-on-scroll and video
  autoplay/hover states also respect it.

**Phase 3 acceptance:** keyboard-only walkthrough of every route with no traps; axe DevTools 0 criticals.

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
