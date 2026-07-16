# whatiiif

Create shareable deep links to highlighted regions inside digitized primary sources. Paste a page URL from a supported library, archive, or museum (or a direct IIIF manifest URL), drag a box over the part you care about, and get back a permanent link, an embeddable iframe, or an IIIF Content State token that points precisely at that region.

Live at [whatiiif.com](https://whatiiif.com). Works with any IIIF Presentation API 2 or 3 source.

## What it does

1. **Paste a URL.** A page URL from a supported institution, a direct IIIF manifest URL, or a share link from another IIIF viewer (any URL carrying a `?manifest=` parameter). whatiiif detects the source and resolves it to a manifest for you.
2. **Find the page.** Multi-page items get page navigation, so you can move to the exact leaf you want.
3. **Select a region.** Drag a box in the deep-zoom viewer, or switch to pan and zoom to move around first. Keyboard users can pan with the arrow keys, zoom with `+` and `-`, or type exact coordinates under "Refine selection." Optional aspect-ratio constraints (phone 9:16, desktop 16:9, square, US Letter, A4) keep crops tidy.
4. **Add a label and share.** Give the region a caption, then copy any of:
   - a **shareable highlight link** back to whatiiif that reopens the region in context,
   - an **embeddable iframe** (small, medium, or large) for a course page, LMS, or blog,
   - an **IIIF Content State token** (Content State API 1.0) that pastes into any compatible viewer, with a one-click "open in Theseus" shortcut.
5. **Download.** Grab the selected region or the full page at full resolution straight from the source image server.

Other niceties: a light and dark (Night) theme that remembers your choice, a chromeless `/embed` view built for iframing, and an attribution bar on embeds that always credits the source institution.

## Supported institutions

Paste a normal item or catalog page URL from any of these and whatiiif resolves the manifest automatically:

- Library of Congress (item pages, Chronicling America newspaper pages, and general resource URLs)
- Harvard Digital Collections (viewer links, DRS URN manifests, and CURIOSity catalog pages)
- Yale Library
- Internet Archive
- Smithsonian Libraries
- Biodiversity Heritage Library
- Cambridge Digital Library
- UCLA Digital Collections
- Princeton University Library (DPUL)
- Northwestern University Libraries Digital Collections
- Illinois State University Digital Collections
- CARLI Digital Collections
- Any CONTENTdm-hosted institution (custom domains included)

Also accepted directly, no institution handler required:

- Direct IIIF manifest URLs (ending in `manifest.json` or `/manifest`)
- Share links from other IIIF viewers (Theseus, Mirador, Universal Viewer, and whatiiif itself)

Publishing IIIF and want your institution added? Get in touch through the [contact page](https://whatiiif.com/contact.html) or the [request form](https://tally.so/r/aQoOBE).

## Coming soon

### Sniiiffer, a faithful companion browser extension

**Sniiiffer** is whatiiif's faithful companion browser extension. It rides along quietly in your toolbar and sniffs out IIIF manifests on the pages you visit, so you can copy a manifest, open an item in whatiiif, or highlight a region without leaving the page you are on. More to come.

## How it is built

- **Front end.** A single self-contained `index.html` (no build step, no framework) served as a static page from GitHub Pages. [OpenSeadragon](https://openseadragon.github.io/) powers the deep-zoom viewer and is loaded only when a viewer is actually needed, so highlight landing pages stay fast.
- **Cloudflare Worker** ([whatiiif_Cloudflare_Worker.js](whatiiif_Cloudflare_Worker.js)). Provides two routes:
  - `/manifest-proxy`, a CORS-adding proxy for the handful of institutions whose manifests are not cross-origin friendly, and
  - `/embed`, the iframe-safe chromeless viewer used by embed codes.

  Most institutions are fetched directly from the browser; the proxy is used only where an institution's CORS or IP rules require it.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole application: viewer, region selection, highlight landing page, and embed view |
| `whatiiif_Cloudflare_Worker.js` | Cloudflare Worker for the `/manifest-proxy` and `/embed` routes |
| `contact.html` | Contact and about page |
| `terms.html` | Terms of use |
| `sitemap.xml`, `robots.txt` | Search-engine metadata |
| `favicon.png` | Site icon |

## Contact

Built and maintained by Nate Moore. Email nate@whatiiif.com, open an issue at [github.com/natemoo93/whatiiif](https://github.com/natemoo93/whatiiif), or use the [feedback form](https://tally.so/r/ZjgNDv) to report a misbehaving institution handler.
