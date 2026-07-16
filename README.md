# VOGELFREI Website

A static site (plain HTML/CSS/JS — no build step) for the VOGELFREI Institute, styled to match your Meridian Institute reference.

## Files

```
index.html              Homepage — hero + "ongoing work" section
what-who-why.html       Mission page — What we do / Who we are / Why
founders.html           Founder bios
nonprofit-status.html   501(c)3 tax status + donate section
styles.css              All site styling (colors, fonts, layout — one file)
script.js               Mobile menu + scroll animations
assets/                 Logo files (gold + cream bird mark, watermark, favicon)
```

Every page has the same header/footer and loads the same `styles.css` and `script.js`, so editing colors or fonts once in `styles.css` updates the whole site.

---

## One-time setup: GitHub → Cloudflare Pages

1. **Create a GitHub repo** (if you haven't already) and upload all the files above, keeping the `assets/` folder structure intact.
2. Go to the **Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git**.
3. Select your repo. Build settings:
   - Framework preset: **None**
   - Build command: *(leave blank)*
   - Build output directory: `/`
4. Deploy. Cloudflare gives you a `*.pages.dev` URL immediately.
5. In your Pages project → **Custom domains**, add `vogelfrei.net` (and `www.vogelfrei.net` if you want it). Since your domain is already on Cloudflare, DNS connects automatically — no manual record editing needed.

That's it. From now on, **any push to your GitHub repo's main branch auto-deploys to vogelfrei.net** within about a minute.

---

## Making edits (no coding required, for text changes)

1. Go to your repo on **github.com**.
2. Open the file you want to change (e.g. `founders.html`).
3. Click the **pencil icon** (top right of the file view) to edit in your browser.
4. Find the text — every editable spot is marked with a comment like `<!-- EDIT: ... -->` right above it. Change only the text between the tags (the stuff between `>` and `<`), leave the tags themselves alone.
5. Scroll down, click **Commit changes**.
6. Wait ~30–60 seconds — Cloudflare Pages auto-rebuilds. Refresh vogelfrei.net to see it live.

### Common edits and where to find them

| What you want to change | File | Look for |
|---|---|---|
| Homepage headline / tagline | `index.html` | `<!-- EDIT: main headline -->` |
| Featured/ongoing project | `index.html` | `<!-- ========== ONGOING WORK ========== -->` section |
| Mission statement | `what-who-why.html` and `nonprofit-status.html` | `<!-- EDIT: ... -->` comments |
| Founder names/bios/photos | `founders.html` | one `.founder-card` block per person |
| EIN / tax status details | `nonprofit-status.html` | `<!-- ========== TAX DOCUMENT PANEL ========== -->` |
| Donate button link | `nonprofit-status.html` | `<a href="#" class="btn btn-solid">Donate Now</a>` — replace `#` with your donation link |
| Contact email / cities | Bottom of every page (footer) | `<!-- EDIT: contact email and locations -->` |
| Site-wide colors/fonts | `styles.css` | The `:root { ... }` block at the very top |

### Adding a real photo (replacing a placeholder)

Placeholders are gradient boxes marked "Placeholder — swap for project photo" etc. To replace one:

1. Upload your image into the `assets/` folder in GitHub (drag-and-drop works on github.com).
2. In the HTML file, find the placeholder `<div>` (e.g. `.feature-image` or `.founder-photo`) and replace its contents with:
   ```html
   <img src="assets/your-photo.jpg" alt="Describe the photo">
   ```
3. Commit. Done.

### Editing the navigation menu / adding a page

The header and footer are repeated at the top/bottom of every HTML file (marked with `<!-- NAVIGATION -->` / `<!-- FOOTER -->` comments). If you add a menu link or new page, update it in **all four** HTML files so the nav stays consistent everywhere.

---

## If you want AI-assisted edits going forward

For back-and-forth editing where you describe a change in plain English and it gets made *and pushed* automatically, install **Claude Code** (Anthropic's coding agent) and point it at your local clone of this repo — it can edit these files and run `git push` for you directly, so the loop becomes: type the change → it's live. This site was built so that either that workflow, or plain manual GitHub edits, both work without any restructuring.
