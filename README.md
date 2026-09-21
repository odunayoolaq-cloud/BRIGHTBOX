# BRIGHTBOX ECOM — Landing Page

A static, single-page website for the BRIGHTBOX ECOM e-commerce mentorship brand.

## What's in this project

```
brightbox-ecom/
├── index.html              Main page (all sections, semantic HTML)
├── assets/
│   ├── css/style.css       All styling (dark luxury theme, responsive, animations)
│   └── js/script.js        Nav, mobile menu, carousel, FAQ accordion, form logic
└── README.md                This file
```

There are no build tools, frameworks, or package managers involved — this is
plain HTML/CSS/JS. You can open `index.html` directly in a browser, or deploy
the folder as-is to any static host.

## External dependency

The page loads **Google Fonts** (Fraunces + Inter) from
`fonts.googleapis.com` / `fonts.gstatic.com` via a `<link>` tag in the
`<head>` of `index.html`. This requires an internet connection at runtime,
which is standard for essentially all production websites. If you need a
fully offline-capable build, download the font files and self-host them,
then update the `<link>` tags and the `font-family` values in
`assets/css/style.css`.

No other external services, CDNs, or libraries are used — no jQuery, no
React, no analytics scripts. Nothing else to install.

## Deploying

Any static host works. A few common options:

**Netlify / Vercel (drag-and-drop or CLI)**
- Drag the `brightbox-ecom` folder into the Netlify or Vercel dashboard, or
- Run `netlify deploy` / `vercel` from inside this folder.

**GitHub Pages**
1. Push this folder to a GitHub repository.
2. In the repo settings, enable GitHub Pages and point it at the branch/root.

**Any traditional web host (cPanel, FTP, etc.)**
- Upload the contents of this folder to your `public_html` (or equivalent)
  directory, keeping the `assets/` folder structure intact.

## Before going live — required configuration

### 1. WhatsApp and email destinations
Open `assets/js/script.js` and find these two lines near the top of the
`submit` handler:

```js
var DESTINATION_WHATSAPP_NUMBER = '10000000000';
var DESTINATION_EMAIL = 'apply@brightboxecom.com';
```

Replace them with:
- The real WhatsApp number that should receive applications, in international
  format with no `+`, spaces, or dashes (e.g. `447911123456`).
- The real destination email address.

**Note on email delivery:** the form currently prepares a `mailto:` link as a
fallback. This opens the visitor's own email client — it does not silently
send an email from your server. For reliable, automatic email delivery
without relying on the visitor's device, connect the form to a backend
endpoint or a form service (e.g. your own server route, Formspree, Getform,
or similar), and POST the form data there instead. The `applyForm` submit
handler in `script.js` is the place to add that `fetch()` call.

### 2. Replace placeholder proof content
Every image slot in the Results carousel and the Sales Proof grid is a
clearly labeled placeholder (dark panel with "PLACEHOLDER — REPLACE WITH…"
text) — nothing fabricated is shown live. To swap in real proof:

- In `index.html`, find each `.slide-media` block (Results carousel) and
  `.proof-shot` block (Sales Proof grid).
- Replace the placeholder `<div class="placeholder-tag">…</div>` with an
  `<img src="assets/img/your-screenshot.jpg" alt="...">` tag, or set the
  placeholder div's background to your image via CSS.
- Create an `assets/img/` folder for your image files and reference them
  with relative paths (e.g. `assets/img/sale-01.jpg`).
- Update the caption text next to each proof item.

### 3. Replace placeholder statistics
In the "The Numbers Tell The Story" section of `index.html`, replace:

```html
$XX,XXX+   →  your verified total sales figure
XXX+       →  your verified order count
XX+        →  your verified stores-built count
XX+        →  your verified students/clients count
```

Only use figures you can verify — the design and copy are built around
transparency, not exaggerated claims.

### 4. Optional: favicon
No custom favicon is included. Add a `favicon.ico` (or `favicon.png`) file
to the project root and reference it in `index.html`'s `<head>`:

```html
<link rel="icon" href="favicon.ico">
```

## Accessibility & performance notes

- Semantic HTML throughout (`header`, `main`, `section`, `footer`, proper
  heading hierarchy with a single `<h1>`).
- Respects `prefers-reduced-motion`.
- No render-blocking scripts beyond the Google Fonts stylesheet.
- Form fields use native validation (`required`, `type="email"`, etc.).

## Support

This is a static hand-off project — there's no ongoing runtime dependency
on any particular platform. Any developer familiar with HTML/CSS/JS can
maintain or extend it.
