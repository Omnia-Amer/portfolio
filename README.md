# Omnia Amer — Portfolio

Personal portfolio site for Omnia Amer, Senior UI/UX Designer.

**Live:** <https://omnia-amer.github.io/portfolio/>

Static site, no build step. Hash-routed single-page app (`index.html` + inline CSS/JS)
with assets served from `assets/`. Bilingual: English + Arabic (RTL) via a header
toggle, with the Arabic strings in `i18n-ar.js` (lazy-loaded on first switch to عربي,
persisted in `localStorage`).

## Structure

| Path | What |
|------|------|
| `index.html` | The whole site — markup, styles, and the client-side router |
| `i18n-ar.js` | Arabic translation dictionary + RTL text-node swap |
| `assets/img/` | Case-study screenshots (`001.jpg` … `168.jpg`) + client logos (`logo-*.png/.svg`) |
| `assets/media/` | Case-study video clips (webm + mp4) |
| `assets/og/` | Per-case 1200×630 social-share cards (`case-*.jpg`) |
| `assets/Omnia_Amer_CV_2026.pdf` | CV, linked from the "Download CV" buttons (`?v=2` cache-bust). `assets/Omnia_Amer_CV.pdf` is a legacy-name copy of the same file. |
| `work/<case-id>/` · `ar/` | Static SEO stubs — real URLs with per-page `<title>`/OG meta that redirect a human into the SPA |
| `favicon.svg` · `og-image.png` | Tab icon (sparkle) and site-level social-share card |
| `robots.txt` · `sitemap.xml` · `404.html` | SEO + SPA fallback redirect |
| `ENHANCEMENTS.md` | Status, plan, and open decisions |

## Third-party services (no backend)

- **Contact form** → [FormSubmit](https://formsubmit.co) emails enquiries to `Omniaamer835@gmail.com`
  (activated; free). Secondary button opens WhatsApp (`wa.me/201558092205`) with the same pre-filled text.
- **Analytics** → [GoatCounter](https://omnia.goatcounter.com) (`omnia.goatcounter.com`), cookie-free,
  counts SPA hash routes.

## Edit and deploy

Edit `index.html` (or swap an asset), then:

```bash
git add -A && git commit -m "…" && git push
```

GitHub Pages redeploys `main` automatically in ~1 minute.

## View locally

Serve the folder over HTTP (opening `index.html` via `file://` breaks the asset paths):

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Notes

- `.nojekyll` is present so Pages serves every file as-is.
- The site is dark-theme only, by design.
- Every case study carries real Brief / Approach / Outcome copy — the old
  `<mark class="todo">` placeholders are gone (see `ENHANCEMENTS.md`, Phase 4).
