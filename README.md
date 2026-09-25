# Shubham Sanjay Patil — Portfolio

Personal portfolio site for **Shubham Sanjay Patil**, GenAI / AI Application Engineer.
Static site (no build step) intended for **GitHub Pages**.

**Live (once Pages is enabled):** https://resurrectors.github.io/profile/

## Structure
```
index.html              # single-page portfolio
assets/
  style.css             # theme + layout (dark default, light toggle)
  script.js             # theme toggle, mobile menu, scroll reveal
  favicon.svg
  Shubham_Patil_Resume.pdf   # downloadable résumé
.nojekyll               # serve files as-is (skip Jekyll processing)
```

## Run locally
Just open `index.html` in a browser, or serve the folder:
```bash
python -m http.server 8000    # then visit http://localhost:8000
```

## Deploy to GitHub Pages
1. Push this repo to `github.com/resurrectors/profile`.
2. In **Settings → Pages**, set **Source = Deploy from a branch**, **Branch = master**, **Folder = / (root)**.
3. The site publishes at `https://resurrectors.github.io/profile/`.

## Editing content
All content is in `index.html`. To refresh the résumé, replace `assets/Shubham_Patil_Resume.pdf`.
