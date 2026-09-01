# Portfolio — Enhancement Plan & Status

Tracking doc for <https://omnia-amer.github.io/portfolio/> (repo: `Omnia-Amer/portfolio`).

Legend: ⬜ not started · 🟡 in progress · ✅ done · ⛔ blocked on you

**Progress:** Phase 1 ✅ · Phase 2 ✅ · Phase 3 ✅ · Phase 4 ⛔ (needs your content) · Phase 5 ⛔ (needs your decisions)

Last updated: 2026-09-02

---

## 1. Status at a glance

| Area | Status | Notes |
|------|--------|-------|
| Site is live & public | ✅ | GitHub Pages, HTTPS enforced |
| Placeholder "todo" notes visible to visitors | ✅ hidden | 47 notes hidden via CSS until real content lands (Phase 4) |
| Social share card (LinkedIn/WhatsApp/Slack) | ✅ | OG + Twitter tags, `og-image.png`, descriptions ≥ 100 chars |
| SEO basics | ✅ | canonical, JSON-LD Person, `robots.txt`, `sitemap.xml` |
| Page weight | ✅ | 14 MB → **192 KB** (assets moved to `assets/`) |
| Image performance | ✅ | intrinsic `width`/`height` + `loading="lazy"` on all 141 images |
| Download CV | ✅ | native `<a download>` → `assets/Omnia_Amer_CV.pdf` |
| Accessibility | ✅ | contrast fixed, skip link, SPA focus management, focus rings |
| Favicon | ✅ | monogram, readable on light + dark tab strips |
| 404 / deep links | ✅ | `404.html` redirects to the app, preserving the hash |
| Mobile | ✅ | verified at 375 px — nav collapses to a working hamburger |
| Real Lighthouse scores | 🟡 | A11y **100** · SEO **100** · Best Practices **96** · Perf **58** (extension-contaminated — see §6a) · **CLS 0** |
| Case-study detail (role/year/metrics) | ⛔ | 47 blanks — **needs your facts** (Phase 4) |
| Analytics | ⛔ | not installed — needs your decision + account |
| Contact form | ⛔ | `mailto:` only — needs your decision + service |
| Custom domain | ⛔ | on `github.io` — needs your decision |

---

## 2. What's done (Phases 1–3)

All committed to `main` and live. Commits: `673510b` (P1), `c68dc9f` + `c78174c` (P2), `c3370c5` (P3), `53aa347` (descriptions), `1eb50a1` (README).

### Phase 1 — SEO, social, polish
- **1.1** Hid the 47 `<mark class="todo">` editor notes — `.todo{display:none !important}` stopgap.
- **1.2** Added `author`, `canonical`, `theme-color`, full Open Graph + Twitter Card set, and built `og-image.png` (1200×630, on-brand).
- **1.3** Added JSON-LD `Person` structured data (name, jobTitle, url, `sameAs`, address).
- **1.4** Moved Google Fonts from an in-`<body>` `@import` to `<head>` `preconnect` + `stylesheet` (non-render-blocking).
- **1.5** Contrast: `--ink-faint` `.40 → .55` alpha — WCAG ratio 3.7:1 → **6.25:1** (passes AA).
- **1.6** Added `robots.txt`, `sitemap.xml`, `404.html`.
- **1.7** Favicon: `#111` background + hairline stroke so it reads on dark browser tabs.

### Phase 2 — Assets & performance (`index.html`: 14 MB → 192 KB)
- **2.2** 141 base64 images → `assets/img/NNN.jpg` (+ one `.png`); alt text unchanged.
- **2.3** Case-study video → `assets/media/clip-01.webm` + `clip-02.mp4`.
- **2.4** CV → `assets/Omnia_Amer_CV.pdf`; Download CV is now a native `<a download>` (Blob/atob JS deleted).
- **2.5** Intrinsic `width`/`height` on all 141 `<img>` (kills layout shift); `loading="lazy"` on all (was 34/141); base `img` rule gains `height:auto`.
- **Follow-up done:** `404.html` rewritten as a tiny hash-preserving redirect (no longer a 14 MB copy that drifts).

