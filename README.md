# Flow Planner — live demo (GitHub Pages)

A self-contained, installable PWA shell that hosts the **Flow Planner** live demo.
Link it from your Etsy listing as "Try the live demo" — visitors can use it in the
browser and **Add to Home Screen** so it opens like a real app, with your ocean icon.

> This is the **demo** build (sample data, resets on refresh) with the
> "Get the full planner" banner pointing to your shop. It is the public, try-before-you-buy
> version — not the paid file you sell on Etsy.

## Files

```
index.html               the Flow Planner demo (single file)
manifest.webmanifest      PWA manifest (name, icons, colors)
sw.js                     service worker (offline caching)
favicon.ico               browser tab icon
.nojekyll                 tells GitHub Pages to serve files as-is
icons/                    app icons generated from your ocean icon
  icon-192.png  icon-512.png                 (standard)
  icon-192-maskable.png  icon-512-maskable.png (Android adaptive, padded)
  apple-touch-icon.png    (iOS home screen, 180px)
  favicon-32.png  favicon-16.png
```

## Deploy (about 2 minutes)

**Option A — GitHub website (no command line)**
1. Create a new repository, e.g. `flow-planner`.
2. Click **Add file → Upload files**, drag in everything from this folder
   (keep the `icons/` folder together), and commit.
3. Go to **Settings → Pages**. Under *Build and deployment*, set
   **Source = Deploy from a branch**, **Branch = main**, **Folder = / (root)**. Save.
4. Wait ~1 minute. Your demo is live at
   `https://YOUR-USERNAME.github.io/flow-planner/`

**Option B — git**
```bash
git init && git add . && git commit -m "Flow Planner demo"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/flow-planner.git
git push -u origin main
# then enable Pages as in Option A, step 3
```

## Custom domain (optional)
In **Settings → Pages → Custom domain**, add e.g. `flow.dreamstodone.com`, then create a
`CNAME` DNS record at your registrar pointing to `YOUR-USERNAME.github.io`. GitHub will add
a `CNAME` file for you.

## Updating later
When you change the app, replace `index.html` (export a fresh demo) **and bump the cache
version** in `sw.js` — change `flow-planner-v1` to `-v2`, etc. Without that bump, returning
visitors keep the old cached copy.

## Notes
- **Install:** on iPhone, Safari → Share → *Add to Home Screen*. On Android, Chrome offers
  *Install app* / *Add to Home screen*. Your ocean icon is used on the home screen.
- **Offline:** the service worker caches the app so it opens with no connection. Brand fonts
  (Fraunces, Hanken Grotesk) load from Google Fonts when online and fall back to system
  fonts offline. Want pixel-perfect fonts offline too? I can self-host them in this bundle.
- **Want a private full-app copy hosted instead of the demo?** Swap `index.html` for the
  paid file — just remember that publishing the full app for free competes with your Etsy sales.
