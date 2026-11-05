# preséntame. (MX) — working codex

*Living document. Last updated: 5 November 2026.*
**Rule: if reality changes (a price, a link, a page, a decision), update this file in the same commit.** Read it before working on this repo.

> **Public-repo warning.** This repo is public and `_config.yml` only hides this file from the *published site*, not from GitHub. Keep anything private out of it: internal pricing strategy, ad budgets and targeting, revenue goals, client personal data, API keys. Private strategy lives in the Claude Project's codex.

---

## 1. What this is

**preséntame.** is the Mexico/LATAM brand of the same solo business as **getPresented.** (UK), run by **Glancy** from Campeche. Simple, fast, fairly priced websites for small local businesses, plus branding add-ons. Promise: **a website you never have to touch, run by a real person you can message.** This repo is the MX marketing and sales site (presentame.online), static HTML on GitHub Pages, no build step. It is the Spanish, MXN sister of the UK repo (`getpresented.co.uk`); structure, design and flows match, copy and prices are localised.

- Language: Mexican Spanish, **tú form**, plain and direct. Tagline on the site: *"Tu negocio, en línea. Como se debe."*
- Email on the site: `hola@presentame.online`
- WhatsApp: +52 981 108 6380 (`https://wa.me/529811086380`). Also the **edit line** for clients.
- Funnel difference from UK: Mexico is **WhatsApp-first** (click-to-WhatsApp ads open a chat, no website step). The website is still used for credibility, the intake form and the checkout confirmations.

## 2. Products and pricing (MXN)

### Billing mechanics (verified in Stripe, Oct 2026)
Every site bundle is **one-off build fee + monthly hosting, with the first month taken at checkout.** **First payment = build fee + first month**, then the monthly from month 2. **No free month, no 30-day trial.** Don't write "primeros 30 días gratis" or "desde el día 30" anywhere. (The older $100 hosting price in Stripe carries a stale `trial_period_days: 30` flag that checkout ignores.)

### Sites and plans
| Product | Build | Monthly | First payment | Link |
|---|---|---|---|---|
| Sitio Web + Hosting (**Live**) | $500 | $150 | **$650** | https://buy.stripe.com/8x2fZgfOi0An1hab2G9EI0q |
| Sitio Web + Fresh | $500 | $300 | **$800** | https://buy.stripe.com/8x26oG7hMfvhgc49YC9EI0r |
| Sitio Web (solo construcción) | $500 | — | $500 | https://buy.stripe.com/28E5kCgSm3Mz3pi8Uy9EI0e |
| Hosting y Mantenimiento (Live, independiente) | — | $150 | $150 | https://buy.stripe.com/7sY6oG59Ecj55xq7Qu9EI0s |
| **Upgrade a Fresh** | — | $300 | $300 | https://buy.stripe.com/4gMcN49pUerde3WdaO9EI0t |
| Transferencia de Dominio | $170 | — | $170 | https://buy.stripe.com/bJecN4atYdn92le6Mq9EI0g |

| Plan | Price | Includes |
|---|---|---|
| **Live** | $150 MXN/mes | Hosting, dominio, **2 cambios al mes por mensaje**, cancela cuando quieras |
| **Fresh** | $300 MXN/mes | Todo lo de Live, **cambios cotidianos ilimitados por mensaje**, un **mensaje mensual "cómo le fue a tu sitio"** (visitas y búsquedas en Google), **avisos antes de temporadas fuertes**, **revisión anual** más renovación de volante/tarjeta/menú |

Fresh tagline on the site: *"Lo vigilamos por ti: cambios, resultados y un aviso cuando algo necesite actualizarse."* Fresh is "we keep an eye on it for you", not just more edits. What is actually delivered and how: `docs/fresh-service.md`.
A **"cambio"** = one request (one topic). Process and fair use: `docs/edit-workflow.md`.
Legacy: the original $100/mes hosting link and bundle link were **deactivated in Oct 2026** (existing subscribers keep their subscriptions and price until Glancy decides otherwise). The build-only and domain-transfer links are unchanged but now redirect to their own confirmation pages.

### Branding (fixed prices, on `/branding/`)
| Product | Price | Contents |
|---|---|---|
| Identidad Inicial | $500 | Logotipo, paleta, tipografía, favicon, tarjeta de presentación |
| Identidad Social | $500 | Recursos WhatsApp Business, firma de correo, imágenes/portadas para redes, volante, QR |
| Identidad Completa | $750 | Inicial + Social |
| Diseño de Menú | $350 | Menú listo para imprimir |

