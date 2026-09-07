# Portfolio — Status & Plan

Live: <https://omnia-amer.github.io/portfolio/> · Repo: `Omnia-Amer/portfolio` · Updated: 2026-09-07

Legend: ✅ done · 🟡 partial · ⬜ open · ⛔ blocked on Omnia · ❌ declined

---

## Artifact reconciliation + 18th case study + polish — 2026-09-07 (shipped)

Commits `8b3f3fd` · `5237c44` · `e26724a` · `d6cc139` · `9e29b31` · `5c2685e` — all live.

Diffed the deployed site against the design master (artifact `41d66502…`). **CSS / design
system: zero drift** — every departure (non-blocking fonts, `--ink-faint` .40→.55 for AA,
sparkle mark, a11y block, contact-form CSS, RTL rules, E4 lightbox) is a documented
improvement. All 17 shared case narratives are byte-identical to the artifact.

**Polish pass (same day):**
- `og-image.png` regenerated at **18 SHIPPED PRODUCTS** (was 17); `?v=2`→`?v=3` everywhere.
- Work-page intro "Seventeen … enterprise" → "Eighteen … enterprise and lifestyle".
- **Hero**: added bottom padding (`168px 0 104px` / `120px 0 64px`) — the project mosaic
  was sitting flush against the `#impact` divider line.
- **Mosaic**: uniform matte — every `.mcell` insets its screenshot 8px on a `--surface-2`
  card with concentric radii, so tiles read consistently regardless of each captured
  site's own background (QNL grey margins vs SASO white bleed etc.).
- **8-point grid**: snapped off-grid spacing (forms, skills, tool badges, footer, skip
  link, lightbox, `.mtag`) to multiples of 8. `.wrap` 135px gutter kept by request;
  deliberate 2px cell-divider gaps and 1px borders left alone.
- AR: "Saudi Azm" → **عزم السعودية** (was أزم السعودية).

