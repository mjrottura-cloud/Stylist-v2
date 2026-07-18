# RIG — Your Personal Stylist

*Rig of the day, decided.* ("Rig of the day" is Navy slang for the prescribed uniform — fitting.)

RIG turns your phone into a fashion designer and personal stylist:

- **The Closet** — snap photos of your clothes; AI automatically catalogs each piece (name, category, colors, formality 1–5, seasons, style tags, pairing notes). Edit anything, favorite pieces, mark items "in laundry" so they're excluded from outfits.
- **Style Me** — pick an occasion (nice dinner, date night, interview, night out…) or write your own, optionally add a location ("Florence, Italy") and weather, optionally anchor everything around one piece you want to wear. RIG builds 3 complete outfits **from clothes you actually own**, with reasoning and styling tips (tuck, cuff, shoes).
- **Pack for a trip** — enter a destination and trip length; RIG builds a mix-and-match capsule from your closet plus a day-by-day outfit plan, tuned to local dress culture.
- **Shop the Gap** — pick a piece you love but can't complete ("I like this shirt but have no pants for it"). RIG looks at the actual photo and suggests exactly what to buy — precise color/fabric/cut — with one-tap searches on Google Shopping, Nordstrom, and ASOS, filtered to your budget.
- **Lookbook** — save outfits you like, log when you wear them, build a record of what works.
- **Style Profile** — your sizes, build, taste, and "never put me in…" list are fed to the stylist on every request.

All data (photos included) is stored **on your device** in the browser's IndexedDB. Nothing is uploaded anywhere except the AI requests you trigger, which go directly to Anthropic.

---

## Deploy on GitHub Pages (5 minutes)

1. Create a new repository on GitHub (e.g. `rig`).
2. Upload these files to the repo root:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `README.md`
3. Go to **Settings → Pages → Source**, choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
4. After a minute your app is live at `https://<your-username>.github.io/rig/`.

### Put it on your phone like a real app
Open the URL in Safari (iPhone) or Chrome (Android) → Share → **Add to Home Screen**. It launches full-screen with its own icon, and the camera button opens your phone's camera directly.

---

## Connect the AI (one-time setup)

RIG's styling brain is Claude. Running from GitHub Pages, you need your own API key:

1. Go to [console.anthropic.com](https://console.anthropic.com) → **API Keys** → create a key.
2. In RIG, open **Profile → AI connection**, paste the key, and save.

The key is stored only on your device and sent only to `api.anthropic.com` over HTTPS. Typical cost is a few cents per styling session. (If the app is run inside Claude.ai as an artifact, it connects automatically with no key.)

---

## Tips for best results

- **Photograph pieces flat or hanging against a plain background**, one item per photo, in decent light. The AI tags colors and formality from what it sees.
- **Fill out your Style Profile first** — sizes, build, taste, and hard "nevers" dramatically improve suggestions.
- **Mark laundry.** Anything "in laundry" is automatically excluded from outfit generation.
- **Use anchors.** "Build around this shirt" is the fastest way to get outfits you'll actually wear.
- **Export a backup** (Profile → Your data) before clearing your browser or switching phones — it includes all photos.

## Files

| File | Purpose |
|---|---|
| `index.html` | The entire app — UI, styling engine, storage, AI calls |
| `manifest.json` | Makes it installable to your home screen |
| `sw.js` | Caches the app shell so it opens offline (AI features need internet) |