Buttons read "Quiero la Identidad Inicial / Social / Completa" and "Quiero el Diseño de Menú" (no price on the button; the price sits on the card). They go straight to Stripe. Links: Inicial https://buy.stripe.com/6oU5kCcC682PcZS7Qu9EI0u · Social https://buy.stripe.com/6oU9AS31w0An6Bu4Ei9EI0v · Completa https://buy.stripe.com/aFafZg9pU5UH8JC8Uy9EI0w · Menú https://buy.stripe.com/aFaeVcfOi2Iv2leeeS9EI0x

### Site + branding bundles (hosting included; sold via WhatsApp "Pregúntanos", not a buy button)
| Bundle | Build | First payment | Then |
|---|---|---|---|
| Sitio + Identidad Inicial | $750 | $900 | $150/mes |
| Sitio + Identidad Social | $750 | $900 | $150/mes |
| **Como Se Debe** (sitio + identidad completa) | $990 | $1,140 | $150/mes, **incluye los primeros 3 meses de servicio nivel Fresh** |

Como Se Debe's Fresh months are a **service perk, not a billing change**: the client pays $150/mes throughout and gets unlimited everyday changes for 3 months; offer the $300 upgrade at the end. Bundle links (send in chat): Inicial https://buy.stripe.com/00w3cueKedn95xqfiW9EI0y · Social https://buy.stripe.com/dRmdR89pUaaX0d6daO9EI0z · Como Se Debe https://buy.stripe.com/14A6oG45A3Mzf804Ei9EI0A

### Pricing messaging rules
- Lead with the bundle: *"$500 para construirlo, luego $150 al mes."*
- Primary CTAs use benefit language ("Crear mi sitio", "Quiero la Identidad Inicial"); no prices on buttons.
- **Public pages talk price, not payment.** No "comprar ahora", "paga y te contactamos", "sin conversación", first-payment ($650/$800) or checkout wording on public pages or `llms.txt`. Payment small print lives only at the point of payment: Stripe checkout and the `/payment-confirmed/` pages. The pricing section ends with small print instead of a price card: *"Construcción desde $500 MXN; los sitios complejos o de varias páginas pueden cotizarse aparte."*
- Ads say **"desde $500"**.
- **Do not publish** "el precio nunca sube", "precio congelado" or any promise restricting future price rises. **Do not publish** a response-time promise until one is decided (see edit-workflow §2).

## 3. Client flow (MX)

```
Meta ad (Leads, conversion location = WhatsApp) → opens WhatsApp with a pre-filled message
→ auto-greeting + 3 quick-reply buttons → natural conversation, Glancy qualifies
→ Stripe link sent in chat → /payment-confirmed/<product>/
→ build → handover message → client uses WhatsApp for changes
```
The site also serves people who arrive without an ad: `/get-started` → `/get-started/details` (FormSubmit) → `/thank-you-enquiry` → WhatsApp conversation → Stripe link. The branding "Quiero…" buttons and the homepage "Crear mi sitio con Fresh" button go straight to checkout and collect details on the confirmation page. Clients send logo/photos by WhatsApp or email; there is no upload form.

## 4. Repo map

```
index.html                 Home: hero demo, shuffled work gallery (8 sites incl. Casa Mayis, MX-only), "Mándanos un mensaje" chat demo, plans, process, branding teaser, solutions teaser
branding/index.html        Identidades y menú (botones "Quiero…" a Stripe) + paquetes con sitio (preguntar por WhatsApp)
get-started/index.html     Persuasion page (ad/WhatsApp landing)
get-started/details/       Intake form (FormSubmit)
thank-you-enquiry/         Fires Lead
solutions/                 Bespoke software page
privacy-policy/            Aviso de privacidad (LFPDPPP). Discloses Meta Pixel and WhatsApp photos/voice notes for edits (add Umami / Cloudflare Web Analytics text if installed)
terms/                     Términos del servicio (plain Spanish; NOT lawyer-reviewed, see §8)
payment-confirmed/<slug>/  One page per Stripe link (§6). /payment-confirmed/index.html is the generic fallback
404.html · sitemap.xml · robots.txt · llms.txt · CNAME · _config.yml
assets/icons/ assets/images/   (gallery, 940x788 top crops: orbitvision, rfstrategic, kennedy, mayatuya, steviemacs, ekvan, ldconstruction, casamayis; plus og-image, logo; branding collages brand-full, brand-starter, brand-social (each with a `-640` variant) and brand-menu (`-560` variant), localised to preséntame. and MXN. Gallery screenshots are the real client sites and stay in their own language.)
docs/                      edit-workflow.md, fresh-service.md, client-site-CLAUDE-template.md
```
Each page is self-contained (inline CSS/JS): shared CSS/JS (burger menu, gallery) is duplicated per page, so change every page. A burger menu (mobile) / inline links (desktop) is on home, branding, solutions, privacy, terms and 404; funnel pages (get-started, details, thank-you, confirmations) stay minimal. Edit visible copy directly. Push to `main` → live in ~2 minutes.

