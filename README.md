# MYWARD — Digital Ward Management Platform

A bilingual (English / Malayalam) Progressive Web App for Panchayat Ward Management, connecting citizens with their elected ward member.

![MYWARD](public/icon.svg)

## ✨ Features

- **23 module screens** — 11 citizen modules + 12 ward member admin modules
- **Bilingual** — full English + Malayalam (മലയാളം) support with instant language toggle
- **Dark / Light theme** — auto-adapting design system
- **PWA** — installable on phone home screens, offline-capable, app icons
- **Mobile-first** — designed like a native mobile app, rendered in a phone frame on desktop

## 👤 Citizen App (11 modules)

Home Dashboard · Ward Updates · Report an Issue · Citizen Services · Government Schemes · Local Directory · Volunteer Network · Events & Programs · My Ward · Notifications · My Profile

## 🧑‍💼 Ward Member App (12 modules)

Dashboard · Resident Management · Ward Updates Mgmt · Issue Management · Citizen Assistance · Scheme Management · Directory Mgmt · Volunteer Mgmt · Events Management · Notifications (Broadcast) · Reports · My Profile

## 🚀 Quick Start

```bash
# Install dependencies
bun install

# Start dev server
bun run dev

# Open http://localhost:3000
```

## 📦 Deployment

See **[DEPLOYMENT.md](./DEPLOYMENT.md)** for step-by-step Vercel deployment + custom domain setup.

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Next.js 16 (App Router) |
| Language | TypeScript 5 |
| Styling | Tailwind CSS 4 + shadcn/ui |
| State | Zustand |
| Animations | Framer Motion |
| Icons | Lucide React |
| PWA | Web Manifest + Service Worker |

## 📁 Project Structure

```
src/
  app/           # Layout, page entry, global styles
  lib/myward/    # Store, i18n, types, mock data
  components/myward/
    phone-frame/   # Mobile frame + toggles
    shared/        # Reusable UI (header, nav, cards)
    citizen/       # 11 citizen screens
    ward-member/   # 12 admin screens
    pwa/           # SW registration + install prompt
public/          # Manifest, service worker, icons
```

## 📄 License

This project is built for panchayat e-governance. Free to deploy and adapt.

---

Built with ❤️ for transparent, connected panchayats.
