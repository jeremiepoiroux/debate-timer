# Debate Timer

Moderate live discussions with real-time speaking time tracking, agenda segments, and a note teleprompter — all from a single HTML file with optional server persistence.

## Features

- **Speaking time tracker** — tap a participant card to start/stop tracking their speaking time; pause and resume at any time
- **Balance warnings** — visual indicators when a speaker has talked too much (⬆ A lot) or too little (⬇ Little) relative to the group average
- **Max speaking time** — optional per-session cap; shows a red ⏱ Max badge when a speaker exceeds it
- **Moderator role** — mark any participant as moderator (excluded from balance warnings); they appear in the same grid as other speakers
- **Segments** — split the session into named phases (e.g. "Open Q&A", "Closing remarks") with individual countdowns
- **Teleprompter** — write structured notes in Markdown (`## Section title` + bullets); navigate section by section with progress tracking
- **Pause & resume** — step back to the setup screen without losing accumulated times; resume exactly where you left off
- **Session persistence** — save configs and results to a server-side MySQL database; reload past sessions from the library
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

### Server requirements

- Apache with `mod_rewrite` and `mod_headers`
- PHP 7.4+ with PDO/MySQL
- MySQL 5.7+ / MariaDB 10.3+

### Steps

1. Upload all files to your server directory (e.g. `/debate-timer-deploy/`)
2. Copy `api/config.example.php` to `api/config.php` and fill in your DB credentials
3. Browse to `install.php` to create the database table and set up HTTP Basic Auth
4. Follow the on-screen instructions from `install.php`, then delete it (or it deletes itself)
5. Uncomment the `Auth` block in `.htaccess` and update the `.htpasswd` path shown by `install.php`

### Files NOT committed (deploy manually)

| File | Reason |
|------|--------|
| `api/config.php` | Contains DB credentials |
| `install.php` | One-time setup script |
| `.htpasswd` | Password file |

## Install as a PWA

### Android (Chrome)

1. Open the app URL in Chrome
2. Tap **⋮ → Add to Home screen** (or accept the install banner)
3. The app installs and runs fullscreen — no browser bar

### iPhone (Safari)

1. Open the app URL in Safari
2. Tap the **Share** button
3. Tap **Add to Home Screen** and confirm

## Data & privacy

Session configs and results are stored in your own MySQL database. Nothing is sent to third-party servers. The API is protected by HTTP Basic Auth.

## License

MIT
