# 875 Meade Ave

Single-page listing site for a top-floor home in Bayview Heights, San Francisco. 3 bed, 2 bath, 1,200 sq ft, offered at $800,000.

## Running it

No build step, no dependencies. Open `index.html`, or serve the folder:

```
python3 -m http.server 8000
```

## Structure

```
index.html      the whole page: markup, styles, and scripts inline
404.html        not-found page (GitHub Pages and Vercel both pick this up automatically)
robots.txt      crawler directives + sitemap pointer
sitemap.xml     single-URL sitemap with image entries
photos/         full-resolution photography (1600px long edge) — hero slides and lightbox
photos/sm/      900px versions — gallery grid tiles
photos/xs/      260px versions — hero thumbnail rail
README.md
.gitignore
.github/workflows/pages.yml   optional GitHub Pages deploy on push to main
```

Gallery tiles point at `photos/sm/` and carry a `data-full` attribute; the lightbox reads it to load the full-resolution file on demand. If you add a photo, generate all three sizes and keep the filename identical across folders.

## Deploying

Any static host works — there is nothing to build.

**Vercel (current target: https://bayview-heights.vercel.app/):** import the repo, leave framework preset as "Other", leave build command and output directory empty. Every push to `main` redeploys.

**GitHub Pages:** `.github/workflows/pages.yml` deploys on push to `main` — enable it under Settings → Pages → Source: GitHub Actions. Or skip the workflow and use Settings → Pages → deploy from branch, `main` / root.

## Photos

Every photo ships at two widths: `photos/<name>.jpg` (1600px, used by the lightbox) and `photos/sm/<name>.jpg` (900px, used by the page). `photos/xs/` holds the five 640px hero thumbnails. All are JPEG at quality 0.82. Raw originals live in `uploads/`, which is gitignored.

## Devices

The layout is fluid with breakpoints at 1080, 980, 880, 680, 560 and 420px, plus a landscape-phone case for short viewports. Hero slides ship `srcset` (900px on phones and tablets, 1600px on desktop) and the LCP image is preloaded with a matching `imagesrcset`. Safe-area insets keep content clear of notches; hover-only effects are disabled on touch devices; `prefers-reduced-motion` turns off the Ken Burns pan and reveal transitions.

## SEO

The page carries a descriptive title and meta description, canonical and Open Graph/Twitter tags, geo meta, and JSON-LD structured data (`SingleFamilyResidence` + `RealEstateListing` with price, agent, and coordinates).

Absolute URLs point at `bayview-heights.vercel.app`. If the site moves to a custom domain, find-and-replace that host in `index.html` (canonical, `og:url`, `og:image`, `twitter:image`, JSON-LD), `robots.txt` and `sitemap.xml` — absolute image URLs are required for link previews to render — and bump `<lastmod>` in `sitemap.xml`.

After launch, submit `sitemap.xml` in Google Search Console and validate the structured data with the Rich Results Test.

## Before publishing

- Confirm the listing status label in the hero ("Coming soon").
- Confirm the license number and contact details in the schedule and footer sections.
- Year built reads 1992 on the page; the Trulia record for this address says 1994. Confirm which is correct.
- The neighborhood image links to candlesticksf.com; confirm that's still the right destination.
