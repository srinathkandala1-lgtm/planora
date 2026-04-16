# Planora v0.1

PROPVR Marketing Automation Hub · 6-Month Spatial Ecosystem Campaign (Apr 20 – Oct 18, 2026).

Static single-page app. Everything client-side. Notes persist in the browser. Ship it to Vercel.

## Quick deploy

```bash
npm i -g vercel
vercel --prod
```

See [DEPLOY.md](./DEPLOY.md) for the full guide.

## What's inside

- `public/index.html` — the complete Planora app (Dashboard, Content Calendar with Pre-Launch + Launch Campaign Month 1, LinkedIn, X, Instagram, Facebook, Blogs, Newsletters, Keywords, Hashtags, Lead Gen, KPI Tracker)
- `public/PROPVR_Content_Plan_DB.xlsx` — the live 5-sheet content database. Editable in Excel; reload in Planora via the **⟳ Reload from Excel** button in the top bar.
- `vercel.json` — Vercel routing + security headers
- `package.json` — project metadata
- `DEPLOY.md` — deployment guide

## Features

- 363 posts across 26 weeks, organized by platform and phase
- 4 pre-launch teasers (Apr 16–19) + 30 daily LinkedIn posts during the launch campaign (Apr 20 – May 19)
- Full Strategy Overview on Dashboard (journey arc, priority product order, special posts, format emphasis, promo rules, scope notes, Month 1 Launch Campaign)
- Per-post **Add Note** button — team members write and post content themselves, no AI captions
- Lead Gen Tracker (W19–W26) and KPI Tracker with inline editing
- Keywords filtered for UAE / Saudi Arabia / India
- Hashtag reference library organized by group
- SheetJS-powered live reload — edits to the Excel DB flow into Planora without a rebuild

## License

Internal to PROPVR. Not for public distribution.
