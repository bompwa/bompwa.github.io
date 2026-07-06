# Laser Chess — PWA deploy kit

Everything in this folder is a complete, installable progressive web app. Deploy the
folder contents to any static host and it becomes a home-screen app that works offline.

## What's in here
- `index.html` — the full game (engine, AI, UI). Also works opened directly as a file.
- `manifest.webmanifest` — app name, icons, standalone display.
- `sw.js` — service worker: precaches the app, runtime-caches fonts, full offline play.
- `icon-192.png`, `icon-512.png`, `icon-512-maskable.png`, `apple-touch-icon.png` — app icons.

## Deploy (pick one)

### GitHub Pages (free, ~5 min)
1. Create a repo (e.g. `laser-chess`), upload these files to the repo root.
2. Repo Settings → Pages → Source: `main` branch, root folder. Save.
3. Game is live at `https://<username>.github.io/laser-chess/`.

### Any static host
Upload the folder contents to the web root (Netlify/Cloudflare Pages drag-and-drop,
or a subdirectory of an existing site). HTTPS is required for the service worker
and Add to Home Screen — all the hosts above provide it automatically.

## Install on a phone
- **iPhone:** open the URL in Safari → Share → Add to Home Screen.
- **Android:** open in Chrome → the install prompt appears, or menu → Add to Home screen.

Launches full-screen with its own icon, plays offline after the first load.

## Notes for the Cowork session
- Scope: deploy only. The game code is final for this iteration — no edits needed.
- If updating the game later: bump `CACHE = "laser-chess-v2"` in `sw.js` so
  installed copies fetch the new version.
- Rating/score persistence: inside Claude's artifact viewer it uses window.storage;
  as a deployed PWA it is session-only (in-memory). Adding localStorage persistence
  for the deployed version is a safe 5-line change if wanted — it's only avoided in
  the source because Claude.ai's artifact sandbox doesn't support it.
