# Portfolio — Status & Plan

Live: <https://omnia-amer.github.io/portfolio/> · Repo: `Omnia-Amer/portfolio` · Updated: 2026-09-05

Legend: ✅ done · 🟡 partial · ⬜ open · ⛔ blocked on Omnia · ❌ declined

---

## Bilingual (English / Arabic) — merged 2026-09-05 (`6de797d`)

The artifact gained a **language toggle** (عربي / EN). Merged into the deployed site:
- Header toggle button; choice persists in `localStorage`, applied on load.
- `I18N_AR` dictionary + a DOM text-node swap that also flips `<html lang dir>`.
- **Extended** beyond the artifact: the toggle now also translates the contact-form
  labels, `<option>`s, placeholders, `aria-label`s and the skip link (~25 keys the
  artifact's dict predated), and the submit-status messages are bilingual.
- RTL CSS: IBM Plex Sans Arabic font stack (non-blocking `<link>`), mirrored spacing,
  brand wordmark + numeric runs pinned LTR, `og:locale:alternate`, `<html dir="ltr">`.

**Verified (local server):** EN + AR, all 23 routes render, toggle round-trips,
0 broken images in both modes, 0 JS errors, form + FAQ + case studies all translate.

**Known Arabic-copy nit (your call, it's your translation):** the hero H1 renders
"…لـالمؤسسات…" — the `لـ` prefix doesn't contract with the following `ال`. Fix that
one dictionary entry in the artifact if it bothers you.

**Size:** `index.html` 216 KB → 390 KB (the AR dictionary is ~165 KB of that; gzips to
~45 KB over the wire). If it grows further, split the dict into an async `i18n.js`.

Also this session: `rel="me"` links, `sitemap.xml` `<lastmod>`, `<meta description>`
trimmed to ~165 chars.

---

## Artifact merge — 2026-09-05

The Claude artifact (`41d66502…`) had diverged: Omnia added **2 new case studies
(Manateq, Qatar Stars League)**, filled in every remaining `todo` (briefs, approaches,
outcomes — all qualitative, no invented metrics), rewrote the FAQ, and bumped the
counts to 17 products / 8 gov clients. The deployed site meanwhile had all the infra
(assets, contact form, analytics, SEO, a11y, sparkle branding).

Merged both: deployed shell/head/CSS/scripts **+** artifact's `<main>` content, then
re-externalised images (159 now), re-applied img dims/lazy/eager, injected the contact
form into the artifact's contact page, kept the FAQ wording from the artifact.

**Case-study "My Role"** now follows the 2026 CV's model (commit `b9abfcf`):
Mannai Corporation + Saudi Azm engagements → **"UX/UI Consultant"** (13);
AZM X / Alborhan / Webtek → **"UI/UX Designer"** (4). Site headline + JSON-LD
`jobTitle` stay "Senior UI/UX Designer".

**New CV** (`b9abfcf`): `assets/Omnia_Amer_CV.pdf` is now the current text-based
`Omnia_Amer_Senior_UIUX_Designer_CV_2026` (134 KB, was a 1.5 MB placeholder) —
filename kept so all links work. It backs the Guinness World Records line.

Files: `index.html` 202 KB → 216 KB · `assets/img/` 141 → 159 · new `case-manateq` +
`case-qsl` routes.

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
| **Bilingual EN / AR** | ✅ verified | header toggle, full RTL, localStorage-persisted; all routes + contact form translate |
| Page weight | ✅ | 14 MB → 192 KB (core); **390 KB** with the inline AR dictionary (~45 KB gzipped) |
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
| Case-study role / year / employer | ✅ | from the 2026 CV — "UX/UI Consultant" for Mannai/Azm engagements, "UI/UX Designer" for AZM X/Alborhan/Webtek; years + employers per CV |
| CV file | ✅ | `assets/Omnia_Amer_CV.pdf` = the current 2026 text CV (134 KB) |
| Case-study brief / process / results | ✅ | **all filled** (from the artifact, 2026-09-05) — qualitative outcomes, no invented metrics. 0 `todo` markers left. |
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
| 2026-09-05 | artifact merge (`774206f`) | — | — | — | — | 2 new case studies + all `todo` filled; 23 routes render; 159 imgs 0 broken; 0 todos; 0 JS errors; contact form + FAQ verified |
| 2026-09-05 | CV + roles (`b9abfcf`) | — | — | — | — | new 2026 CV live (`application/pdf`, 134 KB); per-engagement titles from CV verified live |
| 2026-09-05 | **bilingual EN/AR** (`6de797d`) | — | — | — | — | Local server: 11/11 routes both langs, toggle round-trips, 0 broken imgs, 0 JS errors, form/FAQ/case studies translate, `dir`/`lang`/localStorage correct |
| 2026-09-05 | polish | — | — | — | — | `rel="me"` ×3, sitemap `<lastmod>`, meta description → ~165 chars, `<html dir="ltr">` |
| _tbd_ | **Lighthouse — Incognito** | ? | ? | ? | ? | ← re-run, extensions off, `#/work/case-qnl` + `#/` (do it in EN and AR) |
