# Set Landing Page — Implementation Plan

## Design Analysis

### Design Language (from app screenshots + assets)
- **Palette**: Near-white background (`#F5F5F5`/`#FAFAFA`), charcoal text (`#3C3C3C`), light gray cards/surfaces, subtle green accent (status bar charging icon hints at iOS system green)
- **Typography**: Clean sans-serif, bold large numbers for data, lighter weight for labels. The splash uses a confident serif-ish wordmark for "Set." with the barbell plate as the period.
- **Shape language**: Rounded corners (pill buttons, rounded cards), soft shadows, generous whitespace
- **Tone**: "Just log the work. Built for numbers, not likes." — direct, no-fluff, anti-social-media positioning
- **Icon motifs**: Barbell/dumbbell icon in nav, camera scan button, percentage badge

### Key Brand Elements to Carry to Web
- The "Set." wordmark with barbell-plate period (from `logo.png`)
- The taglines from `splash.png`: "Just log the work." / "Built for numbers, not likes."
- Light, airy, premium-minimal feel — no gradients, no loud colors
- iPhone device frame showcasing the 4 screenshots

---

## Site Architecture

```
/                → Landing page (home + marketing)
/privacy         → Privacy Policy
/support         → Support / Contact
/terms           → Terms of Use
```

All pages share a common header/footer. Single static site, no framework dependencies.

---

## Page-by-Page Plan

### 1. `/` — Landing Page

**Sections (top to bottom):**

1. **Hero**
   - "Set." logo (from `logo.png`) centered or left-aligned
   - Headline: "Just log the work."
   - Subline: "Built for numbers, not likes."
   - Single CTA button: "Download on the App Store" (placeholder link until live)
   - Subtle down-scroll indicator

2. **Feature Showcase — Phone Mockups**
   - Horizontal scroll or staggered grid of 3–4 iPhone frames containing the screenshots:
     - **Lifts dashboard** (IMG_7365) — "Track your PRs at a glance"
     - **Natural language input** (IMG_7366) — "Log sets in plain English"
     - **OCR session calculator** (IMG_7367) — "Snap a whiteboard, get your weights"
     - **Session % result** (IMG_7368) — "Instant percentage breakdowns"
   - Each screenshot in a minimal iPhone 15 device frame (CSS-only, no image dependency)
   - Short caption beneath each

3. **Value Props — Three Pillars**
   - Three-column grid (stacks on mobile):
     - **Fast Capture** — "Type it, say it, or photograph it. Natural language, voice, and OCR input."
     - **Lift Intelligence** — "Auto-estimated 1RM, rep maxes, trend charts, and percentage tables."
     - **Privacy-First** — "All data stays on your device. Optional iCloud sync. No accounts, no tracking."

4. **How It Works — Simple Steps**
   - Three-step visual flow:
     1. "Type or speak your sets" (icon: keyboard/mic)
     2. "Set parses and structures the data" (icon: barbell)
     3. "See your progression over time" (icon: chart-up)

5. **Closing CTA**
   - Repeat the App Store download button
   - "Set is free during beta. No ads, no tracking, no noise."

6. **Footer**
   - Links: Privacy Policy | Support | Terms of Use
   - "© 2026 Set"
   - Small "Made for lifters" tagline

### 2. `/privacy` — Privacy Policy

- **Last updated**: February 2026
- Sections covering:
  - Local-first storage (SwiftData on device)
  - Optional iCloud/CloudKit sync (user-initiated, same Apple ID only)
  - Permissions used: Camera, Photo Library, Microphone, Speech Recognition — and why
  - No analytics, no tracking, no ads, no third-party SDKs
  - No account creation required
  - Data deletion: full local reset available in-app
  - Contact email for privacy requests

### 3. `/support` — Support

- Contact email (prominent)
- Expected response time
- Basic troubleshooting:
  - "My sets aren't parsing correctly" → tips on formatting
  - "iCloud sync isn't working" → check iCloud settings
  - "How do I reset my data?" → Settings > Reset
- Link back to home

### 4. `/terms` — Terms of Use

- Standard terms for a free iOS app
- No warranties, limitation of liability
- Acceptable use
- Reference to Apple's EULA where applicable

