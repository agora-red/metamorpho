# Briefing — Reseñas de clientes (prototipo)

- **Fecha**: 25/8/2026
- **Tipo**: proposal / prototipo interactivo de producto
- **Objetivo**: alinear al equipo (JP + Beto) sobre el sistema de reseñas post-visita: flujo del cliente "god^2" (pedido por WhatsApp → rating de un tap → loop con Google), y la decisión central de producto: **el negocio elige el modo** — Solo Ágora / Solo Google / Ambas / Apagado, con pedir y mostrar como decisiones independientes. Todos los casos cubiertos.
- **Audiencia**: interna (producto) — y compartible con el equipo vía Metamorpho.
- **Mensaje clave**: reseñas verificadas (1 visita real = 1 reseña) con la reputación donde el negocio la quiera; todo opcional.
- **Contexto**: Fresha lanzó su Online Reputation Manager (20/8/2026, Google + Fresha unificados con IA). Pedido real de un vendor de calificación post-servicio + medición anónima de calidad (cubierta con el feedback privado). Cyclone ya tiene `vendor_google_place` (rating + reviews + write_review_url) y el job WA post-visita.
- **Interacción**: selector de modo que hace reaccionar mensaje WA, flujo, vitrina y admin; estrellas clickeables (5★ vs ≤3★ cambia el foco a mejora + privado); switches de "qué se muestra" independientes; deep-link `?mode=` y `?stars=`.
- **Restricciones**: datos de demo (Lumen Estudio / Caro / Meli — nombres ficticios, sin métricas internas reales); Frost tokens; Montserrat; público en Metamorpho.
