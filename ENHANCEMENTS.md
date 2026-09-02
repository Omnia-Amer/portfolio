# Portfolio — Status & Plan

Live: <https://omnia-amer.github.io/portfolio/> · Repo: `Omnia-Amer/portfolio` · Updated: 2026-09-02

Legend: ✅ done · 🟡 partial · ⬜ open · ⛔ blocked on Omnia · ❌ declined

---

## TL;DR

- **The site is live, fast (192 KB, down from 14 MB), accessible (Lighthouse A11y 100, SEO 100), and mobile-clean.**
- **Contact form works and is verified** — it emails Omnia (FormSubmit, activated), shows "Message sent ✓", and offers WhatsApp as a second option. Test emails were sent to Omniaamer835@gmail.com — check inbox/spam.
- **Analytics live** at `omnia.goatcounter.com`.
- **Favicon + logo** are now a colourful sparkle.
- **Case-study role / employer / year are filled from the CV.** What's left is the *narrative* (brief, process) and *results* — that needs Omnia (the CV has no metrics; nothing to invent).
- **One real decision outstanding: Q14 (metrics).** Plus optional items (custom domain, light theme, hi-res images).

---

## 1. Status at a glance

| Area | Status | Notes |
|------|--------|-------|
| Site live & public | ✅ | GitHub Pages, HTTPS enforced |
| Page weight | ✅ | 14 MB → **192 KB** — images/video/CV moved to `assets/` |
| Image performance | ✅ | intrinsic `width`/`height` + `loading` tuned on all 141 images; **CLS 0** |
| Social share card | ✅ | OG + Twitter + `og-image.png`; descriptions ≥ 100 chars (LinkedIn clean) |
| SEO | ✅ | canonical, JSON-LD `Person`, `robots.txt`, `sitemap.xml` — Lighthouse SEO **100** |
| Accessibility | ✅ | contrast AA, skip link, SPA focus management, focus rings — Lighthouse A11y **100** |
| 404 / deep links | ✅ | `404.html` = tiny hash-preserving redirect |
| Mobile | ✅ | verified 375 px — hamburger nav works |
| Placeholder "todo" notes | ✅ hidden | 41 markers hidden by CSS until real content lands |
| **Contact form** | ✅ verified | Email-first via FormSubmit → "Message sent ✓"; WhatsApp is a secondary button. Both tested live. |
| **Analytics** | ✅ verified | GoatCounter at `omnia.goatcounter.com` — count returns 200, SPA routes tracked |
| **Favicon + logo mark** | ✅ | colourful gradient sparkle (✨) + gold twinkle; logo mark matches, spins on hover |
| Case-study role / year / employer | ✅ | from CV — role = "Senior UI/UX Designer" on all 15; GAMA + MECC = Mannai / 2024–Present (confirmed) |
| Case-study brief / process / results | ⛔ | still `todo` on 14 studies — needs Omnia's input (see §4) |
| Lighthouse Performance | 🟡 | **58** with extensions on — contaminated; needs an Incognito re-run (see §5) |
| Image compression / WebP | ❌ | declined — Omnia wants maximum quality / hi-res |
| Cache lifetimes / custom domain | ⬜ | needs Cloudflare + a custom domain (see §5) |

---

## 2. What was done (all live on `main`)

**Phase 1 — SEO / social / polish** (`673510b`)
author + canonical + theme-color · full OG + Twitter Card · `og-image.png` (1200×630) · JSON-LD `Person` ·
fonts moved out of `@import` · contrast `--ink-faint` .40→.55 (3.7:1 → 6.25:1) · `robots.txt` + `sitemap.xml` + `404.html` · dark-tab favicon.

**Phase 2 — assets & performance** (`c68dc9f`, `c78174c`) — **`index.html` 14 MB → 192 KB**
141 base64 images → `assets/img/` · video → `assets/media/` · CV → `assets/Omnia_Amer_CV.pdf` (native `<a download>`) ·
`width`/`height` + `loading="lazy"` on every image · `404.html` slimmed to a redirect.

