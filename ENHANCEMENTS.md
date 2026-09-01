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
| Favicon | ✅ | colourful gradient sparkle (✨) + gold twinkle, dark rounded square |
| Logo mark (header/footer) | ✅ | matches the favicon — sparkle, gentle twinkle, spins on hover |
| 404 / deep links | ✅ | `404.html` redirects to the app, preserving the hash |
| Mobile | ✅ | verified at 375 px — nav collapses to a working hamburger |
| Real Lighthouse scores | 🟡 | A11y **100** · SEO **100** · Best Practices **96** · Perf **58** (extension-contaminated — see §6a) · **CLS 0** |
| Contact form | ✅ | Contact page has a real form → opens WhatsApp (+201558092205) with a pre-filled message **and** emails a copy via FormSubmit so nothing is lost |
| Analytics | 🟡 | GoatCounter snippet installed (SPA-route aware). **Needs the free `omnia.goatcounter.com` site to exist** — your signup |
| Case-study role / year / employer | ✅ | filled from your CV — role = "Senior UI/UX Designer" on all 15; GAMA + MECC inferred (see §3 Q13) |
| Case-study brief / process / **metrics** | ⛔ | still `todo` — **needs your input; metrics can't be invented** (see §4) |
| Image quality (WebP/compression) | ❌ declined | you want max quality / hi-res — WebP + the ~258 KB saving are off the table (see §6a) |
| Custom domain / cache lifetimes | ⛔ | on `github.io` — the cache-header fix needs Cloudflare or a custom domain (see §6a) |

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

### Session 2 additions (2026-09-02) — commits `2da786f` … `6e677c4`
- **Perf:** LCP image on each `work/case-*` page → `loading="eager" fetchpriority="high"`; Google Fonts CSS made non-render-blocking (`media="print"` + `onload`).
- **Contact form** on the Contact page: name / company / email / topic / message → **opens WhatsApp** (`wa.me/201558092205`) with a formatted pre-filled message, **and** POSTs the same data to **FormSubmit** (AJAX) so a copy lands in your inbox even if the WhatsApp message is never sent. Honeypot + native-POST no-JS fallback. ⚠️ **You must click the FormSubmit "Activate Form" email** (sent to Omniaamer835@gmail.com the first time the form was submitted) — until then the email copy doesn't deliver; WhatsApp works regardless.
- **GoatCounter** analytics snippet added (manual count so SPA hash routes register). Needs the free site `omnia.goatcounter.com` — sign up at goatcounter.com (code: `omnia`).
- **Case-study meta filled from CV:** "My Role" = "Senior UI/UX Designer" on all 15; Client/Via/Year already present on 13; **GAMA + MECC** set to `Mannai Corporation / 2024 – Present` — *inferred* from the pattern of the other Qatar-gov engagements, **not itemised in the CV** (Q13).
- **Favicon** redesigned: colourful gradient sparkle (pink→purple→cyan) + gold twinkle on a dark rounded square. File + inline data-URI.
- **Logo mark** (header + footer) restyled to match: sparkle shape via CSS mask + the same gradient, a slow twinkle, and a spin on `.brand:hover`. `prefers-reduced-motion` disables both.

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
| Q4 | Profile URLs `behance.net/omnia-amer`, `dribbble.com/Omniaamer`, `linkedin.com/in/omni-aamer/` | — | ✅ **Answered: correct** |
| Q5 | Phone `+20 155 809 2205` + email public | — | ✅ **Answered: correct, OK public** |
| Q6 | Is `assets/Omnia_Amer_CV.pdf` current? | Download CV serves it | ✅ **Answered: keep for now, will be updated later** — swap the file in `assets/` when ready, same name |
| Q7 | Keep `…github.io/portfolio/` or move to root `omnia-amer.github.io`? | Cleaner on a CV | ⬜ open |
| Q8 | **Custom domain** (e.g. `omniaamer.com`) — own one / want one? | Also unblocks the cache-lifetime Lighthouse item via Cloudflare | ⬜ open |
| Q9 | Analytics | — | ✅ **Answered: GoatCounter** — snippet installed; **create the free site** at goatcounter.com (code `omnia`) or it won't record |
| Q10 | Contact form | — | ✅ **Answered: built** (WhatsApp + FormSubmit email backup). **Click the FormSubmit activation email.** |
| Q11 | Regenerate `og-image.png` with real Outfit font? | Cosmetic | ⬜ open (low priority) |
| Q12 | **Light theme** — confirmed skip? | Big effort; dark by design | ⬜ open |
| Q13 | **GAMA + MECC** are not in your CV. I set both to `Mannai Corporation / 2024 – Present` to match your other Qatar-gov work. **Correct?** | Currently shown as fact on those two case studies | ⬜ **verify** |
| Q14 | **Metrics** — your CV has no numbers. I will **not** invent results. Options: (a) you give real figures per project, (b) replace the "measurable result" line with a true qualitative outcome, (c) drop that sentence. Which? | Fabricated metrics on a job-search portfolio are a serious risk | ⬜ **need direction** |
| Q15 | **Hi-res images** — you want 4K/super-res. I can't upscale here, and the source screenshots are 480–1150 px wide. Do you have **higher-res exports** (Figma @2×/@3×, or full-res captures)? | Drop them into `assets/img/` (same filenames) and I'll update the dimensions | ⬜ **need files** |

---

## 4. Phase 4 — Content you supply ⛔

Replace each `<mark class="todo">` with real detail, then delete the `.todo{display:none}` CSS rule.
Fastest path: **send me everything for ONE case study**, I wire it in as the template, you review the
format, then we roll through the rest.

**Done from the CV:** Role ("Senior UI/UX Designer"), employer, and years are now filled on all 15.

