# Thame Flood Early Warning System — website

This folder is ready to push straight to a GitHub repo and publish with GitHub Pages. It is built so we can make future text edits yourself, directly on github.com, with no coding and no build step.

## Files

- `index.html` — the full interactive site (with maps). This is the main page.
- `simple.html` — a lighter fallback version with static map images instead of interactive maps.
- `images/` — every photo, diagram, the report PDF, the shapefiles, and the siren-demo video used by the two pages above.

Everything is bilingual (English / Nepali) in a single page, switched with the **EN / NP** pill at the top. There's nothing to build or compile — these are plain HTML files you can open directly in a browser or upload as-is.

## Publishing on GitHub Pages

1. Create a new GitHub repository and upload everything in this folder (keep the `images/` folder structure as-is).
2. In the repo, go to **Settings → Pages**, set the source to your default branch, and save.
3. Your site goes live at `https://YOUR-USERNAME.github.io/YOUR-REPO/index.html` (or just the repo root if `index.html` is at the top level, which it is here).

If you want a custom domain, see the domain/DNS steps already discussed separately — they apply the same way to this folder.

## Editing text — no coding needed

You do not need any software installed, and you do not need to know HTML. Everything below can be done in a browser, on github.com:

1. Open the file (`index.html` or `simple.html`) in your repo on github.com.
2. Click the **pencil icon** ("Edit this file") in the top right of the file view.
3. Use your browser's **Find** (Ctrl+F / Cmd+F) to jump to the sentence you want to change — search for a few words of the text you see on the live site.
4. Type your change directly into the text, the same way you'd edit a Word document.
5. Scroll to the bottom, add a short note in "Commit changes" (e.g. "update station count"), and click **Commit changes directly to the main branch**.
6. Wait about a minute; GitHub Pages rebuilds automatically and your change is live. No install, no terminal, no build step — ever.

A few things to know while editing:

- **Bilingual pairs.** Most text appears twice in a row, wrapped like this:
  ```html
  <span class="t-en">English sentence here</span><span class="t-np">नेपाली वाक्य यहाँ</span>
  ```
  Edit the English inside `t-en` and the Nepali inside `t-np` independently, right next to each other. Only one is visible at a time depending on the language toggle; that's normal, don't delete either one.
- **Photo captions and alt text** sometimes use `data-en-alt` / `data-np-alt` attributes instead (for accessibility text) — same idea, edit the matching language's value inside the quotes.
- **Station data, map labels, and the two diagrams** (Automatic Weather Station photo diagram, "what is a glacial lake" infographic) live inside the big `<script>` block near the bottom of `index.html`. Look for the `STATIONS` array for things like station names, elevations, and descriptions — each field has an `_en` and `_np` version, e.g. `name_en: "Thyangbo AWS"`, `name_np: "Thyangbo AWS"`.
- **`index.html` and `simple.html` share most of the same text.** If you change a sentence in one and want it consistent, make the same change in the other file too.
- Always keep the surrounding `<...>` tags and quote marks exactly as they are, only change the words between them (or inside the quotes for `alt`/`data-*` attributes). If a page looks broken after an edit, it's almost always a missing `<`, `>`, or `"` — compare against a version from before your edit to spot it.

## Quick-edit cookbook

Common changes and where to find them (use Ctrl+F / Cmd+F with the "search for" text below, inside `index.html`):

| I want to... | Search for | What to do |
|---|---|---|
| Change the site title / hero heading | `Early Warning and Community-Based Emergency Response` | Edit the text inside the `<h1>` tag (English) and its Nepali `t-np` pair right after it |
| Update the station count badge | `2 AWS, 3 HS, 5 sirens` | Edit the numbers directly |
| Add or change a download (report/shapefile) | `<!-- ============ DOWNLOADS ============ -->` | Copy one whole `<div class="dl-item">...</div>` block, change the name/description text, and change the `href="images/downloads/..."` to point at a new file you've added to `images/downloads/` in the repo |
| Change a station's name, elevation or description | `const STATIONS = [` (inside the `<script>` near the bottom) | Find that station's `{...}` entry and edit its `_en` / `_np` fields |
| Update the Next Phase / funding needs section | `<!-- ============ PART 4: NEXT PHASE & WAY FORWARD ============ -->` | Edit the text inside that section |
| Change a photo | any `<img src="images/...">` tag | Upload the new photo into the `images/` folder (same or new filename), then update the `src="images/..."` path to match |
| Update contact / footer info | `<!-- ============ PART 4: OUTCOMES` ...then scroll to `<footer` | Edit the text inside `<footer id="contact">` |

Every major section of the page also has an HTML comment marker like `<!-- ============ DOWNLOADS ============ -->` right above it — searching for these is the fastest way to jump to a section without reading the whole file.

## A note on the maps

The interactive maps on `index.html` use [Leaflet](https://leafletjs.com), loaded from a public CDN (`unpkg.com`) rather than bundled into the file. This keeps the repo small and the file easy to read/edit, but it does mean the maps need an internet connection to load (which any real visitor will have).

## If something breaks

GitHub keeps every past version of every file. If an edit breaks the page, open the file on github.com, click **History**, and open the previous version to see (and copy back) the working text, or use the "..." menu to revert the commit entirely. You cannot lose the working site permanently by editing in the browser.
