# Briefing · WA Asesor — Documento de scope para discusión

- **Tipo**: wiki-page (single-page, scrollable, con TOC lateral)
- **Objetivo**: alinear a Fer y Beto sobre el rediseño del WA bot — de bot de reserva a asesor personalizado — antes de escribir specs técnicas. Disparar la discusión de equipo.
- **Audiencia**: interno (Fer, Beto, JP). Producto/diseño, no ingeniería.
- **Mensaje clave**: el WA bot deja de intentar tomar la reserva y pasa a asesorar con contexto profundo del negocio, empujando la reserva al in-app vía un link parametrizado.
- **Tono**: lenguaje simple, argentino, directo. Nada de jerga técnica (no specs).
- **Formato**: single-page wiki, secciones con TOC fijo a la izquierda.

## Contenido (de la charla previa con JP)

1. **Cambio de paradigma** — antes (order-taker con fricción) vs ahora (asesor que recomienda + pasa link).
2. **Cómo se ve para el cliente** — flujo conversacional, chat mock.
3. **El contexto que alimenta al bot** — 4 capas en lenguaje simple:
   - Quién es el negocio (identidad/voz)
   - Qué ofrece (catálogo asesorable)
   - Las reglas del negocio (políticas/guardrails)
   - Estado en vivo (disponibilidad/historial — v2)
4. **Cómo arma los links de reserva** — service(s) + staff (único o ninguno), tabla de casos.
5. **Reglas de hand-off simples** — 3 triggers + pausa dumb.
6. **Lo que el bot NUNCA hace** — guardrails.
7. **Cambios clave de cara al usuario** — cliente + vendor.
8. **Decisiones para discutir** — número WA por vendor, fuente del contexto, canal de hand-off, billing.

## Decisiones de diseño aplicadas
- Backgrounds planos (sin gradientes — feedback JP).
- Copy cliente↔vendor nunca menciona Ágora como marca.
- URL canónica `www.agora.red/{username}`.
- "Planes mensuales" (no membresías). "Clientes" (no desdoblar).
- Montserrat + Space Mono, tokens Ágora, isotipo PNG oficial.
</content>
</invoke>
