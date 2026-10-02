# Marketing PRO+ · Propuesta visual
Fecha: 2026-10-02

## Confirmado en el pedido
Proponer un adicional de marketing similar en facturación a Finanzas Pro. Incluir Pulse, campañas, grupos de clientes y acciones. Las plantillas de WhatsApp operativas son transversales. El usuario pidió una propuesta visual con metamorpho-propuestas.

## Objetivo y audiencia
Una página breve para evaluar la oferta, escrita de forma comprensible para profesionales de belleza. Promesa: más clientes que vuelven y más agenda ocupada.

## Valores y decisiones propuestos, no aprobados
ARS 14.900 mensuales por negocio, alternativa a evaluar ARS 9.900. Consumo de WhatsApp separado. Cupo de email, impuestos, límites de envío, crédito inicial y renovación pendientes. Hasta tres oportunidades semanales cuando existan datos. Piloto de 30 días con 10–15 negocios. Inclusión en planes existentes por definir.

## Alcance de la pieza
Cinco bloques: qué proveemos, límites, qué no incluye, cómo se activa y para decidir. No es implementación ni anuncio de disponibilidad. Sin métricas reales de clientes, información personal ni capturas de producción. Los escenarios numéricos y nombres están rotulados como ficticios, sin promesas de resultados. Conserva el acceso actual a Pulse básico y comunicaciones operativas como propuesta de empaquetado.

## Diseño
Montserrat 200/300/500/600, tokens Frost del manual, logo SVG oficial y pictogramas Font Awesome Free. HTML autónomo con assets relativos; fuentes por Google Fonts. Revisión a 390 y 1280 píxeles.

## Publicación
Contiene funcionalidades futuras y precios tentativos. Requiere confirmar este contenido concreto antes de publicarlo en la galería pública.

## Ampliación solicitada: experiencia interactiva
El usuario pidió hacer la pieza interactiva y proponer visualmente cada módulo. Se conserva el slug y los cinco bloques comerciales. El primero incorpora seis vistas conectadas: Pulse, Campañas, Clientes, Automatizaciones, Resultados y Plantillas WA transversales.

La vista Hoy / Propuesta usa la estructura de Clientes observada en Flash el 2 de octubre de 2026, redibujada con datos ficticios. No conserva capturas ni datos personales de la referencia.

Interacciones: campañas preparadas desde Pulse; objetivo y canal editables; vista previa del mensaje; revisión y envío simulado; selección y búsqueda de clientes elegibles; recetas configurables y activación de ejemplo; exclusión por próxima reserva; selector de resultados; biblioteca comercial y operativa; reinicio de la demo. No hay conexiones a APIs ni envíos. Los ejemplos viven en memoria de la página y se reinician al recargar.

Diseño responsive revisado en 390 y 1280 px. Los precios siguen siendo hipótesis pendientes de validación. La publicación pública de funciones sin lanzar permanece pendiente de confirmación.

## Revisión de diseño solicitada con frontend-design
Se revisaron las tres imágenes de referencia aportadas por el usuario para Pulse, en escritorio, móvil y comparación con Analítica. Se recupera la composición: conclusión de semana, evolución de doce semanas, origen de reservas, mapa horario, acciones y ediciones semanales y mensuales (novedades y encuesta retiradas en la revisión del 2/10). Los números son ejemplos ficticios y no estadísticas internas.

Dirección visual: Montserrat, Frost claro, azul para acciones y progreso, verde para resultados de acciones completadas. Pulse mantiene la jerarquía de la referencia; Campañas incorpora un recorrido guiado, Clientes segmentos y fichas de ejemplo, Automatizaciones condiciones visibles, Resultados estados de reserva y Plantillas una vista previa del mensaje. Se agregó modo ampliado de la experiencia.

Interacciones adicionales verificadas: puntos semanales, fuentes de reservas, franjas horarias, historial mensual/semanal, explicación Pulse/Analítica, asistente de tres pasos para campañas, programación simulada, validación de correo vacío, ficha de cliente, activación y pausa de reglas. Ninguna acción contacta clientes o guarda datos en servidores.

## Revisión del 2 de octubre · alcance y uso

