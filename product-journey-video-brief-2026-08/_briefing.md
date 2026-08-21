# Briefing — product-journey-video brief interno

**Tipo**: briefing / one-pager interno (no landing de marketing)
**Objetivo**: documentar la skill `product-journey-video` para el equipo — herramientas, metodología y detalles técnicos.
**Audiencia**: equipo interno de Ágora.
**Mensaje clave**: la skill automatiza el armado de videos tutoriales narrados con highlights sincronizados palabra-por-palabra, evitando los 3 bugs reales que aparecieron al armarlo a mano.

## Brief textual del usuario (verbatim, resumido)

Contenido pedido: qué hace, herramientas (Claude Code + agent-browser, Google Gemini API, ffmpeg),
metodología (8 fases), detalles concretos (duración objetivo ~90s, caso real 73s/13 escenas, resolución
1920×1080, límite de 10 llamados TTS/día, highlight #FFC400, costo $0), y el origen (3 bugs reales que
motivaron la skill). Pedido explícito: "prioriza claridad y densidad de información sobre estética
elaborada" — brief interno, no asset de marketing.

## Fuente

`cyclone/.claude/skills/product-journey-video/SKILL.md` + sesión real de armado del video de alta de
catálogo de productos (13 escenas, 73s, quota Gemini TTS 9/10 usados).
