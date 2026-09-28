# kellyredding.com

The homepage. Static, no build step, no dependencies, no JavaScript.

```
~/kellyredding> make thing_
one builder. more than enough.
```

Served by GitHub Pages from this repository at **https://kellyredding.com**.

## Files

| | |
|---|---|
| `index.html` | The whole page — markup and CSS in one file |
| `404.html` | Not-found page, same voice |
| `CNAME` | Custom domain for GitHub Pages |
| `favicon.svg` | Chevron mark |
| `apple-touch-icon.png`, `icon-512.png` | Touch and app icons |
| `og-image.png` | 1200×630 social share card |
| `avatar.jpg` | 320×320, JPEG because it is a photograph |
| `fonts/*.woff2` | Roboto Mono, subset and self-hosted |
| `robots.txt`, `sitemap.xml` | Indexing |

**Around 37 KB on first paint**, and not a single third-party request.

## Notes

**Fonts are self-hosted and subset.** Roboto Mono is SIL Open Font Licensed,
so redistribution is permitted. Subsetting to printable ASCII takes the two
faces from 160 KB to 14 KB, and self-hosting removes two DNS lookups and two
TLS handshakes from the critical path — which on a page this small was most of
the load time.

**The chevron is a drawn path, never a typed character.** Roboto Mono has no
`❯` (U+276F); typing it falls back to whatever symbol font the visitor happens
to have, which differs on every machine. The geometry here matches the mark
files exactly.

**The chevron sits inside a grid item, not as one.** `vertical-align` has no
effect on grid items, so a bare `<svg>` child of the prompt grid has its offset
silently ignored and baseline alignment lifts it a quarter em. The wrapping
span is load-bearing.

**The typing loop is pure CSS.** Hidden nouns collapse to `width: 0` and so
occupy no space, which means exactly one is visible and the cursor trails it.
No script to fail, and `prefers-reduced-motion` is handled by a media query.

## Changing it

The design system — marks, tokens, the generators that produce them, and the
reasoning behind every decision — lives in a separate private repository. The
assets here are copies. Regenerate there, then copy across; do not edit an SVG
in place.

## Deploying

Push to `main`. GitHub Pages publishes from the repository root.