**Phase 3 — accessibility** (`c3370c5`)
skip link → active `<main>` · focus moves to the new page heading on route change + `aria-live` announce ·
real `:focus-visible` outlines · reduced-motion respected.

**Session 2 (2026-09-02)** (`2da786f` … `4c90f6f`)
- Perf: LCP image per case page `eager` + `fetchpriority=high`; fonts non-render-blocking (`media=print` + `onload`).
- **Contact form** (Contact page): name / company / email / topic / message → emails Omnia via **FormSubmit** (activated), shows **"Message sent ✓"**, resets. Secondary **"or message on WhatsApp"** button carries the same pre-filled text. Honeypot + native no-JS `action` fallback.
- **GoatCounter** analytics — manual count so SPA hash routes register. Site `omnia.goatcounter.com` created & verified.
- Case-study meta from the CV: **role = "Senior UI/UX Designer" on all 15**; GAMA + MECC → `Mannai Corporation / 2024 – Present` (confirmed by Omnia).
- **Favicon** → colourful gradient sparkle + gold twinkle (file + inline data-URI).
- **Logo mark** (header + footer) → matching sparkle via CSS mask + gradient; gentle twinkle, spin on hover; reduced-motion disables it.
- Descriptions lengthened to ~194 chars. README rewritten for the `assets/` layout.

---

## 3. Answered questions

| Q | Answer |
|---|--------|
| Q4 · profile URLs (`behance.net/omnia-amer`, `dribbble.com/Omniaamer`, `linkedin.com/in/omni-aamer/`) | **Correct** — kept in JSON-LD + footer |
| Q5 · phone `+20 155 809 2205` + email public | **Correct, OK to expose** |
| Q6 · `assets/Omnia_Amer_CV.pdf` current? | **Keep for now**, will be updated — replace the file in `assets/`, same name, when ready |
| Q9 · analytics | **GoatCounter** — done & verified |
| Q10 · contact form | **Done & verified** — email-first + WhatsApp secondary |
| Q13 · GAMA + MECC = Mannai / 2024–Present | **Confirmed correct** |

---

## 4. Phase 4 — case-study content ⛔ (needs Omnia)

Role, employer, and years are filled from the CV. Still `todo` on **14 case studies**
(GAMA, GRSIA/Daman, QU, SASO, MCIT, MECC, Jood Eskan web, Jood Eskan kiosk, Optimum Vision, TRAGS, Me7rab, QPMC, CCQ; QNL needs only 2). Surah is complete.

Per study, needed:
- [ ] **The brief / constraints** you were given
- [ ] **Your process** — research method, stakeholder sign-off, IA work, testing
- [ ] **A result** — see Q14 below

Plus the 3 `confirm` markers (unverified claims incl. a Guinness World Record reference — accurate as written? = Q3).

**Fastest path:** send everything for **one** study → it's wired in as the template → you review the format → we roll through the rest → the `.todo{display:none}` line comes out.

### ⚠️ Q14 — the results/metrics line (the one real blocker)

The CV has **no numbers** — it's titles, employers, dates, project names. Nothing to "calculate".
Inventing metrics for a job-search portfolio would be fabricating credentials — not doing that. Pick one:

- **(a)** give real figures per project, or
- **(b)** replace the "measurable result" sentence with a true qualitative outcome ("shipped and in production", "adopted across all N colleges" — only if true), or
- **(c)** drop that sentence and let the work speak.

---

## 5. Open decisions & known limits

