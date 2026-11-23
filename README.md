# HAUNTED HOUSE — Cursed Poker

A single-file, offline Gothic poker roguelike. It can be deployed as a static site on Firebase Hosting; no backend or database is required. Progress is stored in the browser's `localStorage`.

## Play now

[▶️ Play HAUNTED HOUSE in your browser](https://haunted-house-41002.web.app)

No install, no sign-up. The game also works offline if you download `index.html` and open it directly.

## Contents

- `index.html` — the entire game (HTML + CSS + JS + SVG, no external dependencies at runtime)
- `firebase.json` — Firebase Hosting configuration
- `.gitignore` — ignores Firebase/Git artifacts
- `README.md` — this file

## Run locally

Double-click `index.html`, or serve the folder with a small local server:

```bash
npx serve .
```

Then open `http://localhost:3000`.

## Deploy to Firebase Hosting

Requirements: Node.js 18+ and Firebase CLI.

```bash
npm install -g firebase-tools
firebase login
cd haunted-house
firebase use --add      # select your Firebase project
firebase deploy --only hosting
```

Firebase will print a live URL such as `https://PROJECT-ID.web.app`.

## Custom domain

1. Firebase Console → **Hosting** → **Add custom domain**.
2. Add the requested `A` / `CNAME` records at your DNS provider.
3. Once DNS propagates, Firebase issues the SSL certificate automatically.
4. The `rewrites` rule in `firebase.json` routes all paths to `index.html`.

## GitHub

```bash
git init
git add .
git commit -m "HAUNTED HOUSE — initial release"
git branch -M main
git remote add origin https://github.com/USERNAME/haunted-house.git
git push -u origin main
```

No Docker, npm build step or CI is required. As a next step, you can automate `firebase deploy` with GitHub Actions.

## GitHub Pages (alternative)

You can also host the exact same folder directly from GitHub:

1. Repository → **Settings** → **Pages**
2. **Build and deployment** → Source: **Deploy from a branch**
3. Branch: `main`, folder: `/(root)` → **Save**
4. After a few seconds the game is live at:

```text
https://USERNAME.github.io/haunted-house/
```

GitHub shows source code when you click `index.html`; use the live URL above to actually play.

## Notes

- Title and theme: **HAUNTED HOUSE**.
- The original `house-poker-v10.html` is kept separately; this folder is the clean release copy.
- Daily seeds, unlocked jokers and achievements are stored locally in the browser. Firebase only serves static files.
- The dealer target is not a fixed curve. It is estimated from 24 simulated runs using your current deck, jokers and upgrades, then adjusted by boss, bribe and difficulty-curse modifiers.
- The game UI is entirely in English and works offline.