### Phase 3 — Accessibility & UX
- **3.1** "Skip to content" link (visible on focus); `applyRoute()` stamps `id="main-content"` on the active `<main>`.
- **3.2** On navigation, focus moves to the new page's heading; a visually-hidden `#route-status` `aria-live` region announces it. `focus({preventScroll:true})` keeps the existing scroll-to-top.
- **3.3** Real `:focus-visible` outlines on links / buttons / `summary`.
- **3.4** Reduced-motion: global rule already covers it; the one `<video>` has no autoplay.

### Post-Phase fixes
- Meta / OG / Twitter descriptions lengthened to ~194 chars (LinkedIn "≥ 100 characters" warning).
- README rewritten for the new `assets/` structure.

### Verified live (2026-09-02 QA sweep)
Desktop + mobile (375 px): all routes render, every image loads from `assets/`, mobile hamburger opens,
skip link resolves to a real `<main>`, `#route-status` present, focus rings visible, **0 site console errors**
(only browser-extension noise). Router intact after the `applyRoute` changes.

---

## 3. Open questions — need your answer to proceed

| # | Question | Why it matters | Default if no answer |
|---|----------|----------------|----------------------|
| Q1 | **Which case studies already have real detail vs need it?** Confirmed: **QNL is done** (Role: UX Consultant · Via: Mannai Corporation · Year: 2024–Present, full write-up). The other 14 still have `todo` markers. | Tells us how big Phase 4 actually is | Assume the other 14 need everything |
| Q2 | For each case study that needs it: **role, agency/employer, year(s), the brief, your process, one measurable result.** (See §4 for the checklist.) | This is the whole of Phase 4 — can't be inferred or invented | — blocked — |
| Q3 | The 3 `confirm` markers in the copy are **unverified claims** (e.g. a Guinness World Record link, specific figures). Are they accurate as written? | Publishing unverified specifics is a credibility risk | Leave hidden |
| Q4 | Are these the correct, current profile URLs? `behance.net/omnia-amer`, `dribbble.com/Omniaamer`, `linkedin.com/in/omni-aamer/` | They're in the JSON-LD + footer; a wrong LinkedIn slug is bad | Keep as-is |
| Q5 | Is the **phone number** (`+20 155 809 2205`) and **email** on the Contact page correct and OK to expose publicly? | It's live and crawlable now | Keep as-is |
| Q6 | Is `assets/Omnia_Amer_CV.pdf` your **current** CV? (It came out of the original file — may be old or a placeholder.) | The Download CV button serves it | Keep as-is |
| Q7 | Keep the URL as `…github.io/portfolio/`, or move to a **root** `omnia-amer.github.io` (no `/portfolio`)? | Cleaner on a CV; one-time repo rename | Keep `/portfolio/` |
| Q8 | **Custom domain** (e.g. `omniaamer.com`) — do you own one / want one? | Nicer than `github.io`; needs a `CNAME` + DNS | No |
| Q9 | **Analytics** — do you want to see who visits and what they look at? Which tool? | Needs an account you create; I add the snippet | No analytics |
| Q10 | **Contact form** — replace `mailto:` with a real form (Formspree / Web3Forms)? | `mailto:` fails for anyone without a desktop mail client | Keep `mailto:` |
| Q11 | Regenerate `og-image.png` with the **real Outfit font**? (Current one uses a metric-compatible fallback — looks fine, not pixel-perfect.) | Cosmetic | Leave it |
| Q12 | **Light theme** — confirmed skip? | Big effort; site is dark-by-design | Skip |

---

## 4. Phase 4 — Content you supply ⛔

Replace each `<mark class="todo">` with real detail, then delete the `.todo{display:none}` CSS rule.
Fastest path: **send me everything for ONE case study**, I wire it in as the template, you review the
format, then we roll through the rest.

Per case study, fill:

- [ ] **Role** — your exact title on the project
- [ ] **Agency / employer** it was delivered through (if any)
- [ ] **Year(s)**
- [ ] **The brief / constraints** you were given
- [ ] **Your process** — research method, stakeholder sign-off, IA work, testing
- [ ] **A measurable result** — adoption, completion rate, tickets reduced, funds raised, sign-off

Case studies with `todo` markers: QNL, GAMA, GRSIA (Daman), QU, SASO, MCIT, MECC,
Jood Eskan (web), Jood Eskan (kiosk), Optimum Vision, TRAGS, Me7rab, QPMC, CCQ, Surah.

Plus the 3 `confirm` fact-checks (Q3).

**Progress:** _none yet — awaiting content._

---

## 5. Phase 5 — Optional, your call ⛔

| Item | What's involved | Decision (Q#) |
|------|-----------------|---------------|
| Custom domain | You provide a domain + set 4 DNS records; I add `CNAME` + wait for cert | Q8 |
| Analytics | You create a GoatCounter (free) or Plausible (paid) account; send me the snippet; I add it to `<head>` | Q9 |
| Contact form | You create a Formspree/Web3Forms endpoint; I swap the Contact page `mailto:` for a real `<form>` with validation + a thank-you state | Q10 |
| Root URL | Rename repo to `omnia-amer.github.io`; I update `canonical`, `og:url`, `sitemap`, `404.html`, README | Q7 |
| Light theme | New palette + toggle + testing every route in both themes | Q12 (likely skip) |

---

## 6a. Lighthouse read — 2026-09-02 (route: `#/work/case-qnl`, Moto G Power, Slow 4G)

| Category | Score | |
|----------|-------|---|
| Performance | **58** | mostly contaminated — see below |
| Accessibility | **100** | ✅ |
| Best Practices | **96** | ✅ (the −4 is a Chrome "Issues panel" logging entry) |
| SEO | **100** | ✅ structured data valid |

Core Web Vitals: FCP 2.0 s · **LCP 4.1 s** · **TBT 1,850 ms** · **CLS 0** ✅ · SI 2.0 s

**The Performance 58 is not a real reflection of the site.** Lighthouse itself flagged:
*"Chrome extensions negatively affected this page's load performance."* The report shows
"Reduce unused JavaScript — **4,315 KiB**", "Minimize main-thread work — 5.5 s",
"Reduce JS execution — 2.9 s", TBT 1,850 ms. **This site's own JS is ~10 KB.** Those numbers are
Grammarly / Adobe / other extensions injecting into the page.

➡ **Re-run in an Incognito window** (extensions disabled) — Performance should land in the 80s–90s.

**Real issues in the report, and what was done:**