| Item | Detail | Q |
|------|--------|---|
| **Root URL** | Move `…github.io/portfolio/` → `omnia-amer.github.io` (cleaner on a CV). One repo rename + I update canonical/OG/sitemap/404/README. | Q7 |
| **Custom domain** | e.g. `omniaamer.com` — you buy it + set DNS, I add `CNAME`. **Also the only way to fix the cache-lifetime Lighthouse item** (via free Cloudflare in front). | Q8 |
| **Lighthouse Perf 58** | Contaminated — Lighthouse flagged *"Chrome extensions negatively affected this page"* (4,315 KiB "unused JS" — the site's own JS is ~10 KB; that's Grammarly/Adobe/etc.). **Re-run in Incognito** on `#/work/case-qnl` + `#/`; expect 80s–90s. Real fixes already shipped: LCP image eager, non-blocking fonts. |
| **"Improve image delivery" (~258 KiB)** | ❌ Declined — max quality wanted. Accepted trade-off. | Q15 |
| **"Efficient cache lifetimes" (~369 KiB)** | ⛔ Impossible on bare GitHub Pages (fixed 10-min cache, no custom headers). Needs Cloudflare / Netlify. | Q8 |
| **Hi-res images** | Sources are 480–1150 px. Can't upscale to 4K here. If you have Figma @2×/@3× or full-res exports, drop them into `assets/img/` (same filenames) → I update dimensions. | Q15 |
| **og-image font** | Current `og-image.png` uses a metric-compatible fallback, not real Outfit. Cosmetic. | Q11 |
| **Light theme** | Big effort; site is dark by design. Likely skip. | Q12 |

### Smaller polish (one commit, any time)
- Trim `<meta name="description">` to ~155 chars (currently 210 — Google truncates).
- Add `<lastmod>` to `sitemap.xml`.
- `rel="me"` links to LinkedIn/Behance.
- Manual screen-reader pass (VoiceOver / NVDA).
- Real-device check (actual iOS Safari / Android Chrome).

---

## 6. Next steps

**Omnia — now:**
1. Hard-refresh the site (Ctrl+Shift+R) / use a private window — earlier "form not working" was a cached old build.
2. Check inbox **and spam** for the FormSubmit test emails ("Omnia Self-Test"). Mark "not spam" so real enquiries land in the inbox.
3. Delete the ~7 debug test emails/analytics hits from today.
4. Re-run Lighthouse in **Incognito**; paste scores into §7.
5. **Answer Q14** (results line: real numbers / qualitative / drop).

**Then:**
6. Send one full case study → template → roll through the other 13.
7. Decide Q7 / Q8 / Q11 / Q12; supply hi-res images (Q15) if you have them.

---

## 7. Verification log

| Date | Item | Perf | A11y | SEO | BP | Notes |
|------|------|------|------|-----|----|-------|
| 2026-09-01 | Phase 1 | — | — | — | — | 0 console errors, 0 broken images, contrast 6.25:1, meta/JSON-LD valid, todo notes hidden |
| 2026-09-02 | Phase 2 | — | — | — | — | 14 MB → 192 KB; assets externalised & load; CLS-safe img dims; LinkedIn unblocked |
| 2026-09-02 | Phase 3 | — | — | — | — | skip link + focus mgmt + focus rings; router intact |
| 2026-09-02 | QA sweep (desktop + 375 px) | — | — | — | — | all routes render, images load, hamburger works, aria-live present, 0 site console errors |
| 2026-09-02 | Lighthouse — case-qnl, **extensions ON** | **58** | **100** | **100** | **96** | CLS 0 ✅; Perf contaminated by extensions (see §5); LCP 4.1 s |
| 2026-09-02 | perf fixes (`a79e7f6`) | — | — | — | — | LCP img eager; fonts non-blocking (−450 ms) |
| 2026-09-02 | branding + form v1 (`…6e677c4`) | — | — | — | — | sparkle favicon + logo mark; WhatsApp form; GoatCounter loads |
| 2026-09-02 | pipeline (`14ac6a7`, `7b9abae`) | — | — | — | — | FormSubmit `success:true`; GoatCounter 200; real-Chrome: form → WhatsApp with full message (3×); 8 routes render; 141 imgs 0 broken; 0 site errors |
| 2026-09-02 | **email-first form** (`6906ac2`) | — | — | — | — | Real Chrome: "Send message" → **"Message sent ✓"**, form resets, POST `{"success":"true"}`. 2 test emails to Omniaamer835@gmail.com. |
| _tbd_ | **Lighthouse — Incognito** | ? | ? | ? | ? | ← re-run, extensions off, `#/work/case-qnl` + `#/` |
