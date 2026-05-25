# 875 Meade Ave — Bayview Heights, San Francisco

A dark-mode real estate listing website for **875 Meade Avenue, San Francisco, CA 94124**.

## About the property

3 bed / 2 bath top-floor condo in Bayview Heights. Newly remodeled, 1,300 sq ft, panoramic views of the SF skyline, Bay Bridge, and East Bay hills. Built 1994. Listed at $875,000.

## About this site

Single-page static HTML site — no build step, no dependencies. Open `index.html` in a browser or serve with any static file server.

**Sections:**
- Hero with auto-rotating photo carousel
- Overview and property spec sheet
- Full photo gallery (16 images)
- Features grid
- Neighborhood section (Candlestick Point development, SF AI market)
- Schedule / agent contact card

**Design:** Sotheby's International Realty brand palette — navy `#002349`, warm cream `#f4f1ea`. Cormorant Garamond serif + Libre Franklin sans-serif.

## File structure

```
index.html          — the website (single file)
photos/             — optimized property photos used by the site
uploads/            — original uploaded photos
sf-home-website/
  project/          — duplicate of root (design handoff bundle)
  chats/            — original design brief and build transcript
```

## Running locally

```bash
python3 -m http.server 3000
# then open http://localhost:3000
```
