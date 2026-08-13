# 875 Meade Ave

Single-page listing site for a top-floor home in Bayview Heights, San Francisco. 3 bed, 2 bath, 1,200 sq ft, offered at $900,000.

## Running it

No build step, no dependencies. Open `index.html`, or serve the folder:

```
python3 -m http.server 8000
```

## Structure

```
index.html      the whole page: markup, styles, and scripts inline
robots.txt      crawler directives + sitemap pointer
sitemap.xml     single-URL sitemap with image entries
photos/         full-resolution photography (1600px long edge) — hero slides and lightbox
photos/sm/      900px versions — gallery grid tiles
photos/xs/      260px versions — hero thumbnail rail
README.md
.gitignore
```

Gallery tiles point at `photos/sm/` and carry a `data-full` attribute; the lightbox reads it to load the full-resolution file on demand. If you add a photo, generate all three sizes and keep the filename identical across folders.

## Deploying

Any static host works. For GitHub Pages: push to `main`, then Settings → Pages → deploy from branch, `main` / root.

## SEO

The page carries a descriptive title and meta description, canonical and Open Graph/Twitter tags, geo meta, and JSON-LD structured data (`SingleFamilyResidence` + `RealEstateListing` with price, agent, and coordinates).

**One find-and-replace before launch:** every absolute URL uses the placeholder domain `875meade.example`. Swap it for the real domain in `index.html` (canonical, `og:url`, `og:image`, `twitter:image`, and the JSON-LD block), `robots.txt`, and `sitemap.xml`. Absolute image URLs are required for link previews to render.

After launch, submit `sitemap.xml` in Google Search Console and validate the structured data with the Rich Results Test.

## Before publishing

- Replace the placeholder domain (see SEO above).
- Confirm the listing status label in the hero ("Coming soon").
- Confirm the license number and contact details in the schedule and footer sections.
- Year built reads 1992 on the page; the Trulia record for this address says 1994. Confirm which is correct.
