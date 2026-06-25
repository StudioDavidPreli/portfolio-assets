# portfolio-assets

Source images, SVGs, and gifs for davidpreli.com. Like portfolio-Rive, this repo
is asset storage only. The portfolio build pulls these files and vendors them into
`src/assets`, so the deployed site serves fingerprinted copies from `/_astro/` with
explicit width and height. The browser never hotlinks back here or to
freight.cargo.site.

## What lives here

Static and animated media for the home-feed sections that are not Rive, Vimeo, or
p5. By category:

- SVG posters (for example MORE LOVERS `MoreLoversPoster.svg`, ALSO LOVERS
  `alsoLovers.svg`).
- Animated gifs, each paired with a webp first-frame still (see Naming).
- Single images and image sets, as webp.
- Gallery sets, as webp.

The per-section file inventory is recorded in `reference/nav-and-dropdowns.md` and
`reference/SITE-MAP.md` in the site repo, with the asset-url map in
`reference/capture-manifest.json`. Those are the index; this repo holds the files.

## How the site consumes these

- Images ship with explicit `width` and `height` so nothing reflows on load (the
  Core Web Vitals budget).
- Animated gifs hold a static frame under reduced motion. The build pairs each gif
  with its webp still, which serves as the reduced-motion poster.
- SVGs render as responsive images, static in both themes.
- Galleries become carousels that ship only the JS the carousel needs, with
  auto-advance disabled under reduced motion.

## Naming

A gif's webp still uses the exact gif stem plus a `Still` suffix (for example
`green2.gif` pairs with `green2Still.webp`). Keep that pairing intact so the build
can resolve a gif's poster by name.
