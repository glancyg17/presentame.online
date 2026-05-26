# presentame.online

Static site for [presentame.](https://presentame.online) — professional websites for small businesses, from £50.

Hosted on **GitHub Pages**.

---

## Repo structure

```
presentame-online/
├── index.html       # Main site (SEO + Schema.org + Open Graph)
├── 404.html         # Custom not-found page
├── sitemap.xml      # XML sitemap for search engines
├── robots.txt       # Crawler directives
├── llms.txt         # AI/LLM discoverability (GEO optimisation)
├── .gitignore
└── README.md
```

## Deployment

This site deploys automatically via **GitHub Pages**.

1. Push to `main` branch.
2. In repo settings → **Pages** → set source to `main` / `root`.
3. Add a custom domain (`presentame.online`) in the Pages settings and update your DNS:
   - `A` records pointing to GitHub Pages IPs, **or**
   - `CNAME` record: `www` → `<your-github-username>.github.io`

GitHub will provision an SSL certificate automatically once DNS propagates.

## Contact form

The contact form uses [FormSubmit](https://formsubmit.co) — no backend required. The `action` URL in `index.html` sends submissions directly to `hello@presentame.online`. First submission requires a one-time email confirmation from FormSubmit.

## SEO checklist

- [x] `<title>` and `<meta name="description">`
- [x] Canonical URL
- [x] Open Graph tags
- [x] Twitter Card tags
- [x] Schema.org `ProfessionalService` + `WebSite` JSON-LD
- [x] `sitemap.xml` referenced in `robots.txt`
- [x] `llms.txt` for AI/GEO discoverability
- [x] Semantic HTML (`<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`)
- [x] `aria-label` and `role` attributes
- [x] Mobile-first responsive design

## Updating content

All content is in `index.html`. Pricing, services, and copy can be edited directly. No build step required.

---

&copy; presentame. — hello@presentame.online
