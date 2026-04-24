# Ágora Voice — Prototipo interactivo

**Tipo**: Prototipo HTML interactivo (1 página, self-contained)
**Fecha**: Abril 2026
**Contexto de uso**: Brainstorming interno de producto · sell-in del concepto

## Brief

Mostrar cómo se vería un **componente de voz universal** que se pluga en cualquier input largo de Ágora (Flash, Nightwing, Lex Luthor). El componente captura audio, lo transcribe con Whisper, y lo estructura contextualmente con GPT-4o-mini.

## Contenido

- Demo del componente aplicado a "Ficha de cliente" con los 5 estados:
  1. **Idle** — mic button flotante sobre el textarea
  2. **Recording** — press & hold expande el mic con waveform animado + timer
  3. **Processing** — transcripción + estructuración con barra de progreso
  4. **Result** — fade-in palabra por palabra del texto estructurado
  5. **Cambiar tono** — popover con 4 variantes (Técnico / Amigable / Breve / Detallado)
- Grid de los 11 contextos donde se reutiliza el mismo componente
- Footer con métricas: 2 sprints a MVP · <$0.01 por dictado · 11 lugares con 1 componente

## Gancho para abrir el brainstorming

> *"¿Cuánto tarda una maquilladora en escribir una ficha de lo que le hizo a la clienta? 0 segundos, porque no lo hace. ¿Cuánto tardaría en hablarlo? 15 segundos. Propongo que Ágora escuche."*

## Stack

HTML + CSS + JS vanilla, sin dependencias externas más allá de Montserrat (Google Fonts).
Tokens Frost inline, logo Ágora oficial inline (horizontal SVG).