- Pulse se dedica a marketing: se retiran novedades generales de Ágora y encuesta de producto.
- WhatsApp permite elegir una plantilla y revisar texto fijo; no hay textarea ni edición libre. La edición de correo mantiene su propio contenido al alternar canales. Variables automáticas y estados de aprobación están explícitos; todo el catálogo de la demo es ilustrativo.
- Clientes conserva título, tabla, etiquetas, cumpleaños, primera y última visita, ingreso total y ficha de la estructura observada en Flash. Se redibuja con seis clientes ficticios. Los segmentos toman la base de Operator; selección para campañas y elegibilidad se identifican como extensión propuesta.
- Automatizaciones y plantillas forman un recorrido: evento, espera, condiciones, plantilla fija y resultado. La biblioteca muestra la regla vinculada, su espera y su estado, y vuelve a esa misma configuración. No crea otro disparador.
- Simulación de condiciones: apto, próxima reserva, falta de permiso, invitación repetida y falta de presupuesto. Cambiar la espera pausa la regla en la demo para revisarla.
- Las plantillas operativas siguen fuera del requisito Marketing PRO+; su escenario vive en Mensajes automáticos. No se implementaron estas propuestas en el producto real.

## Revisión v5 · Lectura y automatizaciones flexibles

Se elimina el switch Hoy en Flash. Su reemplazo es Entender la propuesta: una vista de lectura breve con cinco pasos y accesos a los módulos. La vista histórica Hoy deja de formar parte de la pieza.

Automatizaciones pasa a un constructor: crear desde cero o copiar una receta. Las copias son independientes. Se pueden elegir eventos (atención, primera atención, cumpleaños o entrada a segmento), espera, condiciones por visitas/servicio/etiqueta combinadas con Y/O y una acción (WhatsApp, correo o agregar etiqueta). El alcance se expresa como combinaciones de los bloques disponibles, no como ejecución arbitraria.

La receta contiene configuración editable; la plantilla WA conserva texto fijo y condiciones de uso. Las combinaciones incompatibles se bloquean en la demo, incluido un saludo de cumpleaños diferido. Cada regla tiene nombre, resumen legible, estado y prueba con un cliente ficticio; cambiar una regla activa la vuelve a borrador. No hay persistencia fuera de la sesión ni acciones reales.


## Revisión v6 · Propósito, sinergia y resultados del conjunto

Entender la propuesta ahora explica los seis módulos: qué pregunta resuelve cada uno, por qué existe, cómo usarlo, cómo se conecta y cuál es su límite. El mapa separa campaña puntual de automatización recurrente, con plantillas compartidas y aprendizaje que vuelve a Pulse. Tres casos muestran el recorrido completo: volver, segunda visita y horarios disponibles.

Resultados reúne campañas, automatizaciones de mensajes y acciones internas. Tiene período, filtro por tipo, detalle de envíos/omisiones/reservas/atenciones/cobros y siguiente acción. Las etiquetas no reciben atribución monetaria. Los ejemplos históricos son ficticios; las pruebas creadas en la demo tienen cero ejecuciones reales. Se explica la regla propuesta de atribución y no se calcula retorno sin costos.

Se simplifican nombres y ayudas: Clientes → Mensaje → Revisión; Cuándo empieza / A quiénes aplica / Qué hace. Las recetas son la entrada principal del constructor. Un segmento prepara una regla y la selección manual de clientes se conserva al cambiar el motivo, reevaluando quién puede recibir. WhatsApp sigue con texto fijo.

La revisión de comprensión es heurística: queda por contrastar con profesionales mediante tareas concretas antes de afirmar facilidad de uso validada. Se probó el prototipo y se revisó el render; no se implementan funciones reales.


## Revisión v7 · Limpieza y pulido visual

Se retira la ficha individual de Clientes, incluidos botones y modal; la propuesta no contiene Fichas y preguntas. Clientes se centra en seleccionar personas y preparar acciones. Se conserva el recorrido de campañas, reglas y plantillas fijas.

Se mejora la jerarquía tipográfica, contraste de texto secundario, estados de selección, navegación y tamaño de controles. Lectura tiene un mapa sincronizado con la explicación, pasos más legibles y menos rótulos repetidos. La tabla muestra los motivos de exclusión junto al nombre en móvil. Se simplifican notas internas visibles.
