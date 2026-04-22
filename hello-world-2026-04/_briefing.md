# Hello World · Design Studio · 2026-04

**Tipo**: deck (showcase)
**Objetivo**: testear que el flujo completo del Design Studio funcione (briefing → research → design → preview → publish).
**Audiencia**: interno — el usuario, para validar el pipeline.
**Mensaje**: "Hola mundo" — showcase del sistema Frost (tokens, tipografía, componentes) aplicado correctamente.
**Data / proof**: N/A — output genérico.
**Formato**: deck scroll-snap, 4 slides, self-contained HTML.

## Fuentes consultadas

- **Frost tokens**: `flash/stories/Design/Tokens.stories.tsx` (paleta completa: brand, severity, ink, surface)
- **Shadows**: `flash/stories/Design/Tokens.stories.tsx` → Shadows export (`frost-xs` … `frost-glow-lg`)
- **Radius**: `flash/stories/Design/Radius.stories.tsx` (6 / 10 / 12 / 20 / 28 / 999)
- **Spacing**: `flash/stories/Design/Spacing.stories.tsx` (Tailwind 4-unit scale)
- **Typography**: `flash/stories/Design/Typography.stories.tsx` (Montserrat exclusiva, 200/300/500/600, scale `agora-*`)

## Decisión tipográfica

El skill menciona Space Mono para data/mono, pero Frost se movió a **Montserrat exclusiva** (con `font-variant-numeric: tabular-nums` para numerales). Respeto el source actual del repo Flash como fuente canónica.
