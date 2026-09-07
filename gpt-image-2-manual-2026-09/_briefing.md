# Briefing · GPT Image 2 en Ágora (manual)

**Tipo**: manual / propuesta visual (deck scroll-snap, 14 láminas).
**Objetivo**: un Metamorpho aparte, enfocado en GPT Image 2 (el modelo que Beto eligió como ganador claro en `low`): qué variables recibe para generar imágenes y qué casos de uso abre — cada variable y cada caso con su imagen.
**Audiencia**: equipo interno (JP), producto.
**Mensaje clave**: un modelo, US$0,005 por imagen, y todo lo que se le puede pedir con la data que Ágora ya tiene (brand kit, servicios, precios, fotos).

## Origen
- Pedido de Beto (7/sep/2026): "creemos una metamorpho aparte enfocado en este modelo, que variables recibe para generar imágenes, diferentes casos de usos con su imagen".
- Continúa `redes-ia-instagram-2026-09` (PoC + propuesta) y la conversación de casos de uso / empaquetado.

## Qué se corrió
- 12 llamadas nuevas a la API de OpenAI (14 imágenes, US$0,245) con `gpt-image-2`, todas con data real de prod: Color & Style (centrodepelo), Meraki Nails (merakinailscin), Melody Espinosa Studio (melodystudio), Azahara (azahara.turnos) — paletas, fuentes y servicios de `vendor_storefronts` / `services`.
- Variables demostradas: `size` (1024², 1088×1360, 1088×1936, 1920×640, 1200×624), `quality` (low/medium/high, del PoC anterior), `n=3`, `background=transparent`, `output_format=webp` + `output_compression=70`, edits con `image` (recolor), `image[]` (dos fotos), `mask` (inpainting).
- Composiciones híbridas reales (Pillow): lista de precios con tres servicios reales, tarjeta de regalo (nombre y monto de ejemplo), cabecera de WhatsApp, ornamento transparente sobre la placa.
- Stats de prod: 11.926 servicios activos con portada por defecto (1.335 negocios vigentes), 1.234 vidrieras sin cover, 1.553 sin avatar.

## Restricciones aplicadas
- Solo capacidades demostradas; los hallazgos negativos se dicen (la máscara guió pero no restringió; el banner sumó un rostro no pedido).
- Sin métricas internas sensibles; precios = tarifas públicas / costo medido por tokens.
- Montserrat, tokens Frost, español rioplatense.
