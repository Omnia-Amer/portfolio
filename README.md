# Omnia Amer — Portfolio

Personal portfolio site for Omnia Amer, Senior UI/UX Designer.

Single self-contained `index.html` (all styles and images inlined). No build step.

## View locally

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

## Publish with GitHub Pages

1. Create a new repository on GitHub (e.g. `portfolio`).
2. Push this folder to it (see steps below).
3. In the repo: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After ~1 minute the site is live at `https://<your-username>.github.io/portfolio/`.

Tip: naming the repo `<your-username>.github.io` serves it at `https://<your-username>.github.io/` with no subpath.

The `.nojekyll` file is included so GitHub Pages serves the files as-is.
