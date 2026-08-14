# Personal website

Static site, single self-contained `index.html`. No build step.

## Local preview

```
python3 -m http.server 8000
```

Then open http://localhost:8000

## Deploy to GitHub Pages

1. Create a repo named `<your-github-username>.github.io` on GitHub (public, no README).
2. Then from this folder:

```
git remote add origin https://github.com/<your-github-username>/<your-github-username>.github.io.git
git branch -M main
git push -u origin main
```

3. In the repo: **Settings → Pages → Source: Deploy from a branch → `main` / `(root)`**.

The site goes live at `https://<your-github-username>.github.io` within a minute or two.

## Editing

- **Photo:** replace `Photo.jpg`.
- **CV:** replace `CV.pdf`.
- **Papers:** each entry is a `<div class="paper">` block. Copy an existing one to add another.
- **Abstracts / paper links:** the template supports collapsible abstracts. Add inside a `.paper`:

```html
<div class="paper-links">
  <a href="#" onclick="toggle('abs1'); return false;">&#9656; Abstract</a>
  <a href="paper.pdf" target="_blank">[Paper]</a>
</div>
<div class="expandable" id="abs1">Abstract text here.</div>
```

Use a unique `id` per abstract (`abs1`, `abs2`, ...).

## Before going live: set your real URL

Every SEO tag currently points at a placeholder. Social previews and the canonical
tag need absolute URLs, so this must be replaced or link previews break silently.

Run this once from this folder, substituting your real site URL (no trailing slash):

```
grep -rl 'https://REPLACE-ME.github.io' . --exclude-dir=.git | xargs sed -i '' 's|https://REPLACE-ME.github.io|https://YOUR-REAL-URL|g'
```

Verify nothing is left:

```
grep -r 'REPLACE-ME' . --exclude-dir=.git
```

## SEO checklist

- [ ] Replace the placeholder URL (above)
- [ ] Push to a **public** repo named `<username>.github.io`, enable Pages
- [ ] Point the old Google Sites page at the new URL, or take it down
- [ ] Add the site URL to your Google Scholar profile (Homepage field)
- [ ] Ask UCLA Economics and CCPR to link your site from your profile pages
- [ ] Update the URL printed on CV.pdf
- [ ] Add the property in Google Search Console and submit `sitemap.xml`
