# preséntame. — Website Repo

Static site for **presentame.online** (Mexico / LatAm market). Hosted on GitHub Pages, no build step — just plain HTML/CSS/JS files served directly. This is the Spanish-language sister site to getpresented.co.uk (UK) — same brand system, same design, localized content and MXN pricing.

## File structure

```
presentame.online/
├── index.html                        ← Homepage
├── get-started/
│   └── index.html                    ← Persuasion page (ad lands here)
│   └── details/
│       └── index.html                ← Intake form
├── thank-you-enquiry/
│   └── index.html                    ← Post-form confirmation
├── payment-confirmed/
│   └── index.html                    ← Post-payment confirmation
├── privacy-policy/
│   └── index.html                    ← Aviso de privacidad (Mexican LFPDPPP)
├── solutions/
│   └── index.html                    ← Bespoke systems page
├── 404.html                          ← Branded error page
├── sitemap.xml
├── robots.txt                        ← Allows all crawlers incl. AI bots
├── llms.txt                          ← AI-readable business summary (Spanish)
├── CNAME                             ← presentame.online
├── README.md
├── .gitignore
└── assets/
    ├── icons/
    │   └── favicon.png               ← rust dot on ink square — shared with UK brand, no text
    └── images/
        ├── og-image.jpg              ← 1200×630px — preséntame. wordmark
        ├── logo.png                  ← preséntame. wordmark, unused in HTML — for email/proposals
        ├── kennedy.jpg               ← Portfolio carousel (shared with UK site)
        ├── ekvanmobile.jpeg          ← Portfolio carousel (shared with UK site)
        ├── casamayis.jpeg            ← Portfolio carousel
        └── mayatuya.jpeg             ← Portfolio carousel
```

Extensionless URLs — every page is a folder with `index.html`. GitHub Pages serves these natively, no config needed.

## Brand basics

| Token | Value |
|---|---|
| Paper (background) | `#F7F3EC` |
| Ink (text) | `#211D17` |
| Rust (primary accent) | `#B5542E` |
| Rust dark (shadows/borders) | `#9A4423` |
| Green (success/secondary) | `#3D7A5C` |
| Line/border | `#D8CFBC` |
| Card | `#FAFAF8` |

**Fonts:** Fraunces (display/headings), Inter (body/UI), Space Mono (prices, labels, small caps), Caveat (handwritten accents, used sparingly).

**Wordmark:** lowercase throughout — `preséntame.` — with the trailing period in rust (`#B5542E`).

## Making content edits

Each page is a single self-contained HTML file — CSS and JS are inline at the top/bottom of the file, no build step required. All copy is in Spanish. To edit copy, prices, or contact details:

1. Open the relevant `index.html` file
2. Find the text directly in the markup (search for the visible Spanish text, not a class name)
3. Edit and save
4. Commit and push to `main` — GitHub Pages rebuilds automatically, live in ~2 minutes

## Forms

The intake form (`get-started/details/index.html`) submits to **FormSubmit.co** at `hola@presentame.online`. FormSubmit requires a one-time confirmation click the first time it receives a real submission — check the inbox after the first live test.

Field names sent to your inbox are set via `name="..."` attributes on each input — keep these human-readable, since they become the email's field labels.

## Payments (Stripe, MXN)

| Product | Price | Payment link |
|---|---|---|
| Sitio Web + Hosting (bundle) | $500 MXN + $100 MXN/mes desde día 30 | https://buy.stripe.com/8x27sK1Xs5UHbVOeeS9EI0d |
| Sitio Web (solo construcción) | $500 MXN | https://buy.stripe.com/28E5kCgSm3Mz3pi8Uy9EI0e |
| Hosting y Mantenimiento (independiente) | $100 MXN/mes | https://buy.stripe.com/6oU4gy6dIerd4tm6Mq9EI0f |
| Transferencia de Dominio | $170 MXN | https://buy.stripe.com/bJecN4atYdn92le6Mq9EI0g |

All links redirect to `/payment-confirmed/` after payment, matching the UK bundle model (card saved at checkout, hosting auto-starts day 30).

## Known placeholders to replace before launch

- [ ] `assets/images/og-image.jpg` — generated with a system serif font as a stand-in for Fraunces; redo in Canva for a pixel-accurate match to the UK version
- [ ] `assets/images/logo.png` — same placeholder situation as og-image
- [x] **WhatsApp**: +52 981 108 6380 is now live across the site (homepage talk-strip, "beyond the website" CTA, solutions page final CTA).
- [ ] Portfolio carousel on the homepage is identical to the UK site (same 4 businesses, English quotes, untranslated per instruction) — swap in MX-specific client sites here as you build more.
- [ ] Meta Pixel ID is currently the same as the UK site (`866982179477687`) — same Ads Manager account. Fine to share if you're tracking both markets in one place; split it out if you want MX-only ad attribution.

## Deploy checklist

Same as the UK repo's SOP — DNS is already handled via Cloudflare (per your setup), and this repo replaces the files in your existing GitHub Pages repo. After upload: activate FormSubmit (submit a real test), submit to Google Search Console, and check `/sitemap.xml`, `/robots.txt`, `/llms.txt` are reachable at presentame.online.
