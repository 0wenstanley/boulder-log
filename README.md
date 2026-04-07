# Boulder Log

A progressive web app (PWA) for logging boulder climbs and scanning photos to highlight holds. Built as a single-file HTML app and hosted via GitHub Pages.

## Features

- Log climbs with gym, wall, grade, hold colour, tries, send status, date, notes and photo
- Manage gyms with custom walls and grading systems (V-scale, Font, colour, custom)
- Stats dashboard with per-gym filtering for tracking progress at each gym
- Import/export data as JSON or CSV
- Installable as a PWA on mobile and desktop, works offline

## Installing the app

### On iPhone / iPad (Safari)

1. Open the GitHub Pages URL in Safari.
2. Tap the Share button.
3. Tap "Add to Home Screen".
4. Tap "Add" in the top right.

### On Android (Chrome)

1. Open the GitHub Pages URL in Chrome.
2. Tap the three-dot menu.
3. Tap "Install app" or "Add to Home Screen".

### On desktop (Chrome/Edge)

1. Open the GitHub Pages URL.
2. Click the install icon in the address bar (or menu → "Install Boulder Log").

## Pushing updates

When you make changes to `index.html`, `sw.js`, `manifest.json` or any other file:

1. **Bump the cache version** in `sw.js`. Find the line like `const CACHE = 'boulder-log-v1'` and increment it (e.g. `v1` → `v2`). This forces the service worker to fetch the new files instead of serving stale cached copies.
2. **Commit and push**:

   ```
   git add -A
   git commit -m "Describe your change"
   git push
   ```

3. GitHub Pages will redeploy automatically, usually within a minute.

## Receiving updates on an installed app

Because the app is a PWA with a service worker, installed copies cache files locally. After you push a new version:

1. Open the installed app (or the site in a browser).
2. The service worker will detect the new cache version in the background.
3. Close and reopen the app to activate the update.
4. If the app still looks stale, hard reload in a browser tab (Cmd+Shift+R on Mac, Ctrl+Shift+R on Windows/Linux).
5. As a last resort, uninstall and reinstall the PWA, or in DevTools → Application → Service Workers, click "Unregister" and reload.

## Local development

No build step is required. Edit `index.html` directly and open it in a browser. For service worker and PWA features to work properly, serve it over HTTP:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## File structure

- `index.html` — the entire app (HTML, CSS, JS in one file)
- `sw.js` — service worker for offline caching
- `manifest.json` — PWA manifest
- `icon-192.png`, `icon-512.png` — app icons

## Data storage

All data is stored locally in the browser via IndexedDB. Use the Export feature in the app's Settings tab to back up your climbs and gyms.
