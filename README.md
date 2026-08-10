# Personal website

One file, `index.html`, containing everything. No build step, no dependencies to install. Open it in a browser to see it; open it in a text editor to change it.

## Editing

The file is divided into sections marked by comment blocks that look like this:

```html
<!-- ==============================================================
     PUBLICATIONS
     ============================================================== -->
```

Anything in square brackets — `[Your University]`, `[Coauthor Name]` — is a placeholder for you to replace. Search the file for `[` to find them all.

### Adding a paper

Each entry is one `<li>` block. Copy an existing one and change the contents:

```html
<li>
  <span class="year">2026</span><span class="item-body">
    <span class="title">The title of the paper</span>
    <span class="venue">with A. Coauthor. <em>Journal</em> <strong>12</strong> (2026), 1&ndash;40.</span>
    <span class="links">
      <a href="https://arxiv.org/abs/2601.12345">arXiv</a>
      <a href="https://doi.org/10.1234/abcd">DOI</a>
    </span>
  </span>
</li>
```

Drop any of the inner `<span>` lines you don't need. Entries are listed newest first; the ordering is manual, so put new ones at the top.

Talks and courses use the identical structure, so the same recipe applies.

### Mathematics

Inline math goes between `\(` and `\)`, displayed math between `$$` and `$$`. Standard LaTeX macros work. Rendering is done by KaTeX, loaded from a CDN in the `<head>`. If you decide you never want math, delete the three KaTeX lines there and the page loses its only external dependency.

Those three lines load code from jsDelivr without subresource-integrity hashes. If you'd like the browser to verify the files haven't been tampered with, copy the current `integrity="sha384-..."` attributes from the installation snippet at [katex.org/docs/browser](https://katex.org/docs/browser) and paste them in. Worth doing, but the page works either way.

### Files to add alongside index.html

- `photo.jpg` — a square portrait. Already present. If absent, the image quietly hides itself.
- `favicon.svg` — the tab icon, an EV monogram. Already present; edit the colours or letters directly, it's four lines of SVG.
- `cv.pdf` — not yet present. Once you add it, uncomment the CV line in the contact section.
- Any `slides.pdf`, `notes.pdf` you link to.

### Two things to do before publishing

The Teaching section is commented out because it still holds placeholder course codes. Fill in your real courses, uncomment the block, and add `<a href="#teaching">Teaching</a>` back to the `<nav>` list.

The link-preview tags in the `<head>` point at `https://example.com/`. Replace that with your real address once you have one, or previews in Slack and Mastodon will show no picture.

### Appearance

All styling is in the `<style>` block near the top. The colours are defined once at the very top as CSS variables:

```css
--link: #7a2018;   /* link colour, currently a dark red */
--bg:   #fdfcfa;   /* page background */
```

Change those two and the whole page shifts. `--measure` controls the width of the text column.

## Publishing to GitHub Pages

1. Create a GitHub account if you don't have one.
2. Create a repository named exactly `yourusername.github.io` (substituting your actual username). Make it public.
3. Upload `index.html` and any PDFs — the web interface has an "uploading an existing file" link on the empty repository page, so no command line is needed.
4. Wait a minute. The site appears at `https://yourusername.github.io`.

To update it later, edit the file on GitHub directly (click the file, then the pencil icon) or re-upload it.

### A custom domain

If you buy a domain, add a file named `CNAME` to the repository containing just the domain name, then point the domain's DNS at GitHub's servers per their documentation. This is worth doing: the URL then follows you between institutions.

## Checking your work

Open `index.html` in a browser after each round of edits. If something looks broken, the usual cause is a deleted or unclosed `</span>` or `</li>` tag.