## 5. Design system

Same tokens and fonts as the UK site: Paper `#F7F3EC`, Ink `#211D17`, Rust `#B5542E` (accent, CTAs, the dot), Rust Dark `#9A4423`, Green `#3D7A5C`, Line `#D8CFBC`, Card `#FAFAF8`, Soft `#5C5648`. Fonts: Fraunces (headings), Inter (body), Space Mono (labels/prices), Caveat (handwritten, sparingly). Wordmark `preséntame.` in Fraunces Bold with a rust dot, **with the accent on the é everywhere except URLs/domains**. Sentence case, no hype. Mobile-first; motion respects `prefers-reduced-motion`.

## 6. Tracking (do not break)

- **Meta Pixel** (MX dataset `1597034095279542`, "preséntame MX Pixel") loads only after consent via the `#fp-consent` banner (Aceptar/Rechazar), stored in `localStorage` key `fp_ad_consent`. The block is copied verbatim into every page; **never edit it, and include it on every new page.** The MX Pixel dataset is **separate from the UK one**; never cross-wire when cloning from the UK repo.
- Events: `PageView` (all pages) · `Lead` (thank-you page load, WhatsApp button `onclick`) · `InitiateCheckout` (branding buy buttons, homepage Fresh button) · `Purchase` (confirmation pages, value = **actual first payment**, currency MXN).

| Confirmation page | Purchase value |
|---|---|
| `/payment-confirmed/` (generic) · `simple-website` | $500 |
| `site-hosting` (Live) | $650 |
| `site-fresh` | $800 |
| `fresh` (upgrade) | $300 |
| `hosting` | $150 |
| `starter-identity` · `social-identity` | $500 |
| `full-identity` | $750 |
| `menu-design` | $350 |
| `site-starter-identity` · `site-social-identity` | $900 |
| `como-se-debe` | $1,140 |
| `domain-transfer` | $170 |

Confirmation pages are `noindex`. When a Stripe link is created or re-priced, create/update its confirmation page and Purchase value.
- **Client-site analytics for the Fresh monthly message**: Cloudflare Web Analytics + Google Search Console (see `docs/fresh-service.md`).
- **Umami**: not installed on MX yet (deferred until there is traffic); the privacy policy deliberately does not mention it. When added: its **own MX website ID** (never the UK one) in `<head>` of every page: `<script defer src="https://cloud.umami.is/script.js" data-website-id="<MX ID>" data-domains="presentame.online"></script>`, plus the policy text.

## 7. Working rules for Claude in this repo

1. **Preserve** the consent/Pixel block, WhatsApp `onclick` Lead handlers, meta tags and Stripe links unless the task says otherwise.
2. After any pricing change, grep the repo for the old number: homepage, get-started, branding, `llms.txt`, confirmation pages, meta descriptions, this file.
3. Never write "primeros 30 días gratis", "desde el día 30" or "el precio nunca sube".
4. New product → new Stripe link, new `/payment-confirmed/<slug>/` page, correct Purchase value, entry in §2 and §6. Copy payment URLs from Stripe or this file, never from memory.
5. Spanish copy: tú form, short sentences, no calques from English. Keep Live/Fresh as plan names.
6. Don't copy UK pages in without translating, and **never carry over the UK Pixel ID, UK Umami ID, UK WhatsApp number or UK Stripe links.** After copying anything from the UK repo, check every `buy.stripe.com/...` id against §2 (the UK branding links nearly shipped once).
7. Check `<div>` balance, anchors and mobile width after edits.
8. Client edit requests follow `docs/edit-workflow.md`.
9. The gallery shuffles on every load and auto-cycles; dots are generated by JS, so adding a card needs no dot edit. Each card's quote is marked in a comment (`TEMP quote` or real review).
10. **Estilo de redacción:** que suene como una persona hablando, no como un folleto. **Sin rayas largas (—)** en el texto del sitio (usa punto, coma, dos puntos o paréntesis). Los títulos de página usan ` | ` como separador. Evita las construcciones del tipo "no es X, es Y", las listas de tres tan ordenadas y frases de relleno. Frases cortas, palabras sencillas, di lo que pasa.

