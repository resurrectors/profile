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


## How to manage environment variables

⚙️ How to Manage Environment Variables in Vite + React
1. Use .env Files for Each Environment
Create separate .env files at your project root:

.env                # default (applies everywhere)
.env.development    # only for dev
.env.staging        # only for staging
.env.production     # only for prod
Example:

.env.development

  VITE_API_URL=http://localhost:5000/api
  VITE_MODE=development
.env.staging

  VITE_API_URL=https://staging.example.com/api
  VITE_MODE=staging
.env.production

  VITE_API_URL=https://api.example.com
  VITE_MODE=production

⚠️ Important: In Vite, env variables must start with VITE_ to be exposed to the client.

2. Access Variables in Your React Code
console.log(import.meta.env.VITE_API_URL);
3. Build for Different Environments
When you run:

npm run dev
→ Vite automatically loads .env.development.

When you run:

npm run build
→ By default it loads .env.production.

If you want staging build:

vite build --mode staging
That will load .env.staging.

4. Update package.json Scripts for Easy Switching
"scripts": {
  "dev": "vite",
  "build:dev": "vite build --mode development",
  "build:staging": "vite build --mode staging",
  "build:prod": "vite build --mode production",
  "deploy:staging": "vite build --mode staging && gh-pages -d dist",
  "deploy:prod": "vite build --mode production && gh-pages -d dist"
}
Now you can easily run:

npm run build:staging
npm run deploy:prod
5. Secure Secrets
Don’t put API keys/secrets directly in client-side .env (they’re exposed after build).

For secrets → keep them on a backend or use a serverless function (Netlify functions, Firebase, etc.).

✅ With this setup:

Local dev → .env.development

Staging → .env.staging

Production → .env.production

Easy to switch with --mode or npm scripts.

