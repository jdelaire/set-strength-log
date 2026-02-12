# Set Website Plan

## Goal
Ship a minimal public website for **Set** with valid HTTPS links for App Store Connect and TestFlight:
- Privacy Policy URL
- Support URL
- Optional Marketing URL

## Scope (MVP)
1. `/` Home page
2. `/privacy` Privacy Policy
3. `/support` Support page
4. `/terms` Terms of Use (optional, recommended)

## Phase 1: Content
1. Draft a short app summary: "Set is a minimalist lifting log."
2. Privacy policy must cover:
   - Local-first storage
   - Optional iCloud/CloudKit sync
   - Permissions: camera, photo library, microphone, speech recognition
   - Whether analytics/tracking/ads are used
   - Contact email for privacy requests
3. Support page must include:
   - Contact email
   - Expected response time
   - Basic troubleshooting guidance
4. Add "Last updated" date and app version reference.

## Phase 2: Build
1. Use a static stack (plain HTML/CSS or static framework).
2. Match the app style: clean, minimalist, readable.
3. Ensure responsive layout for mobile and desktop.
4. Add basic SEO/social metadata (`title`, description, Open Graph).
5. Add favicon/app icon.

## Phase 3: Deploy
1. Deploy on Cloudflare Pages or GitHub Pages.
2. Use HTTPS (required).
3. Optionally attach a custom domain.
4. Verify direct URL access:
   - `https://<domain>/privacy`
   - `https://<domain>/support`

## Phase 4: App Store Connect
1. Set Privacy Policy URL to `/privacy`.
2. Set Support URL to `/support`.
3. Set Marketing URL to `/` (optional but useful).

## Acceptance Checklist
1. All pages are public and load without login.
2. Mobile and desktop layout is clean.
3. Links are valid and not broken.
4. Privacy text matches actual app behavior.
5. URLs are ready to paste into App Store Connect/TestFlight.