| Finding | Est. saving | Action |
|---------|-------------|--------|
| LCP image was `loading="lazy"` | LCP ↓ | ✅ Fixed — first image on every `work/case-*` page is now `loading="eager" fetchpriority="high"` (commit `a79e7f6`) |
| Render-blocking font stylesheet | ~450 ms | ✅ Fixed — loads via `media="print"` + `onload` swap + `<noscript>` (commit `a79e7f6`) |
| "Improve image delivery" | ~258 KiB | ⬜ **S3** — convert JPEGs to WebP (needs `cwebp`/Squoosh locally; can't in build env) |
| "Use efficient cache lifetimes" | ~369 KiB | ⛔ **Can't on GitHub Pages** — it serves a fixed 10-min cache, no custom headers. Only fixable by fronting with Cloudflare or moving to Netlify/Cloudflare Pages. |
| "Reduce unused CSS — 341 KiB" | small real cost | ⬜ Low priority — all routes' CSS is inlined in one `<style>` (~30 KB, ~8 KB gzipped). Per-route CSS splitting is a big refactor for little gain. |

**Next Lighthouse run should be in Incognito**, on `#/work/case-qnl` (a heavy case page) *and* `#/` — record both in §8.

---

## 6. Suggestions (not yet scheduled)

- **S1 — Re-run Lighthouse in Incognito** (done once with extensions on — see §6a; the Perf number was contaminated). Incognito = extensions off = the real score.
- **S2 — Manual screen-reader pass.** VoiceOver (Mac) or NVDA (Windows): tab through the nav, trigger the skip link, change routes, confirm the heading is announced. Automated checks can't fully cover this.
- **S3 — Convert images to WebP.** The 141 JPEGs are ~11 MB on disk; WebP would roughly halve that and speed up case-study pages further. Low risk, one scripted pass.
- **S4 — Trim `<meta name="description">` to ~155 chars.** Currently 210 — Google truncates it in results. The `og:`/`twitter:` ones can stay long.
- **S5 — Add `<lastmod>` to `sitemap.xml`** on each deploy (or just once now).
- **S6 — `rel="me"` links** to LinkedIn/Behance for identity verification (Mastodon-style, low effort).
- **S7 — Real-device check.** Emulation ≠ real iOS Safari / Android Chrome. Worth 5 minutes on an actual phone.
- **S8 — If content will change often,** consider splitting case studies into a small data file the page renders from, instead of hand-editing 15 blocks of HTML. Only worth it if Phase 4 turns into ongoing edits.

---

## 7. Next steps (in order)

1. ~~LinkedIn Post Inspector~~ — done, warning cleared (2026-09-02).
2. ~~First Lighthouse run~~ — done (§6a). **Re-run in Incognito** for the true Perf score, record both `#/work/case-qnl` and `#/` in §8.
3. **You:** answer §3 — especially **Q2** (content for the 14 case studies that still have `todo` markers; QNL is already done).
4. **You → me:** send full detail for one case study.
5. **Me:** wire that case study in as the template; you review the format.
6. **Me:** roll the same through the rest as you supply content; drop `.todo{display:none}` when all done.
7. **Me:** any Phase 5 items you greenlight (Q7–Q10).
8. **Me (needs your local tooling for S3):** WebP images, `<meta description>` trim (S4), sitemap `lastmod` (S5), `rel="me"` (S6) — one polish commit.

---

## 8. Verification log

Checklist to run after each change: site loads & all routes render · Lighthouse (mobile) ·
social card renders · Download CV returns a valid PDF · no console errors · keyboard-only pass.

| Date | Phase | Perf | A11y | SEO | BP | Notes |
|------|-------|------|------|-----|----|-------|
| _tbd_ | baseline | | | | | before any changes |
| 2026-09-01 | Phase 1 | — | — | — | — | Lighthouse unavailable in build env. Substituted: 0 console errors, 0 broken images all routes, contrast 6.25:1, meta/JSON-LD valid, 47/47 todo notes hidden. |
| 2026-09-02 | Phase 2 | — | — | — | — | 14 MB → 192 KB; 141 imgs + video + CV externalised, all load live; width/height + lazy on all imgs; LinkedIn scraper unblocked. |
| 2026-09-02 | Phase 3 | — | — | — | — | Skip link + SPA focus mgmt + focus rings, verified live; router intact. |
| 2026-09-02 | QA sweep | — | — | — | — | Desktop + mobile (375 px): all routes render, images load, hamburger works, skip link → real `<main>`, aria-live present, focus rings visible, 0 site console errors. Descriptions → ~194 chars. |
| 2026-09-02 | Lighthouse (case-qnl, **extensions on**) | 58 | 100 | 100 | 96 | CLS 0 ✅. Perf contaminated by browser extensions (4,315 KiB unused JS not from this site). LCP 4.1s / TBT 1,850ms. |
| 2026-09-02 | perf fixes | — | — | — | — | Commit `a79e7f6`: LCP image eager+fetchpriority per case page; font CSS non-blocking (−450ms). Fonts verified still rendering. |
| _tbd_ | **Lighthouse in Incognito** | ? | ? | ? | ? | **← re-run with extensions off, `#/work/case-qnl` + `#/`** |
