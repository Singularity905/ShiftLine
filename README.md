# Shiftline: install on your iPhone

Shiftline is a Progressive Web App: plain HTML, CSS, and JavaScript. No account, no server, no cost. Your data stays in Safari's storage on your phone.

## Files
- `index.html`: the whole app
- `sw.js`: service worker (offline support)
- `manifest.webmanifest`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`: Home Screen icon and name

## Why it needs hosting
iPhone Home Screen apps must be served over **HTTPS** for offline support to work. Opening `index.html` straight from the Files app will not work well. Free HTTPS hosting is enough:

### Option A: GitHub Pages (free, works from a computer or phone browser)
1. Make a free account at github.com.
2. Create a new **public** repository, e.g. `shiftline`. (Only the app code goes here; your personal data never leaves your phone.)
3. Upload all files from this folder to the repository root ("Add file" → "Upload files").
4. Settings → Pages → Source: "Deploy from a branch", Branch: `main`, folder `/ (root)` → Save.
5. After a minute or two your app is at `https://YOUR-NAME.github.io/shiftline/`.

### Option B: Netlify Drop (free, needs a computer)
1. Go to app.netlify.com/drop.
2. Drag this whole folder onto the page. You get an `https://….netlify.app` address. Create a free account to keep it permanently.

## Add to Home Screen
1. Open your HTTPS address in **Safari** on the iPhone.
2. Tap the **Share** button → **Add to Home Screen** → **Add**.
3. Open Shiftline from the Home Screen icon (not from Safari) from now on. Data saved in Safari and in the Home Screen app are kept separately.

## Updating
Replace the files on your host. The app picks up the new version the next time it is opened with a connection (open it twice if it still looks old).

## Run it on a computer (for testing)
```
python3 -m http.server 8000 -d shiftline-pwa
```
Then open http://localhost:8000.

## Limitations (honest list)
- **No reminders while closed.** iOS only lets web apps notify through a push server, which this version does not use. Use Settings → Backup → "Download calendar file" to add wake, leave-by, and wind-down alerts to Apple Calendar, or set iPhone alarms.
- **Data lives on one phone.** Use Settings → Backup weekly. Deleting the Home Screen app deletes its data.
- **Fonts** load from Google Fonts the first time; offline after that, or the system font is used.
