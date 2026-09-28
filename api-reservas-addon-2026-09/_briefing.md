# Briefing — API de reservas (add-on)

- **Pedido (28/9/2026, #brainstorming):** una barbería cliente preguntó «¿Ágora cuenta con API, webhook o alguna integración que permita a un sistema externo consultar disponibilidad y crear/cancelar/reprogramar reservas automáticamente?». JP: «me encanta la idea, pero siempre queda la duda de cómo lo limitamos para que se use sanamente». Beto: «definitivamente es un add-on». → `/product-research` «hagamos un metamorpho con la propuesta».
- **Tipo:** proposal, página con scroll, responsive.
- **Audiencia:** equipo interno (JP, producto, comercial).
- **Objetivo:** decidir si y cómo se ofrece una API pública de reservas como add-on.
- **Mensaje clave:** hoy no existe; se arma con ocho límites que la hacen segura, y más de la mitad de la base técnica ya existe.
- **Datos:** código de `origin/develop` (28/9), base de producción solo lectura (90 días), Slack 2026, documentación oficial de 15 competidores.
- **Fuente larga:** `cyclone/docs/research-api-publica-reservas-2026-09.md`.
- **Límites declarados:** la DB de ideas de Notion no se pudo consultar (conector en otro workspace); no sabemos qué sistema quiere conectar la barbería.