**Still needed per case study — your knowledge, not on the CV:**

- [ ] **The brief / constraints** you were given
- [ ] **Your process** — research method, stakeholder sign-off, IA work, testing
- [ ] **A measurable result** — see Q14: give a real number, a true qualitative outcome, or say "drop it"

Case studies with narrative `todo` markers (14): GAMA, GRSIA (Daman), QU, SASO, MCIT, MECC,
Jood Eskan (web), Jood Eskan (kiosk), Optimum Vision, TRAGS, Me7rab, QPMC, CCQ, QNL.
(Surah has none. QNL only has the process + result markers.)

### On "metrics calculated" — why I didn't

Your CV is an experience list: titles, employers, dates, project names. **No quantitative
outcomes** ("reduced X by Y%", "N requests processed", "funds raised"). There is nothing to
calculate from. Putting invented numbers on a portfolio you send to employers is fabricating
credentials — I won't do it. Give me the real figures where you have them, or we use honest
qualitative outcomes, or we cut the metric line and let the work speak. Your call (Q14).

**Progress:** meta (role/year/employer) ✅ · narrative + metrics ⬜ awaiting you.

---

## 5. Phase 5 — Optional, your call ⛔

| Item | What's involved | Decision (Q#) |
|------|-----------------|---------------|
| ~~Analytics~~ | ✅ done — GoatCounter snippet in. **Your step:** create the free site at goatcounter.com, code `omnia` | Q9 |
| ~~Contact form~~ | ✅ done — WhatsApp + FormSubmit email backup. **Your step:** click the FormSubmit activation email | Q10 |
| Custom domain | You provide a domain + set 4 DNS records; I add `CNAME`. **Also lets Cloudflare fix the cache-lifetime Lighthouse item.** | Q8 |
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
| "Improve image delivery" | ~258 KiB | ❌ **Declined by Omnia** — wants maximum image quality / hi-res, no WebP or compression. The ~258 KB and its LCP cost are an accepted trade-off for fidelity. (If anything, images will get *bigger* — see Q15 on hi-res sources.) |
| "Use efficient cache lifetimes" | ~369 KiB | ⛔ **Not possible on bare GitHub Pages** — it serves a fixed 10-min `Cache-Control`, no custom headers. Fix requires **Cloudflare in front** (free, needs a custom domain — Q8) or moving the host to Netlify / Cloudflare Pages. |
| "Reduce unused CSS — 341 KiB" | small real cost | ⬜ Low priority — all routes' CSS is inlined in one `<style>` (~30 KB, ~8 KB gzipped). Per-route CSS splitting is a big refactor for little gain. |

**Next Lighthouse run should be in Incognito**, on `#/work/case-qnl` (a heavy case page) *and* `#/` — record both in §8.

---

## 6. Suggestions (not yet scheduled)

- **S1 — Re-run Lighthouse in Incognito** (done once with extensions on — see §6a; the Perf number was contaminated). Incognito = extensions off = the real score.
- **S2 — Manual screen-reader pass.** VoiceOver (Mac) or NVDA (Windows): tab through the nav, trigger the skip link, change routes, confirm the heading is announced. Automated checks can't fully cover this.
- ~~S3 — Convert images to WebP.~~ **Declined** — Omnia wants max quality / hi-res (Q15).
- **S4 — Trim `<meta name="description">` to ~155 chars.** Currently 210 — Google truncates it in results. The `og:`/`twitter:` ones can stay long.
- **S5 — Add `<lastmod>` to `sitemap.xml`** on each deploy (or just once now).
- **S6 — `rel="me"` links** to LinkedIn/Behance for identity verification (Mastodon-style, low effort).
- **S7 — Real-device check.** Emulation ≠ real iOS Safari / Android Chrome. Worth 5 minutes on an actual phone.
- **S8 — If content will change often,** consider splitting case studies into a small data file the page renders from, instead of hand-editing 15 blocks of HTML. Only worth it if Phase 4 turns into ongoing edits.

---

## 7. Next steps (in order)

**Your quick actions (unblock the automated parts):**
1. **Click the FormSubmit "Activate Form" email** in Omniaamer835@gmail.com — until then the contact-form email backup doesn't deliver. Then submit the form once yourself to confirm it arrives.
2. **Create the GoatCounter site** — goatcounter.com → sign up → code `omnia` (must resolve to `omnia.goatcounter.com`). Free, ~2 min.
3. **Re-run Lighthouse in Incognito** (extensions off) on `#/work/case-qnl` and `#/`; record in §8.
4. **Answer Q13** (GAMA/MECC = Mannai/2024–Present, yes/no) and **Q14** (metrics: real numbers / qualitative / drop).

**Then the content loop:**
5. Send me full detail for **one** case study (brief + process + result) → I wire it in as the template → you review.
6. I roll the same through the other 13 as you supply content; drop `.todo{display:none}` when done.

**Optional, when you decide:**
7. Q7 (root URL), Q8 (custom domain — also fixes cache lifetimes via Cloudflare), Q11 (og-image), Q12 (light theme).
8. Hi-res image sources (Q15) → drop into `assets/img/`, I update dimensions.
9. Small polish commit: `<meta description>` trim (S4), sitemap `lastmod` (S5), `rel="me"` (S6).

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
| 2026-09-02 | contact form + branding | — | — | — | — | Commits `2da786f`…`6e677c4`: WhatsApp form (URL + message verified live), FormSubmit AJAX reachable (activation email sent), GoatCounter loads, sparkle favicon + logo mark verified, 0 console errors. |
| _tbd_ | **Lighthouse in Incognito** | ? | ? | ? | ? | **← re-run with extensions off, `#/work/case-qnl` + `#/`** |
