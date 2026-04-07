# Planora — Vercel Deployment Guide

## Option 1: Deploy via Vercel Dashboard (Easiest)

1. Go to **https://vercel.com** and sign in (or create a free account)
2. Click **"Add New…" → "Project"**
3. Choose **"Upload"** and drag-and-drop the entire `planora-vercel` folder
4. Vercel will auto-detect the config — just click **"Deploy"**
5. Your site will be live at a `.vercel.app` URL within seconds

## Option 2: Deploy via Vercel CLI

### First-time setup
```bash
npm install -g vercel
vercel login
```

### Deploy
```bash
cd planora-vercel
vercel
```

Follow the prompts — Vercel will read the `vercel.json` config automatically.

### Deploy to production
```bash
vercel --prod
```

## Option 3: Connect a Git Repository

1. Push this `planora-vercel` folder to a GitHub/GitLab/Bitbucket repo
2. In the Vercel dashboard, click **"Add New… → Project"**
3. Import the repository
4. Vercel auto-deploys on every push to `main`

## Custom Domain

After deploying, you can add a custom domain:
1. Go to your project in the Vercel dashboard
2. Click **Settings → Domains**
3. Add your domain (e.g., `planora.propvr.com`)
4. Update your DNS records as instructed

## Project Structure

```
planora-vercel/
├── public/
│   └── index.html    ← Your Planora app
├── package.json
├── vercel.json       ← Vercel routing & headers config
└── DEPLOY.md         ← This file
```
