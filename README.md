# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend using TypeScript with type-aware lint rules enabled. Check out the [TS template](https://github.com/vitejs/vite/tree/main/packages/create-vite/template-react-ts) for information on how to integrate TypeScript and [`typescript-eslint`](https://typescript-eslint.io) in your project.


## How to deploy application on Github pages

1. Install gh-pages package
In your React project, run:

npm install gh-pages --save-dev

2. Update package.json
Add a homepage field at the top level (replace your-username and your-repo with yours):

"homepage": "https://your-username.github.io/your-repo"
Add deploy scripts:

"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d build",
  ...
}

3. Push your code to GitHub
If not already:

git init
git remote add origin https://github.com/your-username/your-repo.git
git branch -M main
git add .
git commit -m "Initial commit"
git push -u origin main

4. Deploy to GitHub Pages
Run:
npm run deploy
This creates a gh-pages branch in your repo and uploads the build files.

5. Enable GitHub Pages in Repo Settings
Go to your repository on GitHub.

Navigate to Settings → Pages.

Under Branch, choose gh-pages branch and root /.

Save.

6. Access Your Site 🎉
Your app will be live at:

https://your-username.github.io/your-repo
✅ Done! Each time you want to redeploy after changes, just run:

npm run deploy

7. if build is getting saved in dist file

"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist",
  "build": "vite build",
  "dev": "vite"
}

Also set correct base path in Vite
Since you’re deploying to GitHub Pages (inside a repo, not root domain), add base in your vite.config.js (or vite.config.ts):

import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: "/your-repo-name/",  // <-- replace with your repo name
})
Example: if repo name is profile, then:

base: "/profile/"