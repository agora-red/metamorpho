# Briefing · Redes con IA → Instagram

**Tipo**: propuesta visual (deck scroll-snap) con PoC real adentro.
**Objetivo**: retomar el PoC de generación de imágenes por IA para el builder de Redes (julio 2026), expandirlo a más modelos con distintos costos, y atarlo a la novedad del 5/sep: Meta aprobó los permisos de Instagram (`instagram_business_content_publish` + `instagram_business_basic`).
**Audiencia**: equipo interno (JP), como propuesta de producto.
**Mensaje clave**: ahora que cualquier profesional puede conectar su Instagram y publicar desde Ágora, la IA puede generar el visual con la data real del negocio — y Ágora lo publica. El texto crítico (precio, duración, URL) sigue siendo capa HTML determinística.

## Origen
- Hilo de Slack de JP (15/jul/2026): "probá Seedream 5.0 Pro para posts de IG". PoC de julio: NB2 / NB Pro / GPT Image 2 (artefacto `PoC Imagen IA — Redes`). Seedream quedó sin probar (fal.ai sin saldo). Research de mercado en `docs/research-mercado-imagen-ia-redes.md`.
- Hilo de Slack #general (7/sep/2026): permisos de IG aprobados; lo que habilitan y lo que no.

## Qué se corrió en esta versión (7/sep/2026)
- Data real de Color & Style (centrodepelo, Bariloche) leída de prod: brand kit actual (marrón `#96694d` sobre beige `#f1e7dd`, Fraunces + Inter), servicio "Corte de pelo dama (incluye lavado)" $21.500 · 60 min, cover real del servicio.
- 4 casos de julio + historia 9:16, contra 6 variantes de OpenAI (clave de la empresa): GPT Image 1 Mini · medium, GPT Image 2 · low / medium / high, GPT Image 1 · medium, GPT Image 1.5 · medium.
- Placa híbrida compuesta de verdad: fondo IA + texto determinístico con las fuentes del brand kit (Pillow).
- Escalera completa de 15 modelos con precio real del catálogo de Vercel AI Gateway (Nano Banana 2 / Lite / Pro, Seedream 4.0→5.0 Pro, FLUX.2, Recraft, Muse, Grok). NO corridos: la capa gratuita del gateway no cubre modelos de imagen — requiere créditos pagos.

## Restricciones aplicadas
- Solo capacidades demostradas: lo que Cyclone ya sabe publicar (`publishImage`, `publishReel`, `publishCarousel` en `services/instagram`) y lo que el builder de Flash ya hace (3 templates, data real, html-to-image, publicar feed).
- Sin métricas internas ni datos de otros clientes. Precios = tarifas públicas de API.
- Montserrat, tokens Frost, español rioplatense.
