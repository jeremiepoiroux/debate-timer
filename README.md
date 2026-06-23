# Debate Timer

Moderate live discussions with real-time speaking time tracking, agenda segments, and a note teleprompter. No dependencies, no build step, no server — one HTML file.

## Features

- **Speaking time tracker** — tap a participant card to start/stop tracking their speaking time; pause and resume at any time
- **Balance warnings** — visual indicators when a speaker has talked too much (⬆ A lot) or too little (⬇ Little) relative to the group average
- **Max speaking time** — optional per-session cap; shows a red ⏱ Max badge when a speaker exceeds it
- **Moderator role** — mark any participant as moderator (excluded from balance warnings); appears in the same grid as other speakers
- **Segments** — split the session into named phases (e.g. "Open Q&A", "Closing remarks") with individual countdowns
- **Teleprompter** — write structured notes in Markdown (`## Section title` + bullets); navigate section by section with progress tracking
- **Pause & resume** — step back to the setup screen without losing accumulated times; resume exactly where you left off
- **Offline-ready PWA** — installs on Android and iPhone, works without internet after first load
- **Wake Lock** — screen stays on during a session (Chrome / Android)

## Teleprompter note format

Write notes using Markdown headings followed by bullet points:

```markdown
## Introduction
- Participant introductions
- Context and objectives

## Main discussion
- Opening question: …
- Follow-up angles

## Wrap-up
- Key takeaways
- Next steps
```

Each section becomes a slide in the teleprompter. Navigate with ← Prev / Next →.

## Deployment

### Option 1 — Open locally (zero setup)

Download `index.html` and open it in any browser. No server, no install. Data is saved in the browser's local storage.

### Option 2 — GitHub Pages (recommended)

1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch**, select `main`, folder `/` (root)
4. Save — your app is live at `https://your-username.github.io/debate-timer/`

HTTPS is provided automatically, which is required for the PWA and offline support.

### Option 3 — Any static host

Upload `index.html`, `manifest.json`, `sw.js`, and `icon.svg` to any host that serves static files over HTTPS (Netlify, Vercel, Cloudflare Pages, etc.).

## Install as a PWA

### Android (Chrome)

1. Open the app URL in Chrome
2. Tap **⋮ → Add to Home screen** (or accept the install banner)
3. The app installs and runs fullscreen — no browser bar

### iPhone (Safari)

1. Open the app URL in Safari
2. Tap the **Share** button (box with arrow at the bottom)
3. Tap **Add to Home Screen** and confirm

## Data & privacy

All data stays on your device — nothing is sent to any server. Sessions are stored in the browser's `localStorage`, scoped to the PWA origin. Data persists across sessions and app updates.

## License

MIT