## 8. Open items

- [ ] **Términos del servicio (`/terms/`) are a draft, not lawyer-reviewed.** Decide governing law/courts (currently *leyes de México, tribunales de Campeche*, marked `DECISIÓN PENDIENTE` in the HTML), add the supplier's name and address, confirm IVA treatment of prices, then in Stripe set the Terms of service URL to `https://presentame.online/terms/` and require acceptance on payment links.
- [ ] **Quotes in the gallery.** All are placeholders or translated temporary wording except L.D Construction, which is a real Google review translated to Spanish (it keeps "getPresented" as the client wrote it). Replace the rest with real Google reviews as they arrive; get client OK for Orbit Vision, RF Strategic and Stevie Macs wording. Descriptors for those three are guesses.
- [ ] **Fresh monthly message:** before the first Fresh client reaches month 2, set up Cloudflare Web Analytics + Search Console per client site, finish the Spanish templates in `docs/fresh-service.md`, and test one end to end. The site already promises it. Add Cloudflare Web Analytics / Search Console to the privacy policy when it goes live.
- [ ] **Umami (deferred until there is traffic):** when adding it, create an MX website in Umami (never reuse the UK ID; the free plan may not allow a second site), add the tag (§6) and re-add the Umami paragraphs to the privacy policy.
- [ ] **Response-time promise** for message edits, then add to the site and Terms (the Terms currently promise none).
- [ ] **OXXO / bank transfer** for recurring hosting: many MX owners don't pay by card online. Verify Stripe options and decide how non-card clients pay monthly.
- [ ] Decide what happens to any existing $100/mes subscribers.
- [ ] Update the click-to-WhatsApp ad copy and quick replies if they mention $100/mes.
- [ ] Privacy policy: confirm the WhatsApp-content retention wording matches practice.
- [ ] Maya Tuya gallery screenshot is the English view of a bilingual site; replace with the Spanish view if desired.
- [ ] Gallery card for Kennedy is `kennedyexecutivetravel.co.uk` (was `.com`): verify it is live. Update any old links/QRs.
- [ ] MX OG image tagline uses a fallback mono font; regenerate with Space Mono if desired.
- [ ] Clean up the stale 30-day trial flag on the $100 hosting price in Stripe (create a new price, don't edit).

## 9. Decisions log (newest first)

- **5 Nov 2026**: MX site brought to the UK 26 Oct standard: burger menu, 8-site shuffled gallery (Casa Mayis MX-only), Fresh redefined (monthly message, seasonal avisos, annual check-up), pricing card replaced by small print, payment wording removed from public pages ("price yes, payment no"), branding buttons renamed "Quiero…", Términos del servicio added, privacy notice updated for WhatsApp edit content, branding collages and OG image localised to preséntame./MXN.
- **24 Oct 2026**: Pixel dataset confirmed in Events Manager as `1597034095279542` (the repo previously used a different ID; fixed on every page). `hola@presentame.online` confirmed as the working mailbox. Umami deferred on MX until there is traffic; Umami removed from the privacy policy to match.
- **24 Oct 2026**: MX site brought in line with the UK site: edit-by-message positioning, Live/Fresh plans, branding catalogue and bundles, per-product confirmation pages, docs, this file.
- **24 Oct 2026**: MX prices set: Live **$150/mes** (was $100), Fresh **$300/mes**; build stays **$500**; first payment = build + first month. Branding and bundles priced for the MX market ($500/$500/$750/$350; bundles $750/$750/$990). Flagship bundle named **Como Se Debe** (echo of the tagline); includes 3 months of Fresh-level service.
- **Aug 2026**: Site moved from presentame.digital to presentame.online; conversion destination for ads = WhatsApp (not Website); chat quick-reply buttons instead of a Flow form.
