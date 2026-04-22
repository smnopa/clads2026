# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start dev server
npm run build     # Build to dist/
npm run preview   # Preview built output locally
```

## Architecture

Single-page static site built with **Astro 4** + **Tailwind CSS 3**, deployed on Vercel.

The site has one page (`src/pages/index.astro`) that composes section components in order: `Navbar → Hero → About → Agenda → Topics → Timeline → Venue → CTA → Footer`.

**Layout** (`src/layouts/Layout.astro`) handles:
- `<head>` with SEO/OG meta tags (site: `https://clads2026.com`, lang: `es`)
- Global IntersectionObserver that triggers `.reveal` animations when elements enter the viewport
- Navbar scroll effect: adds `.scrolled` class to `#navbar` after 50px scroll (frosted glass style)
- Mobile menu toggle (`#mobile-menu-btn` / `#mobile-menu`)

**Components** (`src/components/`) are each a self-contained section with its own inline styles where needed. No JS framework — all interactivity is vanilla JS inside `<script>` tags in Layout.

## Design system

Brand palette (defined in both `tailwind.config.mjs` and `src/styles/global.css`):
- `brand-blue` / `--brand-blue-mid`: `#2563EB`
- `brand-blue-light` / `--brand-blue-light`: `#5BA3F5`
- `brand-blue-dark` / `--brand-blue-dark`: `#0F2852`
- `brand-ink` / `--ink`: `#0F172A`

All font families (sans, display, body, mono) map to **Montserrat**. Tailwind's default font stacks are fully replaced.
- `.font-display` = Montserrat Black Italic (weight 900, italic) — used for primary headings
- `.font-mono` = Montserrat Medium with wide tracking — used for labels/codes

Custom CSS utility classes in `src/styles/global.css` (use these instead of composing raw Tailwind):
- `.glass` — frosted glass card (white/85%, blur, subtle border)
- `.glass-hover` — adds lift + border highlight on hover
- `.btn-primary` / `.btn-outline` — brand CTA buttons (uppercase italic, fixed padding)
- `.section-label` — small all-caps gradient label above section titles
- `.gradient-text` / `.gradient-text-blue` — blue gradient text fill
- `.reveal` — scroll-reveal base (opacity 0 → 1, translateY 30px → 0); add `.reveal-delay-{1-5}` for stagger
- `.orb` — blurred decorative circle (absolute positioned, pointer-events none)
- `.hero-grid` — subtle grid background pattern for the hero section
- `.count-badge` — large Black Italic gradient number (used in stat cards)
- `.border-glow-anim` — pulsing blue border animation

Custom Tailwind animations (defined in `tailwind.config.mjs`): `animate-fade-up`, `animate-fade-in`, `animate-float`, `animate-pulse-slow`, `animate-spin-slow`, `animate-marquee`, `animate-glow`.
