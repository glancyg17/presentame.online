# Cloudflare migration (presentame.online)

**Status: prepared, NOT live.** The site is still served by GitHub Pages. Nothing below changes live traffic until step 5.

## What was added to the repo
| File | What it does |
|---|---|
| `wrangler.jsonc` | Declares a static-assets-only Worker named `presentame-online`: serve this folder, custom 404 page, folder pages with a trailing slash (same as GitHub Pages). **No custom domain is set on purpose** (see step 5). |
| `.assetsignore` | Keeps repo-only files off the public site: `CLAUDE.md`, `README.md`, `docs/`, `_config.yml`, `CNAME`, `.git`, and the config files themselves. Replaces what `_config.yml` `exclude` did on GitHub Pages. |
| `_headers` | Security headers on every page (`nosniff`, referrer policy, same-origin framing, permissions policy), a 1-hour cache on `/assets/*`, and `noindex` on the `*.workers.dev` address. Cloudflare reads this file and does not serve it. |

## Tested locally (Wrangler 4.158, `wrangler dev`)
- Every page loads; `/terms` redirects to `/terms/` (and likewise for the other folder pages); unknown URLs return the custom 404 page with status 404.
- `CLAUDE.md`, `README.md`, `docs/`, `wrangler.jsonc`, `_headers`, `.assetsignore`, `_config.yml`, `CNAME` and `.git` all return 404 (not published).
- Security headers are present on `/`; `/assets/*` gets the 1-hour cache.
- **Not tested:** a real deploy, Workers Builds from a private repo, DNS, certificates, Meta Pixel events and Stripe return pages on the new host. Do these in steps 1 to 2 and 6.

## Cutover steps
1. **Connect the repo (no live impact).** Cloudflare dashboard > Workers & Pages > Create > Import a repository (GitHub) > this repo. Worker name must match `name` in `wrangler.jsonc` (`presentame-online`). Build command: empty. Deploy command: the default (`npx wrangler deploy`). You get a `presentame-online.<your-subdomain>.workers.dev` address.
2. **Click through the workers.dev site.** Home, branding, terms, 404, the forms, WhatsApp buttons, Stripe buttons (check they open the right link), consent banner, Meta Pixel in Events Manager (test events), mobile menu.
3. **Put the domain on Cloudflare DNS (if it is not already).** Add the site in Cloudflare and let it scan existing records. **Compare the scan with the current DNS at Namecheap and copy every MX, TXT (SPF, DKIM, DMARC, verification) and any other record** so email and verifications keep working (including whatever serves `hola@presentame.online`). Keep the GitHub Pages records (A `185.199.108.153`, `.109.153`, `.110.153`, `.111.153`; CNAME `www` > `glancyg17.github.io`) in place until step 5. Then change the nameservers at Namecheap to the two Cloudflare gives you.
4. **Search Console / other verifications.** The repo has Google-style verification files in its root. On Cloudflare they are served at a redirected address (`/name` instead of `/name.html`), which may not satisfy the verifier. Safest: verify the domain with a **DNS TXT record** in Cloudflare, then the files are no longer needed.
5. **Cutover.** On the Worker: Settings > Domains & Routes > Add > Custom domain, for the apex and for `www`. Remove the conflicting GitHub A/CNAME records when Cloudflare asks. Add a redirect from `www` to the apex (Redirect Rule), as GitHub Pages did automatically. Do this at a quiet hour.
6. **Verify live.** `https://` loads with a valid certificate; `curl -I https://presentame.online/terms/` shows the security headers; `/terms` redirects; `/robots.txt` and `/sitemap.xml` load; Stripe confirmation pages load after a test payment; Pixel events fire; email still delivers.
7. **After 1 to 2 stable days.** Turn off GitHub Pages (repo Settings > Pages). The repo can then be made private (Cloudflare builds from private repos; confirm at setup). Delete `CNAME`, update the hosting lines in `CLAUDE.md`.

## Rollback
GitHub Pages stays enabled until step 7, so rollback is a DNS edit: point the apex A records and the `www` CNAME back to the GitHub values in step 3 (remove the Worker custom domains first).

## Later (optional)
- HSTS (zone setting) once HTTPS is confirmed everywhere.
- A Content-Security-Policy. The sites use inline scripts, Google Fonts, the Meta Pixel and FormSubmit, so write it carefully and try it as `Content-Security-Policy-Report-Only` first.
- Preview deployments for branches (enable preview builds in Workers Builds) so client edits can be checked before they go live.
- Cloudflare Web Analytics for the Fresh monthly message.

## Limits worth knowing (free plan, checked Nov 2026)
Workers Builds: 3,000 build minutes a month, one build at a time. Static asset requests are free. Re-check Cloudflare's pricing page before relying on these numbers.
