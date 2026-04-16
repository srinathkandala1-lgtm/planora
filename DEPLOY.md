# Planora v0.1 — Vercel Deployment Guide

Single-file static HTML app. Self-contained: all JS data is baked into `public/index.html`; Chart.js and SheetJS load from public CDNs; team notes persist in the browser's localStorage.

## Folder layout

```
planora-deploy/
├── public/
│   ├── index.html                    ← the Planora v0.1 app
│   └── PROPVR_Content_Plan_DB.xlsx   ← the live content DB (re-uploadable via the "⟳ Reload from Excel" button)
├── vercel.json                       ← routing + headers
├── package.json                      ← project metadata
├── .vercelignore
├── .gitignore
└── DEPLOY.md                         ← this file
```

## Option 1 — Deploy via Vercel CLI (fastest)

```bash
# one-time install
npm i -g vercel

# from inside this folder
cd planora-deploy
vercel login         # follow the prompt (Github/Google/Email)
vercel               # first run: creates a preview URL
vercel --prod        # promote to production
```

First `vercel` run will ask:
- Set up and deploy? **Y**
- Scope? Pick your Vercel team/personal account
- Link to existing project? **N** (for first deploy)
- Project name? **planora**
- In which directory is your code? **.** (current directory)
- Override settings? **N**

Vercel auto-detects this as a static site because there is no framework. It serves everything in `public/` at the root.

## Option 2 — Deploy via Git (recommended for the team)

1. Push this `planora-deploy/` folder to a private GitHub repo (e.g., `propvr/planora`).
2. Go to [vercel.com/new](https://vercel.com/new).
3. Import the repo. Vercel will detect the `vercel.json` and use `public/` as the static output.
4. Click **Deploy**. Every future `git push` to `main` auto-deploys.

## Option 3 — Drag-and-drop

Go to [vercel.com/new](https://vercel.com/new) → "Deploy a static site" → drag the `planora-deploy/` folder. Good for a one-off test.

## Local preview

```bash
cd planora-deploy
npx serve public -p 3000
# open http://localhost:3000
```

## Environment variables

None required. Planora runs entirely client-side.

## Updating the content database

Two paths:

1. **Live, no-redeploy** — Open the deployed app, click **⟳ Reload from Excel**, choose the latest `PROPVR_Content_Plan_DB.xlsx` from your machine. Data reloads for your session; Lead Gen + KPI sheets are reparsed.
2. **Committed update** — Drop the new `PROPVR_Content_Plan_DB.xlsx` into `public/` and regenerate `index.html` from `build_v12.py`. Redeploy with `vercel --prod` or push to git.

## Custom domain

In the Vercel dashboard: **Project → Settings → Domains** → add (e.g., `planora.propvr.com`).
Update the CNAME at your DNS provider to `cname.vercel-dns.com`.

## Protecting access

Planora contains internal campaign data. Do one of:

- Turn on **Vercel Password Protection** (Project Settings → Deployment Protection → Password).
- Put it behind **Vercel Authentication** (requires Teams plan).
- Keep the repo private, deploy to a Vercel team, and share previews only with logged-in members.

## Notes persistence

Team notes (the "Add note" button on every post) are stored in the browser's `localStorage` under keys `planora_v12_notes`, `planora_v12_leadgen`, `planora_v12_kpi`. They are **per-browser, per-domain**. Users can click **⇩ Export notes** in the top-right data bar to download a JSON backup any time.

If the team wants shared notes across users, the next step is to swap localStorage for a serverless KV store (Vercel KV / Upstash Redis) — reach out to add that.

## Version history

- **v0.1** (Apr 16, 2026) — First Vercel-deployable cut. 363 posts · 26 weeks · 6 months · UAE/Saudi/India. 5-sheet Excel as live DB. No AI generation — notes-only workflow.
