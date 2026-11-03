# Kanban de Producto · cómo funciona (deck interno)

Pedido (Fermín, 22/10/2026): «Armá una presentación con design studio sobre cómo funciona esta funcionalidad. ¿Qué resuelve? ¿Cómo se compone cada sección? ¿Cómo se alimenta? Todo lo necesario para que el equipo de Ágora pueda utilizarla en el seguimiento de funcionalidades. No lo llenes con cosas sin sentido para llenar huecos que denotan que es generado con IA. Hacelo bien.»

- Tipo: deck (11 slides, 1280×720).
- Audiencia: equipo interno de Ágora.
- Mensaje: un solo tablero para las ideas de producto, con origen, estado y release; cómo se carga y quién hace qué.
- Fuente de verdad: el código local de Multiplex (docs/openclaw/kanban.py, dashboard/src/pages/Kanban.tsx, KanbanGuia.tsx), sin deployar a la fecha.
- Capturas: Multiplex local con una copia de la base de dev que tiene solo ideas reales (las 3 de Alberto en #brainstorming y topics reales del Idea Box); se sacaron las tarjetas de prueba y los releases inventados.
- El aviso de #anuncios-inapp se muestra como formato (ese release no existe).

## Actualización 3/11/2026

Pedido (Fermín): «necesito actualizar la presentación con todos estos cambios y actualizar el metamorpho». El Kanban pasó a ser la herramienta de trabajo de Producto: tramos Ideas / Producto / Release, tipos (Idea, Feature, Mejora, Bug, Tarea, Negocio), responsable (Admin) + deadline, vista Semana, lanzadas ocultas a las 2 semanas, y el vínculo con Releases (la tarjeta refleja el checklist; abrir release desde la tarjeta o /release-abrir).
- Fuente de verdad: el código local de Multiplex (kanban.py, Kanban.tsx, KanbanGuia.tsx, control.py), sin deployar a la fecha.
- Demo: las ideas siguen siendo las reales (negocios anónimos); el trabajo, los responsables, las fechas y los releases son de ejemplo, y así lo dicen la barra de la demo y el cierre.
