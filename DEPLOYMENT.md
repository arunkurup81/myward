# MYWARD — Deployment Guide

A bilingual (English/Malayalam) PWA for Panchayat Ward Management.
Built with Next.js 16, TypeScript, Tailwind CSS 4, and shadcn/ui.

---

## Prerequisites

1. A **GitHub account** (free)
2. A **Vercel account** (free — sign up at vercel.com with your GitHub account)
3. **Git** installed on your computer (download from git-scm.com)
4. *(Optional)* A custom domain (e.g., `myward.in`) from any registrar (GoDaddy, Namecheap, etc.)

---

## Step 1: Prepare the code locally

1. **Unzip** the project folder you downloaded.
2. Open a terminal in the project folder.
3. Initialize git and make the initial commit:

```bash
git init
git add -A
git commit -m "MYWARD — Digital Ward Management Platform (PWA + bilingual)"
```

---

## Step 2: Push to GitHub

1. Go to **github.com** → click **"+"** → **"New repository"**
2. Name it `myward` (or any name)
3. Set it to **Private** (recommended) or Public
4. **Don't** add a README/license/.gitignore (already included)
5. Click **"Create repository"**
6. Copy the commands GitHub shows you (they look like this):

```bash
git remote add origin https://github.com/YOUR_USERNAME/myward.git
git branch -M main
git push -u origin main
```

7. Run those commands in your terminal. Your code is now on GitHub.

---

## Step 3: Deploy to Vercel

1. Go to **vercel.com** → click **"Log In"** → sign in with **GitHub**
2. Click **"Add New..."** → **"Project"**
3. You'll see your GitHub repos — find `myward` → click **"Import"**
4. Vercel auto-detects Next.js. **Don't change any settings** — they're already correct:
   - Framework Preset: Next.js
   - Build Command: `next build`
   - Output Directory: `.next`
   - Install Command: `bun install`
5. Click **"Deploy"**
6. Wait ~2 minutes. Vercel builds and deploys.
7. You'll get a live URL like: **`myward.vercel.app`** 🎉

---

## Step 4: Verify the PWA

Open your deployment URL on a **phone** (Chrome on Android or Safari on iOS):

1. The MYWARD login screen should load
2. Tap the **share** button → **"Add to Home Screen"** (iOS) or Chrome will show an **"Install"** prompt (Android)
3. The app icon appears on your home screen
4. Launch it — it opens fullscreen like a native app
5. Toggle language with **EN/മല** (bottom-left) and theme with **sun/moon** (bottom-right)

---

## Step 5 (Optional): Add a custom domain

### In Vercel:
1. Go to your project → **Settings** → **Domains**
2. Enter your domain (e.g., `myward.in`) → click **"Add"**
3. Vercel shows you DNS records to add

### At your domain registrar (GoDaddy, Namecheap, etc.):
4. Go to **DNS management** for your domain
5. Add the records Vercel shows you. Typically:

| Type | Name | Value |
|------|------|-------|
| A | `@` | `76.76.21.21` |
| CNAME | `www` | `cname.vercel-dns.com` |

6. Wait 5–30 minutes for DNS to propagate
7. Vercel automatically provisions a **free SSL certificate**
8. Your app is now live at `https://your-domain.com`

---

## What's included

### Features
- ✅ **23 module screens** (11 citizen + 12 ward member)
- ✅ **Bilingual** English / Malayalam (toggle bottom-left)
- ✅ **Dark/Light theme** (toggle bottom-right)
- ✅ **PWA** — installable, offline-capable, app icons
- ✅ **Mobile-first** responsive design

### Tech stack
- **Framework**: Next.js 16 (App Router)
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4 + shadcn/ui
- **State**: Zustand
- **Animations**: Framer Motion
- **Icons**: Lucide React

### Project structure
```
src/
  app/
    layout.tsx          # Root layout (PWA meta, SW registration)
    page.tsx             # Entry → AppShell
    globals.css          # Design system + dark theme
  lib/myward/
    store.ts             # Zustand (role, screen, theme, language)
    i18n.ts              # 250+ EN/ML translations + useT() hook
    types.ts             # TypeScript types
    mock-data.ts         # All mock data
  components/myward/
    phone-frame.tsx      # Mobile frame + theme/lang toggles
    app-shell.tsx        # Router (login → citizen/ward-member)
    login-screen.tsx     # Login & role selection
    shared/              # ScreenHeader, BottomNav, UI primitives
    citizen/             # 11 citizen module screens
    ward-member/         # 12 ward member module screens
    pwa/                 # Service worker registration + install prompt
public/
  manifest.webmanifest   # PWA manifest
  sw.js                  # Service worker (offline caching)
  icon.svg               # App icon
  icon-maskable.svg      # Maskable icon (Android)
vercel.json              # Vercel deployment config
.env.example             # Template for backend env vars
```

---

## Troubleshooting

### Build fails on Vercel
- Check the build logs in Vercel → your project → **"Deployments"** → click the failed build
- Common fix: delete `bun.lock` and let Vercel use `npm install` instead (change Install Command to `npm install` in Project Settings)

### PWA install prompt doesn't show
- Make sure you're on **HTTPS** (Vercel provides this automatically)
- Chrome requires a **valid manifest** + **service worker** + **HTTPS** — all included
- iOS Safari: tap Share → "Add to Home Screen" manually (no auto-prompt on iOS)

### Language toggle doesn't persist
- Check browser settings → make sure localStorage isn't blocked

### Custom domain not working
- DNS propagation can take up to 24 hours (usually 5–30 min)
- Verify DNS at dnschecker.org → search for your domain

---

## Next steps (Phase 2)

This is the **UI/UX prototype** (Phase 1). For a real trial run, add:

1. **Backend** — Prisma + Postgres, API routes for all modules
2. **Authentication** — NextAuth.js with role-based access (citizen/wardMember)
3. **Image upload** — for issue reporting photos (S3 / Cloudinary)
4. **Push notifications** — for emergency alerts (Web Push API)
5. **Real data** — replace mock-data.ts with database queries

See `.env.example` for the environment variables you'll need.

---

## Support

If anything goes wrong during deployment, check:
1. The build logs in Vercel
2. The browser console (F12) for runtime errors
3. Lighthouse audit (Chrome → Inspect → Lighthouse) for PWA validation
