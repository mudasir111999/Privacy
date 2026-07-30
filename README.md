# Autofill Vault — site branding

Five pages, one mark. Every page now carries the monogram, a favicon, a
theme colour, and a social preview card.

## Where each file goes

**To the Privacy repo** (`mudasir111999.github.io/Privacy/`), alongside the
existing pages:

```
pricing.html      privacy.html      terms.html      contact.html
brand/            <- new folder, upload the whole thing
```

**To the licence admin host** (wherever `index.html` is served from today):

```
index.html
icons/            <- replaces the old icons folder
```

The admin console keeps its own `icons/` paths because it is served from a
different host than the Privacy repo. The inline SVG favicon works on both.

## What changed on every page

| | |
|---|---|
| **Logo** | The old two-shard mark is replaced with the monogram everywhere |
| **Favicon** | Inline SVG data URI (no extra request, scales cleanly) plus 16/32px PNG fallbacks |
| **Touch icon** | 180×180, full-bleed — iOS masks its own corners, so rounded corners here would show as black notches |
| **Theme colour** | `#f5f4ee`, so mobile browser chrome matches the page |
| **Titles** | Each page names itself: the three legal pages all said "Legal - Autofill Vault" before |

## What changed on the public pages only

- **Social preview** — `og:` and `twitter:` tags with a 1200×630 card. Links
  shared on WhatsApp, Facebook or LinkedIn now show the brand instead of a
  bare URL. This matters most for WhatsApp, which is how the licence key
  reaches customers.
- **Brand footer** — the monogram and wordmark above the existing legal note,
  so each page closes on the brand rather than trailing off.
- **The nav logo links somewhere.** It was `href="#"` on all four pages.

## What changed on the admin console only

- **`noindex, nofollow`.** A licence-admin login page should never appear in
  search results. It had no robots directive at all.

## Assets

```
brand/favicon.svg              master mark, scalable
brand/favicon-16.png           browsers that ignore SVG favicons
brand/favicon-32.png
brand/apple-touch-icon.png     180x180, full-bleed
brand/og-image.png             1200x630 social card
brand/og-image.svg             re-export this if you change the tagline
brand/apple-touch-icon.svg
```

`og-image.png` was rendered with a fallback serif. If you have Tiempos Text
licensed, re-export it from `og-image.svg` and the wordmark will match the
site exactly.

## Checking the social card

After uploading, paste a page URL into
`developers.facebook.com/tools/debug/` to force a re-scrape. WhatsApp and
LinkedIn cache aggressively, so previews can lag a few hours otherwise.
