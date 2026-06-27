# Whatiiif

A lightweight tool for creating shareable deep links to specific regions of digitized documents in any IIIF-compliant collection.

## The problem

IIIF (International Image Interoperability Framework) has made digitized primary sources accessible across thousands of institutional repositories. But sharing a precise reference to something specific like a name in a census, a passage in a manuscript, an entry in a travel log, still means either sending a vague "it's on page 6 somewhere" or hoping your viewer's URL updates as you navigate.

Whatiiif closes that gap. Paste a JSON manifest or a page URL from a supported institution, draw a box around what you want to share, and get a permanent link that shows anyone exactly what you're pointing at. No viewer software required.

## How it works

- Accepts page URLs from supported a growing list of platforms (CONTENTdm, Internet Archive, Library of Congress) or direct IIIF manifest URLs
- Detects the platform and resolves the IIIF manifest automatically
- Loads the document in a zoomable viewer powered by OpenSeadragon
- Lets you drag a selection box over any region of any page
- Generates a shareable URL that renders the cropped region alongside its full-page context, visible to anyone in a standard browser

## Who it's for

Researchers citing specific content in digitized primary sources, digital humanities scholars, librarians, archivists, and anyone who has ever tried to point a colleague at something specific in a 300-page scan.

## Self-host

whatiiif is a single static HTML file with no backend dependencies. Download `index.html` and serve it from anywhere.

## Built with

- [OpenSeadragon](https://openseadragon.github.io/) for zoomable image rendering
- [IIIF Presentation API](https://iiif.io/api/presentation/) 2 and 3
- [IIIF Image API](https://iiif.io/api/image/) for server-side region cropping

## Coming soon

- **Sniiiffer** a browser extension for detecting IIIF manifests on any page, for institutions whose URLs don't follow a predictable pattern

## License

MIT
