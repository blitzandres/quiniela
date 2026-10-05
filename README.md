# Quiniela: World Cup 2026 Prediction Pool

Decentralized prediction pool for the FIFA World Cup 2026. Nickname + PIN auth,
real-time sync via Firebase Firestore, live scores via api-sports.io, group
consensus odds, and automatic standings.

No build step: plain HTML/CSS/JS with the Firebase compat SDK.

- **Project page:** https://andresblitz.com/projects/quiniela/

## Features

- Standings, match picks, specials (champion, runner-up, top scorer), results and share tabs
- Real-time sync across everyone in the pool through Firestore
- Live final scores pulled from api-sports.io (API-Football) and written back for everyone
- Automatic scoring and standings

## Files

| File | Purpose |
|------|---------|
| `index.html` | HTML shell (header, nav, `#q-app` mount point) |
| `app.js` | All app logic: fixtures, Firebase sync, live scores, scoring, rendering |
| `style.css` | Styles |
| `config.example.js` | Template for local config (API keys) |
| `config.js` | Your real config. **Gitignored, never commit it** |
| `metadata.json` | App index / notes for humans and AI tools |

## Setup

1. Clone the repo:
   ```bash
   git clone https://github.com/blitzandres/quiniela.git
   cd quiniela
   ```
2. Create your local config and add your api-sports.io key:
   ```bash
   cp config.example.js config.js
   # edit config.js and replace YOUR_API_SPORTS_KEY with your key
   ```
   Get a key from [API-Football / api-sports.io](https://dashboard.api-football.com/).
   Without a key the app still works; live score sync just shows "Not configured".
3. Serve the folder with any static server:
   ```bash
   python3 -m http.server 8000
   # open http://localhost:8000
   ```

> Note: anything in `config.js` is still sent to the browser, so the key is
> visible to anyone using the deployed site. Use a restricted/free-tier key,
> or proxy the API through a small serverless function if that matters.

## Deploying

The app is static, so any static host works. Because `config.js` is gitignored,
a host that serves straight from this repo (e.g. GitHub Pages) won't have it.
Provide `config.js` at deploy time, or live score sync will be disabled.
