[README.md](https://github.com/user-attachments/files/28967105/README.md)
# Best Summer Weekend Cookbook

A data-driven web app and bundled-shell base for a hybrid Apple/Android app.
Recipes by Jane Rodmell (originally from *Cottage Life*).

## What deploys (site root)
Upload the contents of this folder (everything except `_project-assets/`) to Netlify.

- `index.html` — the app shell. Renders entirely from the data feed.
- `recipes.json` — the data feed (v1.3): 7 categories, 360 recipes, the Herbs page,
  per-category landing copy, and the daily "Helpful Hint" pools. Re-upload this to update the site.
- `stamp.svg` — the single-ink seal/logo (scalable, ~3 KB).
- `netlify.toml` — caching rules (fresh `recipes.json`, long-cached images).
- `images/` — web-optimized photos. Each `name.jpg` has a matching `name-thumb.jpg`
  (carousels and banners use the thumbs). Includes `logo-optimized.png`.

## _project-assets/ (NOT served)
Reference material kept with the project, not part of the live site:
- `logo-original.png` — full-resolution logo.
- `Best_Summer_Weekends_master.xlsx` — index transcription + recipe master.
- `Best_Summer_Weekends_subtables.xlsx` — the 7 chapter sub-tables + fresh categories.

## How it works
- `index.html` ships with a baked-in copy of the data (instant first paint / offline),
  then fetches the live `recipes.json` on top. Update the feed → site updates.
- Routing is hash-based: `#/cat/<slug>` for categories, `#/page/<slug>` for pages (e.g. `#/page/herbs`).
- `USE_REAL_IMAGES` is on; carousels auto-request the `-thumb` variants.

## Deploy
1. Drag this folder's contents into Netlify (no build command; publish dir = root).
2. Confirm it loads on the temporary `*.netlify.app` URL and photos appear.
3. Add the Hover domain; wait for DNS + free SSL to settle.
4. For the native app build, set `CONFIG.apiUrl` in `index.html` to
   `https://yourdomain.com/recipes.json` so the bundled app pulls live updates.

## Still to come
- Individual-recipe detail (ingredients, yields, methods) → nutrition.
- Deeper per-chapter hint pools.
- The MySQL database that generates `recipes.json`.
- A proper herb close-up for the Herbs hero (currently a stand-in).
