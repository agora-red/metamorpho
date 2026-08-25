# Briefing — Reseñas de clientes (prototipo)

- **Fecha**: 25/8/2026
- **Tipo**: proposal / prototipo interactivo de producto
- **Objetivo**: alinear al equipo (JP + Beto) sobre el sistema de reseñas post-visita: flujo del cliente "god^2" (pedido por WhatsApp → rating de un tap → loop con Google), y la decisión central de producto: **el negocio elige el modo** — Solo Ágora / Solo Google / Ambas / Apagado, con pedir y mostrar como decisiones independientes. Todos los casos cubiertos.
- **Audiencia**: interna (producto) — y compartible con el equipo vía Metamorpho.
- **Mensaje clave**: reseñas verificadas (1 visita real = 1 reseña) con la reputación donde el negocio la quiera; todo opcional.
- **Contexto**: Fresha lanzó su Online Reputation Manager (20/8/2026, Google + Fresha unificados con IA). Pedido real de un vendor de calificación post-servicio + medición anónima de calidad (cubierta con el feedback privado). Cyclone ya tiene `vendor_google_place` (rating + reviews + write_review_url) y el job WA post-visita.
- **Interacción**: selector de modo que hace reaccionar los 17 touchpoints; estrellas clickeables (5★ vs ≤3★); switches de "qué se muestra" independientes; deep-link `?mode=` y `?stars=`.
- **v2 (25/8, pedido de Beto)**: mapear ABSOLUTAMENTE todos los lugares donde aparece el sistema — 17 touchpoints en 4 actos (WhatsApp, email con estrellas que puntúan, tabla Actividad, página de rating + variante 1–3★, gracias+Google, campanita del negocio "Tu bandeja", side menu en Marketing y comunicación, inbox, email al negocio, dashboard, ficha del cliente "Última actividad", equipo, storefront, marketplace, Google Maps, cierre del loop por email → rebooking). OJO (Beto 25/8): la campanita es la DEL PROFESIONAL en Flash — al cliente no se le agrega campanita. Mocks fieles a las superficies reales relevadas en Flash/nightwing/cyclone (labels y layouts literales del código).
- **Restricciones**: datos de demo (Lumen Estudio / Caro / Meli — nombres ficticios, sin métricas internas reales); Frost tokens; Montserrat; público en Metamorpho.
