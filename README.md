# Shahnawaz — Animated Bio Website

A fast, responsive bio site built with **React + Vite + Tailwind + Framer Motion**.

## Local Setup
```bash
# 1) Extract the zip
# 2) In this folder, install deps:
npm install

# 3) Start dev server
npm run dev
```

## Deploy to Netlify (easiest)
1. Create a Netlify account.
2. Click **Add new site → Deploy manually**.
3. Run locally: `npm run build` (creates `dist/`).
4. Drag-and-drop the `dist/` folder into Netlify.

## Deploy to GitHub Pages
1. Create a new GitHub repo, e.g. `shahnawaz-bio`.
2. Push this project to that repo.
3. In repo **Settings → Pages**, set **Source** to **GitHub Actions** and pick a Vite React workflow (or add a simple action):

Create `.github/workflows/pages.yml` with:
```yaml
name: Deploy Vite site to Pages
on:
  push:
    branches: [ main ]
permissions:
  contents: read
  pages: write
  id-token: write
concurrency:
  group: "pages"
  cancel-in-progress: true
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

## Customize
- Edit social links in `src/App.jsx` (SOCIALS array).
- Tweak colors/animations directly in `src/App.jsx`.
- Tailwind config: `tailwind.config.js`.
- 
