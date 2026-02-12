# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Marketing website for **Set**, a minimalist iOS strength-training log app. Static site with no build step — plain HTML, CSS, and vanilla JS.

## Local Development

```bash
# Serve locally (from project root)
python3 -m http.server 8080
# Then open http://localhost:8080
```

No build tools, no dependencies, no package.json. Just open `index.html` directly or use any static file server.

## Architecture

- **4 HTML pages**: `index.html` (landing), `privacy.html`, `support.html`, `terms.html`
- **1 CSS file**: `css/style.css` — design system with CSS custom properties in `:root`
- **1 JS file**: `js/main.js` — header scroll effect + IntersectionObserver scroll reveals
- **Assets**: `assets/logo.png`, `assets/splash.png`, `assets/screenshots/IMG_7365-7368.PNG`

Each HTML page repeats the header and footer (no templating). Changes to nav/footer must be replicated across all 4 files.

## Design System

All design tokens are CSS custom properties in `css/style.css` under `:root`. Key conventions:
- Fonts: `DM Serif Display` (headlines h1/h2), `Outfit` (everything else) — loaded from Google Fonts via `<link>` in each HTML file
- Colors: near-white bg (`#FAFAFA`), charcoal text (`#1A1A1A`), muted (`#999999`)
- Phone mockups: CSS-only iPhone frames (`.phone-frame`) with dynamic island pseudo-element
- Animations: `.reveal` class + `.reveal-delay-{1-4}` for staggered scroll-triggered fade-ups
- Content pages use `.site-header--solid` (always-visible header bg) vs landing page's scroll-triggered `.scrolled` class

## Deployment

Intended for Cloudflare Pages or GitHub Pages. Nav links use clean URLs (`/privacy` not `/privacy.html`) — Cloudflare Pages resolves these automatically; GitHub Pages needs directory-based structure.

## Planning Docs

`plan/` contains product context:
- `business.md` — app features, target users, value proposition
- `website-plan.md` — site goals and acceptance checklist
- `implementation.md` — detailed build plan and design decisions

## Placeholders to Update

- Contact email `support@setapp.io` appears in privacy.html, support.html, terms.html
- App Store download button links to `#` (update when app is live)
- OG image uses `assets/splash.png` (generate a proper 1200x630 og-image)
