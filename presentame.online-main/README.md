# preséntame. — presentame.online

Sitio estático para la marca de México/LATAM (español, MXN), alojado en GitHub Pages. HTML/CSS/JS plano, sin paso de build. Haz push a `main` y queda en vivo en unos 2 minutos.

Es el sitio hermano de getpresented.co.uk: mismo sistema de diseño y estructura, contenido localizado.

**El codex de trabajo es [`CLAUDE.md`](CLAUDE.md)**: productos y precios, enlaces de Stripe, mapa del repo, tokens de diseño, reglas de seguimiento, pendientes y decisiones. Empieza por ahí. Las solicitudes de cambios de clientes siguen [`docs/edit-workflow.md`](docs/edit-workflow.md).

## Edición rápida
Cada página es un solo archivo HTML. Busca el texto visible, edítalo, commit, push. Si cambias un precio o agregas un producto, sigue las reglas de `CLAUDE.md` §8.

## No tocar sin cuidado
El bloque de consentimiento de cookies y Meta Pixel al inicio de cada página, los manejadores `onclick` de Lead de WhatsApp y los enlaces de pago de Stripe.
