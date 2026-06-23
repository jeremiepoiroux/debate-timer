# Debat Timer

A mobile-first discussion and debate moderation tool. Track speaking time per participant, follow a structured agenda with segments, and use the built-in teleprompter for prepared notes — all from a single HTML file with optional server persistence.

## Features

- **Speaking time tracker** — tap a participant card to start/stop tracking their speaking time; pause and resume at any time
- **Balance warnings** — visual indicators when a speaker has talked too much (⬆ Beaucoup) or too little (⬇ Peu) relative to the group average
- **Segments** — split the session into named phases (e.g. "Discussion libre", "Questions public") with individual countdowns
- **Teleprompter** — write structured notes in `N Title / bullets` format; navigate section by section during the session with progress tracking
- **Pause & resume** — step back to the setup screen without losing any accumulated times; resume exactly where you left off
- **Session persistence** — save configs and results to a server-side MySQL database; reload past sessions from the library
- **Offline-ready PWA** — installs on Android and iPhone, works without internet after first load
- **Wake Lock** — screen stays on during a session (Chrome / Android)

## Teleprompter note format

Structure notes with numbered section headers followed by bullet points:

```
1 Introduction
Présentation des participants
Contexte et enjeux

2 Débat principal
Question ouverte : …
Sous-question de relance

3 Synthèse
Points clés à retenir
```

Each section becomes a slide in the teleprompter. Navigate with ← Préc. / Suivant →.

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
