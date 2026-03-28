# CLADS 2026 — Landing Page

XXIV Congreso Latinoamericano de Dinámica de Sistemas  
Built with **Astro** + **Tailwind CSS**

---

## Quick Start

```bash
# Install dependencies
npm install

# Start development server (http://localhost:4321)
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## Project Structure

```
clads2026/
├── public/
│   └── favicon.svg
├── src/
│   ├── components/
│   │   ├── Navbar.astro       # Top navigation bar
│   │   ├── Hero.astro         # Hero/landing section
│   │   ├── About.astro        # About + objectives
│   │   ├── Agenda.astro       # 3-day event schedule
│   │   ├── Topics.astro       # Thematic areas + submission types
│   │   ├── Timeline.astro     # Key dates & milestones
│   │   ├── Venue.astro        # Location & institutions
│   │   ├── CTA.astro          # Registration call-to-action
│   │   └── Footer.astro       # Footer + contact
│   ├── layouts/
│   │   └── Layout.astro       # Base HTML layout with SEO
│   ├── pages/
│   │   └── index.astro        # Main page (assembles all components)
│   └── styles/
│       └── global.css         # Global styles, animations, utilities
├── astro.config.mjs
├── tailwind.config.mjs
├── vercel.json
└── package.json
```

---

## Image Replacement Guide

Search for `<!-- REPLACE:` comments throughout the component files to find all placeholder images.

| File | What to Replace |
|------|----------------|
| `About.astro` | Congress/event photo (line ~55) |
| `Venue.astro` | Universidad Andrés Bello campus photo (line ~18) |
| `Venue.astro` | Santiago de Chile cityscape (line ~40) |
| `Venue.astro` | Institution logos (search for `REPLACE: Replace this div`) |

All images currently use Unsplash placeholders. Replace the `src` attributes with your actual images placed in `/public/images/`.

---

## Deploy to Vercel

1. Push to GitHub
2. Import repository on [vercel.com](https://vercel.com)
3. Vercel auto-detects Astro — no additional config needed
4. `vercel.json` is already configured

Or via CLI:
```bash
npm i -g vercel
vercel
```

---

## Customization

- **Colors**: Edit `tailwind.config.mjs` → `theme.extend.colors.brand`
- **Fonts**: Edit `src/styles/global.css` → `@import url(...)` and font-family variables
- **Content**: Each section is a standalone component in `src/components/`
- **SEO**: Edit metadata in `src/layouts/Layout.astro`

---

## Tech Stack

- [Astro](https://astro.build) v4
- [Tailwind CSS](https://tailwindcss.com) v3
- Google Fonts: Syne (display) + DM Sans (body) + JetBrains Mono (code)
- Vanilla JS for scroll animations & mobile menu