**Ported the one thing the site was missing — `case-clayton`** (Clayton Art House, craft
studio, Alexandria/Egypt, freelance, 2023), which the artifact had in full and the repo had
nowhere:
- `assets/img/160–167.jpg` — 8 case screenshots (decoded from the artifact's base64, all 900w);
  `assets/img/168.jpg` — mosaic crop (654×805).
- `index.html` — new `#/work/case-clayton` detail page (cd-num 16, verbatim brief/approach/
  outcome + 8 captions); home mosaic tile (→ 18); `#/work` card under **Featured Projects (08)**;
  **stat tile 17 → 18**; 3 `<meta>` descriptions 17 → 18 (Gulf/gov prose kept per Omnia).
- `work/case-clayton/index.html` — E5 static SEO stub + redirect.
- `sitemap.xml` — `case-clayton` entry (18 case URLs now).
- `i18n-ar.js` — +23 Arabic keys covering every Clayton string (h3, tag, meta, 8 captions,
  3 copy paragraphs, mosaic/card labels). **Needs a native-speaker review before it ships.**

**Role labels:** artifact has 6 inconsistent variants; deployed site's normalized 2
(`UX/UI Consultant` ×13, `UI/UX Designer` ×4, per the CV) is the keeper — **fix the artifact**,
not the site.

### Open follow-ups from this pass
| Item | Detail |
|------|--------|
| ⬜ `assets/og/case-clayton.jpg` | Bespoke 1200×630 share card (E5 pattern). `card-clayton.html` (a self-contained generator, sent to Omnia) produces it — save its output to `assets/og/`, then point the stub's `og:image`/`twitter:image` back at it (currently falls back to the site-level `og-image.png?v=3`). |
| ✅ `og-image.png` | Regenerated at **18** (`5237c44`). |
| ⬜ Arabic review | Native-speaker pass over the 23 new Clayton `i18n-ar.js` keys + the reworded Work-page intro key. |
| ⬜ `ar/index.html` | Says "17 منتجًا … عبر قطر والسعودية والإمارات" — left at 17 (Clayton is neither Gulf nor public-sector); confirm that's the intent, or reword. |
| ⬜ EN vs AR count | EN meta now says "18 delivered"; AR meta stays "17". Decide whether to align. |
| ⬜ `.cd-num` (pre-existing) | `case-joodeskan` has none; `case-joodeskan-kiosk` and `case-manateq` both show "14". Not caused by this pass. |
| ⬜ "2 Countries delivered in" stat | Clayton adds Egypt; the artifact still shows "2". Confirm the intended number. |
| ⬜ Role labels in the artifact | 6 inconsistent variants; the site's normalized 2 are the keeper — republish the artifact to match. |

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

**Follow-ups (all done — see §5 Enhancements):** hero H1 wording fixed (E2); AR
dictionary split into async `i18n-ar.js`, `index.html` back to 223 KB (E1); `<title>`
/ meta / OG translated for Arabic shares + static `/ar/` landing page (E3).

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

## 4. Phase 4 — case-study content ✅ DONE

All 17 case studies now carry a real Brief / Approach / Outcome (written by Omnia in
the artifact, merged 2026-09-05). **0 `todo` markers left.** Outcomes are qualitative —
no invented metrics — so Q14 is resolved by choice (b). The Guinness World Records
line is backed by the 2026 CV.

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
| ~~**og-image numbers / font**~~ | ✅ done (`76000a4`) — `og-image.png` rebuilt at 1200×630 with **17 SHIPPED PRODUCTS · 8 NATIONAL INSTITUTIONS**, real Outfit + IBM Plex Mono, and the current gradient-sparkle mark (was the old placeholder). `og:image`/`twitter:image` carry `?v=2` so scrapers re-fetch. | Q11 |
| **Light theme** | Big effort; site is dark by design. Likely skip. | Q12 |

### Smaller polish
- ~~Trim `<meta name="description">`~~ ✅ done (~165 chars).
- ~~`sitemap.xml` `<lastmod>`~~ ✅ done.
- ~~`rel="me"` links~~ ✅ done (LinkedIn / Behance / Dribbble).
- Manual screen-reader pass — **EN and AR** (VoiceOver / NVDA); the AR pass matters most (new RTL).
- Real-device check — actual iOS Safari / Android Chrome, both languages.

### Enhancements
| # | Enhancement | Status |
|---|-------------|--------|
| E1 | Split the AR dictionary into `i18n-ar.js` | ✅ done (`c381734`) — `index.html` 390 KB → **223 KB**; English loads fetch 0 bytes of it; loads once on first switch to Arabic (or synchronously on a `?lang=ar` entry — no flash). Verified live. |
| E2 | Fix the AR hero-H1 contraction | ✅ done (`c381734`) — now "تصميم واجهات للمؤسسات التي يضع الناس ثقتهم فيها." Verified live. |
| E3 | Translate `<title>` / `<meta description>` for AR shares | ✅ done (`f4efe81`) — `applyMeta()` swaps title/description/OG/Twitter/`og:locale` EN↔AR on toggle; new static `ar/index.html` carries full Arabic OG/Twitter meta for social scrapers and redirects humans to `/portfolio/?lang=ar`; head `hreflang="ar"` → `/portfolio/ar/`; sitemap `xhtml:link` alternates. Verified live. |
| E4 | Case-study **image lightbox / zoom** (screenshots are dense; click-to-enlarge) | ✅ done (`d2fa660`) — click / Enter / Space any case-study screenshot → full-size overlay with prev·next (scoped to that case page), counter, caption from `alt`, Esc / backdrop close, focus trap + restore, body-scroll lock. Screenshots are now `role="button"` + `tabindex=0` + `aria-label`. RTL-aware; closes on route change; honours `prefers-reduced-motion`. Verified live. |
| E5 | Per-case-study OG image (share a case, get its screenshot as the card) | ✅ done (`480fefe`) — 17 bespoke **1200×630** share cards in `assets/og/case-*.jpg` (brand card: sector eyebrow + case name + byline + gradient spine + that case's own hero screenshot) and 17 **static pages at real URLs** `…/portfolio/work/<id>/` carrying per-case `<title>` / description / OG / Twitter / canonical, then redirecting a human into the SPA. `sitemap.xml` lists all 17. Verified live (pages 200, images 1200×630, redirect lands on the right case). **Note:** the rich card shows on the *clean* URL (`…/work/<id>/`) — that's the one to paste into a post / application. The in-app hash URL (`…/#/work/<id>`) still unfurls with the site-level card, because scrapers ignore `#`. |

> **E5 follow-up (optional, your call):** to make the *address-bar* URL of a case also the shareable one, the SPA would need real-path routing instead of `#/` hashes — a bigger change. Cheaper half-measures: a "copy share link" button on each case page that copies the clean URL, or point the "View Case Study" buttons at the clean URLs (costs one extra redirect on click). None are needed for the cards to work — they're about which URL people copy.

---

## 6. Next steps

**Omnia — now:**
1. Check inbox **and spam** for FormSubmit test emails; mark "not spam".
2. Delete the debug test emails / analytics hits from testing.
3. Re-run Lighthouse in **Incognito** (EN and AR); paste scores into §7.
4. Skim the Arabic side — especially the hero H1 wording (E2).

5. Share case studies using the **clean URLs** — `https://omnia-amer.github.io/portfolio/work/<case-id>/` — to get the per-case preview card (list of ids in `sitemap.xml`).

**E1–E5 are all done; `og-image.png` regenerated (17 / 8).** Still open: decide Q7/Q8/Q12, send hi-res images (Q15), optional E5 follow-up (§5). After the LinkedIn/social card matters to you, run it through the [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) once to force a re-scrape of the new card.

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
| 2026-09-05 | **E1 + E2** (`c381734`) | — | — | — | — | Live: AR dict → `i18n-ar.js`; EN load fetches **0** bytes of it, AR toggle fetches it **once**, `?lang=ar` loads it synchronously (no flash); `index.html` 390→223 KB; AR hero fixed; 7/7 AR routes, 0 broken imgs, 0 JS errors |
| 2026-09-05 | **E3** (`f4efe81`) | — | — | — | — | Live: `/portfolio/ar/` returns 200 with Arabic `<title>` + `og:locale=ar_AR` + refresh→`?lang=ar`; main-page toggle swaps `<title>`/`meta description`/`og:locale` EN↔AR both directions, 0 JS errors; sitemap + head `hreflang` updated |
| 2026-09-06 | **E4** (`d2fa660`) | — | — | — | — | Live (case-saso, case-qnl, case-gama): screenshot → overlay opens, counter `n / N`, next/prev step + disable at ends, caption = `alt`, Esc + backdrop + route-change all close, focus restores to the thumbnail, scroll-lock toggles, 0 JS errors; RTL: Arabic button labels + `ArrowLeft`=next; home page has 0 wired shots (guard OK) |
| 2026-09-06 | **E5** (`480fefe`) | — | — | — | — | Live: 17 `work/<id>/` pages return 200 with per-case `<title>` + `og:title/description/image` + canonical; 17 `assets/og/case-*.jpg` serve as `image/jpeg` 1200×630; `work/case-manateq/` redirect lands on `#/work/case-manateq` and renders that case; `sitemap.xml` has 18 `<loc>` |
| 2026-09-06 | CV link + og-image (`cadb573`, `76000a4`) | — | — | — | — | CV: both artifact links → site, old URL gone from text layer, other links intact (pdf.js). `og-image.png` live 1200×630, `17 / 8` numbers, `?v=2` on meta |
| _tbd_ | **Lighthouse — Incognito** | ? | ? | ? | ? | ← re-run, extensions off, `#/work/case-qnl` + `#/` (do it in EN and AR) |
