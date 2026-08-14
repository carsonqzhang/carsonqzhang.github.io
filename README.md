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

## Site URL

Live at **https://carsonqzhang.github.io** — this URL is baked into the canonical tag,
Open Graph tags, JSON-LD, `robots.txt`, and `sitemap.xml`. If you ever move to a custom
domain, update it everywhere with:

```
grep -rl 'https://carsonqzhang.github.io' . --exclude-dir=.git | xargs sed -i '' 's|https://carsonqzhang.github.io|https://NEW-DOMAIN|g'
```

