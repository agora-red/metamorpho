# Briefing · Ágora Impulso

- **Tipo**: proposal (documento de plan de producto para mostrar)
- **Objetivo**: presentar el plan completo de "Ágora Impulso" — agente operativo que detecta oportunidades con datos reales, prepara acciones y las ejecuta con aprobación del profesional. Nada se implementa todavía; el documento debe entenderse solo y quedar bien presentado.
- **Audiencia**: interna (JP + equipo) — decisión de producto.
- **Mensaje clave**: Impulso no es un chatbot; es una bandeja de oportunidades accionables en Flash. El MVP resuelve UN circuito completo: turno cancelado → clientes compatibles → aprobación → WhatsApp → reserva en Nightwing → atribución.
- **Input**: plan de producto completo pegado por Beto (25/08/2026) — 14 secciones: decisión de producto, casos P0/P1/P2, flujo MVP, selección de candidatos, UX en Flash, arquitectura, modelo de datos, API, papel de la IA, prerrequisito WhatsApp, fases 0–4, métricas, criterios de aceptación, fuentes existentes a reutilizar.
- **Restricciones**: sin métricas inventadas (el plan no trae números duros — no se agregan). Selección determinística, IA solo explica/redacta. Referencias reales de código: pulse/select.ts, client-segmentation.ts, whatsapp/auto-messages.ts, PulseCardView.tsx (Flash), Service Options.tsx (Nightwing).
- **Revisión 25/08**: Beto pidió sacar toda mención y dependencia de WaBot — el circuito no usa bot conversacional: el mensaje lleva el enlace de reserva y las respuestas siguen en el WhatsApp del negocio.
- **Revisión 25/08 (2)**: audiencia NO técnica — se eliminó la sección "Modelo de datos y API". Se agregó un prototipo visual funcional montado sobre el Pulse existente de Flash (misma estética frost — valores reales de `flash/src/styles/_tailwind.css` — y mismo nombre: es expandir Pulse con el bloque «Para hoy»). Tres pantallas interactivas: home → detalle (quitar candidatas) → ejecución animada → vuelta con Completada. Testeado E2E con agent-browser.
- **Formato**: HTML autocontenido, Frost tokens, Montserrat, chrome Ágora, mocks del dashboard y del detalle de oportunidad. Publicable en Metamorpho.
