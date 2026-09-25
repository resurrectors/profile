# Shubham Sanjay Patil - Portfolio

Personal portfolio site for **Shubham Sanjay Patil**, GenAI / AI Application Engineer.
Plain static site (no build step, no framework) hosted on **GitHub Pages**.

**Live:** https://resurrectors.github.io/profile/

---

## Structure
```
index.html                       # the whole page
assets/
  style.css                      # theme + layout (dark default, light toggle)
  script.js                      # theme toggle, mobile menu, scroll reveal
  favicon.svg                    # "SP" gradient monogram
  shubham.jpg                    # hero headshot (400x400)
  Shubham_Patil_Resume.pdf       # downloadable resume
.nojekyll                        # serve files as-is (skip Jekyll processing)
```

---

## How hosting works (read this once)

- GitHub Pages for this repo is set to **Deploy from a branch -> `master` / (root)**.
- **Every push to `master` auto-redeploys the site.** There is no build step and nothing to run -
  GitHub rebuilds Pages within ~1 minute of the push.
- The live URL never changes: **https://resurrectors.github.io/profile/**
- After a deploy, if you still see the old version, it's browser cache - hard-refresh
  (**Ctrl+F5**) or open in a private window.

> One-time setup (already done): repo **Settings -> Pages -> Source: Deploy from a branch ->
> Branch: `master`, Folder: `/(root)` -> Save**.

---

## How to make a change and publish it

1. Edit the files (see "What to edit" below).
2. Preview locally (optional, recommended) - from inside this folder:
   ```bash
   python -m http.server 8000
   # open http://localhost:8000  (Ctrl+C to stop)
   ```
   Or just double-click `index.html` to open it in a browser.
3. Commit and push:
   ```bash
   git add -A
   git commit -m "Update portfolio"
   git push origin master
   ```
4. Wait ~1 minute, then hard-refresh https://resurrectors.github.io/profile/ - your change is live.

### What to edit
- **Text / sections / links** -> `index.html`
- **Colors, spacing, fonts, layout** -> `assets/style.css` (theme colors are the CSS variables
  at the top under `:root`)
- **Headshot** -> replace `assets/shubham.jpg` (keep it roughly square; ~400x400 is plenty)
- **Resume** -> replace `assets/Shubham_Patil_Resume.pdf` (keep the same filename so the download
  link keeps working)

---

## Working on this from another computer (clone elsewhere)

1. **Clone:**
   ```bash
   git clone https://github.com/resurrectors/profile.git
   cd profile
   ```
2. **Set your commit identity** (once per machine, or `--local` for just this repo):
   ```bash
   git config user.name  "Shubham Sanjay Patil"
   git config user.email "shubhampatil26199@gmail.com"
   ```
3. Edit -> commit -> **push to `master`**:
   ```bash
   git add -A
   git commit -m "Your change"
   git push origin master
   ```
   The push triggers the same auto-deploy - the change is live at the URL above in ~1 minute.
   You don't touch any Pages settings again; they live on GitHub, not in the clone.

**Auth note:** pushing needs a GitHub login. Easiest is to push from **VS Code -> Source Control ->
Sync/Push** (it does the browser sign-in for you). In a terminal, GitHub needs a Personal Access
Token or SSH key (plain password won't work).

**Keeping clones in sync:** if you edited on another machine, run `git pull origin master` before
you start editing so you're on the latest.

---

## Notes
- `master` is the source **and** the published branch. The older `main` / `gh-pages` branches in
  this repo are not used by the site and can be ignored (or deleted later).
- This repo is independent from the `react_pages` repo - changes here never affect that site.
