# Set Business Features

## Product Positioning
Set is a minimalist strength-training log app focused on fast capture and clear progression.  
Core promise: **log real training data quickly, then turn it into useful strength insights**.

## Target Users
- Lifters who want fast logging without social or content noise.
- Athletes and coaches tracking key lifts and progression trends.
- Users moving from notes apps/spreadsheets to structured training data.

## Core Value Proposition
- Input is flexible (natural language, voice, photo OCR) but output is structured.
- Progress is measured through practical strength metrics (1RM, estimated rep maxes, trends).
- Privacy-first architecture keeps data private, responsive, and simple:
  all data is stored locally on device first, with optional iCloud sync/backup via CloudKit when enabled.

## Current Feature Pillars

### 1. Fast Workout Capture
- Natural-language parsing (`"BS 5x3 @ 100kg"`, `"deadlift 1 rep 180 kg"`).
- Voice dictation input.
- OCR import from camera or photo library.
- Parse confidence and validation states for safe review before save.
- Editable parse preview for correction before save.

### 2. Lift Intelligence
- Movement aliases and custom movement support.
- Movement scope is intentionally lifting-focused (plus core gymnastics movements such as pull-up, chin-up, dip, muscle-up).
- Auto-estimated 1RM from recent qualifying sets.
- Manual 1RM override and provenance display.
- Estimated 2RM–5RM outputs.
- Estimated %age from 50% to 90% of 1RM.
- 1RM trend chart for progression visibility.
- **Session % calculator** from whiteboard/photos:
  detect percentage blocks from camera or photo library, match movement,
  compute target weights from the user’s current 1RM, and show a clear
  "today session" result with `Set 1`, `Set 2`, etc. and the exact 1RM values used.
- Session % results are intentionally ephemeral today (computed and displayed, not persisted as logged sets).

### 3. Session & History Management
- Log list grouped by date.
- Session detail with editable notes and date context.
- Movement detail with recent sets and % target table.
- Delete workflows for movement organization.

### 4. Data Portability & Control
- Local-first storage with optional CloudKit sync across user devices.
- Markdown export for max lifts (share sheet flow).
- Text import for existing 1RM values.
- Import history for recent 1RM imports (with success/failure summary).
- Full local reset for test/device cleanup.

### 5. UX & Platform Foundation
- Premium-minimal visual style across tabs.
- 4-screen onboarding flow (logging, progression, `%` session from photo, philosophy).
- i18n foundation with English and French localization.
- Appearance mode control: `System`, `Dark`, or `White`.
- iOS-first architecture using SwiftUI + SwiftData.

## Near-Term Business Priorities
- Reduce parsing failure/ambiguity rate for real-world phrasing.
- Improve onboarding activation and first-session completion.
- Validate CloudKit behavior end-to-end on two physical devices (same Apple ID) and document operational expectations.
