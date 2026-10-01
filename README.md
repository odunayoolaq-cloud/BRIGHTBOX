# Brightbox Custom Theme — Sales Website

A single-page, self-contained marketing site for the "Brightbox Custom Theme" Shopify theme product.

## What's in this project

```
brightbox-website/
├── index.html   ← the entire website (HTML, CSS, and JS in one file)
└── README.md    ← this file
```

That's it. There is no build step, no package manager, and no framework — `index.html` is the whole site.

## Dependencies

The page only loads two things from outside the file, both from Google Fonts:

- `https://fonts.googleapis.com/css2?family=Fraunces...&family=Inter...`
- The underlying font files from `https://fonts.gstatic.com`

Everything else — layout, colors, buttons, the FAQ accordion, the license price selector, the mobile menu — is plain HTML/CSS/vanilla JavaScript inside `index.html`. There are no npm packages, no CDNs for JS libraries, and no server-side code, so there is nothing else to install.

If you need the site to work with zero external requests (e.g. a fully offline/air-gapped environment), download the two font files from Google Fonts, place them in a `fonts/` folder next to `index.html`, and swap the `<link>` tags in `<head>` for a local `@font-face` rule. This isn't necessary for normal web hosting.

## Deploying it

Because it's a static file, you can host it almost anywhere:

- **Netlify / Vercel / Cloudflare Pages**: drag-and-drop the `brightbox-website` folder (or connect a git repo containing it) — no build command needed.
- **GitHub Pages**: push this folder to a repo and enable Pages, pointing at the root.
- **Any static host / S3 bucket / shared hosting**: upload `index.html` to the web root so it's served at `/`.

## Before you launch — content to replace

The page ships with clearly-marked placeholder content. Search `index.html` for these before going live:

| What | Where | Look for |
|---|---|---|
| Screenshots / mockups | Hero, purchase gallery | `.mock` blocks and the `[Admin: replace with real store screenshots]` note |
| Pricing | Purchase section | `id="priceOut"`, the `data-price` attributes on `.lic` license cards, and the compare-at price |
| Cost comparison figures | "Stop renting your store" section | `$XX/mo` and `$XXX+ / year` placeholders |
| Refund policy | FAQ | `[Admin: insert your actual refund policy here before launch.]` |
| Testimonials, demo store links, video embed, changelog | Not included in this build — see note below | — |
| Checkout links | `Get Instant Access` / `Get Brightbox...` buttons | currently `href="#"` or `#buy` — point these at your real checkout |
| Legal pages, social links | Footer | currently placeholder `#` links |

## Known gaps from the original brief

This build focuses on the core conversion path (hero → proof → features → problem/solution → pricing → FAQ → final CTA) to keep the file lean and dependency-free. Not included, and safe to add as separate sections later:

- Embedded video / "See Brightbox in Action" player
- Demo store showcase carousel
- Advanced cart drawer visual showcase
- Full product-page block library and 50+ section library grids
- Pre-lander/advertorial preview cards
- Testimonials and "Built with Brightbox" results grid
- Version/changelog module

Let me know if you'd like any of these built out — each can be added as its own `<section>` following the same CSS classes already defined in `index.html` (`.card`, `.sec-head`, `.grid`, etc.), so the visual style stays consistent.
