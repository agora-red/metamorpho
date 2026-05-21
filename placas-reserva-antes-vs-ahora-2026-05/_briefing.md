# Briefing — Placas de Reserva (Alfred) · Antes vs Ahora

**Tipo:** proposal (propuesta de diseño interna)
**Audiencia:** equipo Ágora (producto + fundadores / JP)
**Objetivo:** mostrar por qué las placas auto-generadas actuales están flojas y proponer un rediseño radical, con comparación lado a lado evidenciada en output real.

## Qué son estas placas
Carrusel-tutorial "Cómo reservar un turno en nuestra página" — 6 Feed (1080×1350) + 6 Story (1080×1920).
Se piden por Slack: `@Alfred genera las imágenes para el user <username>`.

## Pipeline
Alfred encola job → cyclone arma URLs `https://pro.agora.red/posts/{feed|story}?id={1..6}&vendor={username}` → Puppeteer headless les saca screenshot → sube a S3/CloudFront. Los diseños viven en Flash (`FeedPreview.tsx` / `StoryPreview.tsx`). Cada paso embebe el storefront VIVO del negocio vía iframe (`/iframe/{username}`, `/{username}/reservar`). 2 de 6 pasos usan PNG estáticos hardcodeados (slide4/slide5) en azul viejo de iOS.

## Vendor de ejemplo (real)
@agora.pelu — "Peluquería canina". Paleta: primario mauve #C9A9A6 · acento #B8918E · crema #FDF8F6 · tinta #2D2926 · éxito #16A34A. Tipografías: Playfair Display + Raleway.

## Problemas (evidenciados en el output real)
1. Bugs de render: texto fuera del canvas (feed-3, feed-6), línea de progreso que sangra fuera de 1080px, numeración off-by-one, miniaturas de servicio rotas.
2. Cero marca del vendor (títulos navy fijo).
3. Cuatro mundos de color (navy + mauve + azul iOS + verde).
4. Placeholders desactualizados (slides 4-5, azul iOS, datos genéricos).
5. Estética wireframe (fondo plano, marcos inconsistentes, espacio muerto).
6. Redundancia / estructura débil (story-1 ≈ story-6, no vende).

## Propuesta
Carrusel editorial co-branded Ágora × Negocio. Color del vendor como sistema; grid editorial consistente; device-frame unificado premium; pasos reales en mauve (no azul iOS); stepper contenido + numeración correcta; tipografía con jerarquía y anti-overflow; portada con hook + cierre con CTA.

## Assets
Capturas reales de agora.pelu en `assets/feed-{1..6}.jpg` y `assets/story-{1..6}.jpg` (vendor 30440, generadas 2026-05-20).

## Notas
Contiene datos internos (feature, vendor real, bugs) → NO publicar al gallery público metamorpho sin OK explícito. Preview local solamente.
