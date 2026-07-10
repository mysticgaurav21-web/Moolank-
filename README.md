# Moolank Guru ✨

A premium, mobile-first Vedic numerology web app. Enter a date of birth, get a complete Moolank (Birth Number) report — personality, career, love, money, lucky factors, remedies and more. Compare any two numbers, save reports, share, print or download as PDF.

Built with **React + TypeScript + Tailwind CSS + Vite**, animated with **Framer Motion**, icons by **Lucide**.

## Run locally

```bash
npm install
npm run dev
```

Open the URL Vite prints (usually http://localhost:5173).

## Build for production

```bash
npm run build      # output in dist/
npm run preview    # test the production build locally
```

## Deploy

The `dist/` folder is fully static — deploy it to **Netlify**, **Vercel**, **GitHub Pages** or any static host.

> **Note for GitHub Pages / sub-path hosting:** set `base: '/your-repo-name/'` in `vite.config.ts` and consider switching `BrowserRouter` to `HashRouter` in `src/main.tsx` so deep links work without server rewrites. On Netlify, instead add a `_redirects` file with `/* /index.html 200`.

## Features

- **Instant Moolank calculation** — birth day reduced to a single digit (28 → 2+8 = 10 → 1)
- **Full report** — 35+ sections per number: overview, personality, traits, leadership/thinking/communication styles, career, business, money, love, marriage, family, health, spirituality, all lucky factors, affirmation, habits, remedies
- **Explore** — browse/search all 9 numbers
- **Compare** — any two numbers: star score, relationship, business, friendship, strengths, challenges (45 unique pairs, order-independent)
- **Favorites** — bookmark reports (localStorage)
- **Share / Print / PDF** — Web Share API with clipboard fallback; PDF via the browser print dialog ("Save as PDF") with dedicated print styles
- **Settings** — dark/light theme, three font sizes (persisted)
- **SEO** — meta tags, Open Graph, Twitter card, JSON-LD structured data
- **Accessible** — keyboard navigable, ARIA labels, visible focus states, reduced-motion support

## Architecture

```
src/
  data/            All content lives here — zero hardcoded text in components
    moolank.json        Complete knowledge base for numbers 1–9
    compatibility.json  All 45 pair combinations
    ui.json             Every UI string (easy to translate to Hindi later)
  types.ts         Shared TypeScript interfaces
  utils/           calc.ts (pure calculation + data access), share.ts
  hooks/           useSettings (theme/font), useFavorites (bookmarks)
  components/      Reusable UI: GlassCard, SectionBlock, ChipList, BigNumber,
                   LuckyGrid, Nav, Footer, ActionBar, SettingsDrawer, Logo
  pages/           Home, Result, Search, Compare, Favorites
```

### Ready for future modules

The data-driven design means new modules plug in cleanly:

- **Bhagyank / Personal Year** — add a util in `calc.ts` + a JSON file + a route
- **Name Numerology / Business Name Analysis** — new letter-value util + JSON
- **AI Guru / Daily Prediction** — add an API layer beside `utils/`; the report UI (SectionBlock, GlassCard) is already generic
- **Hindi edition** — translate the three JSON files, nothing else changes
- **Premium membership** — gate routes in `App.tsx`

## Content note

All report content ships in structured JSON — no AI calls, no network requests at runtime, so the app is extremely fast and works offline once loaded.