---

## Technical Stack

### Build
- **Plain HTML + CSS + minimal vanilla JS** (no framework, no build step)
- One CSS file with custom properties for the design tokens
- Responsive: mobile-first, breakpoints at 768px and 1024px
- CSS-only iPhone device frames for screenshots
- Smooth scroll, intersection observer for fade-in animations (vanilla JS)
- System font stack: `-apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", sans-serif`

### File Structure
```
set-web/
├── index.html
├── privacy.html
├── support.html
├── terms.html
├── css/
│   └── style.css
├── js/
│   └── main.js          (scroll animations, mobile nav)
├── assets/
│   ├── logo.png
│   ├── splash.png
│   ├── favicon.ico       (to generate from logo)
│   ├── og-image.png      (to generate for social sharing)
│   └── screenshots/
│       ├── IMG_7365.PNG
│       ├── IMG_7366.PNG
│       ├── IMG_7367.PNG
│       └── IMG_7368.PNG
├── plan/
│   ├── business.md
│   ├── website-plan.md
│   └── implementation.md (this file)
└── README.md             (only if needed for deploy)
```

### SEO & Meta
- `<title>`: "Set — Minimalist Strength Training Log"
- `<meta name="description">`: "Log your lifts fast. Track 1RM progression. No noise, no social, no tracking. Just the work."
- Open Graph tags with `og-image.png` (to be generated)
- `favicon.ico` derived from logo
- Canonical URLs for each page

---

## Design Tokens (CSS Custom Properties)

```css
:root {
  --color-bg:        #FAFAFA;
  --color-surface:   #F0F0F0;
  --color-text:      #2C2C2C;
  --color-text-muted:#8A8A8A;
  --color-border:    #E5E5E5;
  --color-accent:    #3C3C3C;    /* charcoal — matches logo */
  --radius-sm:       8px;
  --radius-md:       16px;
  --radius-lg:       24px;
  --radius-pill:     999px;
  --shadow-card:     0 2px 12px rgba(0,0,0,0.06);
  --font-family:     -apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", Roboto, sans-serif;
  --font-size-hero:  clamp(2.5rem, 6vw, 4.5rem);
  --font-size-h2:    clamp(1.75rem, 4vw, 2.5rem);
  --font-size-body:  1.125rem;
  --max-width:       1120px;
}
```

---

## Build Sequence

### Step 1: Scaffold & Global Styles
- Create `index.html` with semantic HTML structure, meta tags, OG tags
- Create `css/style.css` with reset, custom properties, typography, layout utilities
- Create shared header (logo + nav) and footer as HTML partials repeated in each page

### Step 2: Landing Page Hero
- Build hero section with logo, headline, subline, CTA button
- Style the App Store button (dark pill matching the charcoal accent)

### Step 3: Screenshot Showcase
- Build CSS-only iPhone device frames
- Place the 4 screenshots inside with captions
- Responsive layout: horizontal scroll on mobile, grid on desktop

### Step 4: Feature Sections
- Three-column value props with simple SVG icons (inline)
- "How it works" step flow

### Step 5: Secondary Pages
- `/privacy.html` — structured legal content
- `/support.html` — contact + FAQ
- `/terms.html` — standard terms

### Step 6: Animations & Polish
- `js/main.js` — IntersectionObserver fade-in on scroll
- Smooth scroll for anchor links
- Mobile hamburger nav if needed (likely not — only 3 links)

### Step 7: Assets & SEO
- Generate `favicon.ico` from logo
- Generate `og-image.png` (1200x630) — logo + tagline on light bg
- Validate all meta tags

### Step 8: Deploy Prep
- Test all pages at mobile (375px), tablet (768px), desktop (1280px)
- Validate HTML
- Verify all internal links work
- Ready for Cloudflare Pages or GitHub Pages deployment

---

## Acceptance Criteria (from website-plan.md)

- [ ] All pages are public and load without login
- [ ] Mobile and desktop layout is clean
- [ ] Links are valid and not broken
- [ ] Privacy text matches actual app behavior
- [ ] URLs are ready to paste into App Store Connect / TestFlight
- [ ] `/privacy` directly accessible
- [ ] `/support` directly accessible
