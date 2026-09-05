# Off the Planckian Locus: Using 2D Chromaticity to Improve In-Camera Color

Project page for the ECCV 2026 paper.

**Paper:** https://arxiv.org/abs/2511.17133

```
index.html    all page content
style.css     all styling
images/       figures
.nojekyll     tells GitHub Pages to serve files as-is
```

Plain HTML and CSS. No build step, no dependencies, no frameworks. The only JavaScript is about
twenty lines at the bottom of `index.html` for the result tabs and the image carousel.

## Publishing on GitHub Pages

1. Create a repository. Naming it `<username>.github.io` publishes at that address automatically;
   any other name publishes at `<username>.github.io/<repo>/`.
2. **Add file → Upload files**, then drag in the contents of this folder — `index.html`,
   `style.css`, and the whole `images` folder. Commit.
3. If the repo is *not* named `<username>.github.io`, go to **Settings → Pages** and set
   *Source: Deploy from a branch*, branch `main`, folder `/ (root)`.
4. Wait a minute or two, then load the URL.

Drag the `images` folder itself, not the files inside it — the uploader keeps the folder structure,
and the page looks for `images/…` and `images/wild/…`.

## One edit before you publish

`index.html` line 12 sets the link-preview image, and Open Graph requires an absolute URL:

```html
<meta property="og:image" content="images/og-teaser.png">
```

Change it to the live address once you know it, e.g.

```html
<meta property="og:image" content="https://ccmmlp.github.io/images/og-teaser.png">
```

Without this, links shared on Slack, X, or Bluesky show no preview image. Everything else on the
page works with relative paths and needs no change.

## Previewing locally

Serve the folder rather than double-clicking `index.html`:

```bash
python3 -m http.server 8000     # then open http://localhost:8000
```

Over `file://` the page's origin is `null` and the YouTube embed refuses to load — the video shows
blank or "Video unavailable" while everything else renders. That is a local-preview artifact only;
it works correctly once served, including on GitHub Pages.

## Editing

**Text** — all body copy is in `index.html`, written to match the paper's wording. Figure captions
sit in `<figcaption>` next to each image.

**Header links** — the `<nav class="links">` block near the top. Code is currently a non-clickable
"coming soon" pill; swap it for `<a class="btn" href="...">Code</a>` when the repo is public.

**Tabs** — Quantitative Results and Qualitative Results each use a `.tabs` row plus one `.scene`
block per tab, matched by `data-scene`. Add a button and a matching scene; no JavaScript changes.

**Carousel** — the in-the-wild strip is a `.car-track` row of `.car-item` figures. To change how
many show at once, edit the divisor in `.car-item`'s `flex-basis` in `style.css`.

**Colors and spacing** — the `:root` variables at the top of `style.css` drive the whole page.

## Figures

Paper figures were converted from the LaTeX source with `pdftocairo -svg` (diagrams and plots, kept
as vector) or `pdftoppm` at ~2200px (photo-heavy comparisons, kept as PNG rather than JPEG since
lossy compression on color-reproduction results is a bad idea). Poster panels were exported from
Affinity as transparent PNG, then flattened onto white and resized to 2400px.

| File | Origin |
|---|---|
| `fig1-teaser.svg` | paper Fig. 1 |
| `panel-1d-vs-2d.png` | poster |
| `panel-pipeline.png` | poster |
| `panel-colorimetric-stage.png` | poster |
| `fig3-training.svg` | paper Fig. 3 (stage 2) |
| `panel-multi-illuminant.jpg` | poster |
| `fig7-macs-vs-resolution.svg` | paper Fig. 7 |
| `panel-lightbox-charts.png` | capture set |
| `wild/wild-01…12.jpg` | capture set (carousel) |
| `fig5-lightbox-results.png` | paper Fig. 5 |
| `fig6-in-the-wild.png` | paper Fig. 6 |
| `fig8-multi-illuminant.svg` | paper Fig. 8 |
| `og-teaser.png` | raster of Fig. 1, for link previews |

## Citation

```bibtex
@inproceedings{tedla2026planckian,
  title     = {Off the Planckian Locus: Using 2D Chromaticity to Improve In-Camera Color},
  author    = {Tedla, SaiKiran and Little, Joshua and Karaimer, Hakki C. and Brown, Michael S.},
  booktitle = {European Conference on Computer Vision (ECCV)},
  year      = {2026}
}
```
