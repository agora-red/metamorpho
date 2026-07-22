# Briefing · claude-manos-ia-lab-2026-07

**Tipo**: deck (7 slides, scroll-snap, fixed canvas)
**Fecha**: 2026-07-22 (se presenta miércoles 23/7)
**Presenta**: Alberto
**Audiencia**: equipo no-técnico de Ágora (JP, Fermin, Isabella, Lautaro) que usa Claude Code a diario
**Objetivo**: IA Lab de orientación — que el equipo sepa que Claude ahora puede manejar un navegador, qué pedirle y cómo activarlo. NO es un producto terminado; es una capacidad + hands-on.
**Mensaje clave**: "Hasta ahora Claude leía internet. Ahora tiene manos." Antes te contaba lo que leyó; ahora entra y lo ve con sus propios ojos.
**Tono**: español argentino, simple, directo, cero jerga técnica.

## Estructura (guion ~25 min)
1. HOOK (ink): Claude leía internet → ahora tiene manos.
2. DEMO EN VIVO (placeholder minimal): prompt real "Entrá al sitio de AgendaPro y contame qué planes y precios tienen, con capturas."
3. QUÉ ACABA DE PASAR: antes (leía) vs ahora (navega) — dos columnas.
4. QUÉ LE PODÉS PEDIR: 4 ejemplos por rol con output — Fermin/CS (bug de reserva → capturas del paso exacto), JP/Producto (AgendaPro recordatorios WA → sí/no con evidencia), Isabella/CS (página del negocio en mobile → capturas), Lautaro/Growth (features de una herramienta → resumen con fotos). Remate: en castellano, sin comandos.
5. ¿ES SEGURO?: navegador propio y aislado, no ve tus cuentas, pide permiso; captchas/logins raros → te pide una mano y sigue.
6. ACTIVALO HOY (slide clave): novedad de hace 10 días — Claude Code Desktop trae navegador integrado (Cmd+Shift+B, cero instalación). Fallback terminal: "Instalá agent-browser y probalo abriendo www.agora.red — mostrame una captura." Dato de color: OpenAI dio de baja su browser la misma semana.
7. CIERRE (ink) — AHORA USTEDES: cada uno tira su primer pedido en vivo + brainstorm "¿dónde lo usarías vos?". Takeaway: solo hay que saber que Claude puede navegar, y pedírselo.

## Contexto de research
- Verificado 22/7: Claude Code Desktop shippeó browser embebido (~10-12 jul 2026, semana 28, Cmd+Shift+B, sandboxeado, safety classifiers, desktop-only).
- agent-browser (Vercel Labs) queda como fallback terminal y motor de las skills de Beto.
- Patrón de deck reusado de multiplex-ia-lab-2026-05 (scroll-snap, chrome wordmark+dot, ink cover/cierre, Frost tokens).
