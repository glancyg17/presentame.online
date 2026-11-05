# Fresh: el servicio detrás de los $300

Fresh es "lo vigilamos por ti", no solo "más cambios". Un cliente que nunca cambia nada debe sentirse cuidado igual. Esfuerzo objetivo: **unos 5 minutos por cliente al mes**, además de los cambios. Si tarda más, simplifica.

(Process notes are in English, client-facing message templates are in Spanish.)

## 1. Mensaje mensual "cómo le fue a tu sitio" (WhatsApp, primera semana del mes)

**Data sources (both free, cookie-free, no consent banner needed):**
- **Cloudflare Web Analytics**: add each client site (the beacon script works on any host, including GitHub Pages). One dashboard for all clients.
- **Google Search Console**: verify each client domain at build time (SOP). Gives searches shown and clicks.
- Not available from these: taps on call/WhatsApp buttons. Never promise them.
- Check Cloudflare's coverage for sites with visitors outside Mexico before relying on the numbers.

**Plantilla (corta, honesta aunque los números sean pequeños):**
> Hola [nombre], así le fue a [negocio] en [mes] 👋
> 👀 [N] visitas a tu sitio
> 🔍 Apareció en [N] búsquedas de Google, [N] clics
> 📄 Página más vista: [página]
> Una idea: [un cambio pequeño y concreto]. ¿Lo hago?

First month: say it is the baseline. Low numbers: lead with the idea, not the number. **Never send automatically**: a human reads it first.

## 2. Avisos de temporada (4 al año, envío en lote)
Finales de marzo (Semana Santa, horarios de primavera) · mediados de junio (vacaciones de verano) · principios de septiembre (regreso a clases) · mediados de noviembre (aguinaldo, Buen Fin, horarios navideños). One template each, same day to every Fresh client. Example: *"Ya viene diciembre. ¿Quieres cambiar tus horarios u ofertas? Solo responde con lo que necesites."* The reply is a normal edit.

(Buen Fin and the local calendar matter more than the UK one: adjust the dates to what MX small businesses actually run.)

## 3. Revisión anual (en el aniversario de la fecha de inicio)
Click every link and button, check phone/email/address/hours, photos and speed, confirm the domain renewal and the Google listing details. Reply with a short "todo en orden / esto arreglé". Then offer the flyer/card/menu refresh.

## 4. Extras opcionales (no prometidos en el sitio)
- Keep the Google Business Profile in step when hours/phone change (the client adds Glancy as manager).
- A "déjanos tu reseña en Google" link and QR file on joining Fresh.
- Uptime alert (free monitor) that only pings when a client site is down.
- **Como Se Debe** clients get this same service for their first 3 months (Fresh-level perk).

## 5. Before the first Fresh client reaches month 2
Set up Cloudflare Web Analytics and Search Console for that client's site, write the four seasonal templates in final form, and test one monthly message end to end. The site already promises the monthly message.
