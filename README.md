# Flow Planner — full app (GitHub Pages / hosted link)

This bundle hosts the **full** Flow Planner as an installable web app. Sell or share the
link; on a phone it can be added to the home screen with your ocean icon and opens like a
native app, fully offline.

> This is the **full** build (`index.html`, no demo banner). Each visitor's data is saved
> in their own browser and persists across visits. There's a one-time "Welcome aboard" card
> on first open. Anyone who has the URL can use the full app, so treat the link as the
> product (e.g. deliver it on purchase) rather than posting it publicly.

## Files
```
index.html               the full Flow Planner app
manifest.webmanifest      PWA manifest (name, icons, colors)
sw.js                     service worker (offline caching) — cache: flow-planner-v2
favicon.ico               browser tab icon
.nojekyll                 serve files as-is on GitHub Pages
icons/                    icons generated from your ocean icon
  icon-192.png  icon-512.png                  (standard)
  icon-192-maskable.png  icon-512-maskable.png (Android adaptive, padded)
  apple-touch-icon.png    (iOS home screen, 180px PNG — fixes the home-screen icon)
  favicon-32.png  favicon-16.png
```

## Deploy (~2 minutes)
**GitHub website (no command line)**
1. Create a repository, e.g. `flow-planner`.
2. **Add file → Upload files**, drag in everything here (keep the `icons/` folder together), commit.
3. **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*,
   Branch = `main`, Folder = `/ (root)`. Save.
4. After ~1 minute it's live at `https://YOUR-USERNAME.github.io/flow-planner/`.

**git**
```bash
git init && git add . && git commit -m "Flow Planner"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/flow-planner.git
git push -u origin main
# then enable Pages as above
```

## Add to Home Screen (what your buyers do)
- **iPhone (Safari):** Share → *Add to Home Screen*. Your ocean icon appears; it opens
  full-screen with no browser bars.
- **Android (Chrome):** the *Install app* / *Add to Home screen* prompt uses the same icon.

## Updating later
Replace `index.html`, then **bump the cache version** in `sw.js`
(`flow-planner-v2` → `-v3`). Without the bump, returning visitors keep the old cached copy.

## Notes
- **Offline:** the service worker caches the app so it opens with no connection. Brand
  fonts load from Google Fonts online and fall back to system fonts offline — want them
  embedded for pixel-perfect offline type? I can add that (~200 KB).
- **Custom domain:** Settings → Pages → Custom domain (e.g. `flow.dreamstodone.com`) plus a
  CNAME DNS record to `YOUR-USERNAME.github.io`.
