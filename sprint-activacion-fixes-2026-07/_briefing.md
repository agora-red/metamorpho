# Sprint de activación — one-pager interno (#brainstorming)

**Tipo:** one-pager · **Audiencia:** equipo interno Ágora · **Fecha:** 6 jul 2026

Resumen del sprint del 6/jul: auditamos el Pulso de Activación + grabaciones del
finde y salió una cadena de 5 fixes a prod (flash + nightwing):
1. Callback resiliente (recovery silencioso ante state mismatch; rescató usuarios reales).
2. Scrub de credenciales en URLs capturadas por analytics.
3. /comenzar detecta cuenta existente antes de pedir contraseña (banner + CTA login).
4. Setup 2 con navegación por historial (el "atrás" no eyecta a Setup 1) + guards anti-loop + CTAs.
5. Progreso del setup sobrevive re-logins del mismo usuario.

Todo pasó por 2 pasadas de code review multi-agente (16 findings, 3 hubieran sido
incidentes) y quedó un audit horario vigilando la salud.

Team-safe: sin credenciales, sin el detalle explotable del token, sin números de
prod crudos sensibles. Tono técnico-celebratorio, "de la observación al fix en un día".
