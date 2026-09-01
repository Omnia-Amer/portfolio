# Omnia Amer — Portfolio

Personal portfolio site for Omnia Amer, Senior UI/UX Designer.

**Live:** <https://omnia-amer.github.io/portfolio/>

Static site, no build step. Hash-routed single-page app (`index.html` + inline CSS/JS)
with assets served from `assets/`.

## Structure

| Path | What |
|------|------|
| `index.html` | The whole site — markup, styles, and the client-side router |
| `assets/img/` | Case-study screenshots (`001.jpg` … `141.jpg`) |
| `assets/media/` | Case-study video clips (webm + mp4) |
| `assets/Omnia_Amer_CV.pdf` | CV, linked from the "Download CV" buttons |
| `favicon.svg` · `og-image.png` | Tab icon and social-share card |
| `robots.txt` · `sitemap.xml` · `404.html` | SEO + SPA fallback redirect |
| `ENHANCEMENTS.md` | Improvement plan and its status |

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
- Case studies still contain `<mark class="todo">` placeholders, hidden via
  `.todo{display:none}` until the real detail is written in (see `ENHANCEMENTS.md`, Phase 4).
