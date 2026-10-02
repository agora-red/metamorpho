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

## Revisión v8 · Estructura, wording y comprensión

Pedido: dar una vuelta de UI/UX y wording para que la propuesta se entienda, sin entrar en lo técnico.

- **Orden del documento**: promesa → 01 Cómo funciona (4 pasos visibles, cada uno abre su módulo) → 02 Qué suma a tu plan (tabla Tu plan / Con PRO+) → 03 Probalo en un minuto (instrucciones antes de la demo) → 04 Precio y condiciones → 05 Para decidir. Se retira el desplegable «Qué incluye cada módulo» y las notas sueltas entre secciones.
- **Dos voces separadas**: todo lo que lee un profesional va en presente y con «vos»; las preguntas abiertas y el piloto pasan a una nota para el equipo, marcada como «no forma parte de la oferta». Lo pendiente se marca con una etiqueta «a definir» en vez de condicionales.
- **Precio y condiciones** reúne precio, activación en tres pasos (Facturación → tope de envíos → primera campaña), límites redactados como beneficios («Un adicional por negocio», «Sin ruido», «Solo a quien corresponde») y «No incluye».
- **Ejemplo**: navegación en el orden del recorrido (Pulse, Clientes, Campañas, Automatizaciones, Resultados) y Plantillas de WhatsApp aparte como biblioteca. Botón «Ver cómo se conecta» / «Volver al ejemplo». Sin la abreviatura «WA».
- **Coherencia de los datos de ejemplo**: Pulse ya no muestra el viernes libre y, a la vez, «Llenar el viernes» como hecho; la tarjeta resuelta pasa a ser la automatización de segunda visita (4 reservas, enlaza a su detalle). Eje del gráfico: «Últimas 12 semanas · julio a septiembre». Clientes aclara «Muestra de 6 clientes».
- **Wording de módulos**: disparadores en lenguaje simple («Termina una visita», «Es el cumpleaños del cliente»), costo y tope en la revisión de campaña, «Costo de tus envíos · Todavía sin datos» en Resultados, «Reservas · No requieren PRO+» en Plantillas.
- **Mapa «Cómo se conecta todo»**: campaña y automatización con íconos y separador «o»; en el celular se apilan para no recortarse.

Sin cambios de alcance, precios ni funcionalidades. Datos íntegramente ficticios.

## Revisión v9 · Canales, base contactable y horarios libres

Pedido: sumar a Marketing PRO+ tres ideas del research del 2/10. Perfil de Google e Instagram quedan afuera porque van al plan base.

- **Canales (nuevo módulo).** Reservas por canal (Instagram, tu página, mensajes de Ágora, Google, WhatsApp, marketplace, cargadas a mano) y visitas a tu página, incluidas en todos los planes. PRO+ suma cuántas visitas terminan en reserva, las búsquedas de Google con las que te encontraron (Search Console de agora.red filtrado por la ruta del negocio, sin que conecte nada) y una recomendación semanal. Pulse enlaza desde «De dónde vinieron».
- **Base lista para campañas (en Clientes).** A cuántos de tus clientes podés escribirles (teléfono, permiso, email, cumpleaños) y cómo completar lo que falta: pedir permiso y cumpleaños al reservar o al confirmar un turno ya agendado. No se usan campañas para pedir permiso.
- **Horarios libres (nuevo módulo).** Turnos vacíos de la semana, oferta de último momento con descuento y vencimiento, publicación en tu página y aviso a la lista de espera (por orden o a todos). Pulse enlaza desde «Horas libres». Las ofertas aparecen en Resultados como un tipo más.
- Documento: pasos 1 y 3, tabla «Qué suma a tu plan» (filas Canales y Horarios libres; Clientes con base contactable) y una decisión nueva sobre qué parte de Canales va en todos los planes. Lectura: guías de los dos módulos, mapa con Canales y Horario libre, y el ejemplo «Ocupar horarios» reescrito.
- Datos de ejemplo coherentes entre módulos: 328 reservas en septiembre; 33 por mensajes de Ágora = 14 recordatorios + 19 vinculadas a campañas, automatizaciones y ofertas en Resultados; la oferta de ejemplo es de un martes, para no contradecir el viernes libre de Pulse.

Sin cambios de precio ni de alcance comercial. Datos íntegramente ficticios.

## Revisión v10 · Fidelización, referidos y reservas sin terminar

Pedido: sumar al paquete reservas sin terminar, referidos entre clientes y Fidelización.

- **Fidelización (nuevo módulo).** Mismo club que ya existe en Ágora: puntos por turno completado y por cada $1.000, niveles con descuento permanente, premios canjeables y vencimiento por inactividad. Vista de la tarjeta del cliente que se recalcula con las reglas, y avisos del club (faltan pocos puntos, vencen, subió de nivel). El nivel del club se suma como condición en el constructor de automatizaciones.
- **Referidos (pestaña de Fidelización).** Cada clienta comparte su link por WhatsApp; la amiga recibe un beneficio en su primera visita y quien recomienda, su premio después de esa visita. Ágora no le escribe a la amiga. Las reservas entran como canal «Referidos» en Canales.
- **Reservas sin terminar (receta y disparador nuevos).** «Alguien deja una reserva sin terminar → 60 minutos → plantilla Reserva sin terminar». Espera en minutos (15 a 1.440), un solo aviso, solo a quien dejó teléfono y aceptó avisos. Plantilla nueva en la biblioteca (no se usa en campañas) y resultado de ejemplo en Resultados.
- Datos coherentes: 328 reservas en septiembre; mensajes de Ágora 40 = 14 recordatorios + 26 vinculadas en Resultados; Referidos 5.
- Documento: paso 3, tabla (fila Fidelización), lectura, mapa y una decisión nueva sobre quienes ya usan el club.

Sin cambios de precio ni de las condiciones comerciales.


## Revisión v11 · Pasada de diseño con frontend-design

Pedido: mejorar la UI/UX de la propuesta con la skill frontend-design. La identidad Frost queda fija (Montserrat, azul Ágora, coral como micro-acento, fondo #EFF3F9); la libertad se usó en layout, jerarquía y texto.

- **Hero con la agenda de la semana.** A la derecha del titular, la agenda de Estudio Brisa del 5 al 10 de octubre: una invitación por WhatsApp a Ana y tres turnos libres que se llenan (Ana, Nati, Vale) con «Volvió con tu invitación». Es el titular hecho imagen. Animación única al cargar (la burbuja y después los turnos); con movimiento reducido se ve llena de entrada.
- **Barra de secciones fija** (Cómo funciona, Qué suma, Probalo, Precio, Nota interna) con la sección actual resaltada. Reemplaza los números 01–05, que no eran una secuencia.
- **Títulos de sección** sin número ni palabra resaltada, más grandes (hasta 40px). El énfasis en una palabra queda solo en el h1, como firma de Frost.
- **Cómo funciona como circuito:** cuatro nodos numerados sobre una línea (acá sí es una secuencia) y un retorno «Y vuelve a empezar: lo que aprendés en Resultados vuelve a Pulse». Sin tarjetas.
- **Qué suma:** «No incluido» escrito en lugar de «—»; encabezados en minúscula; sin separadores con punto medio.
- **Precio y condiciones:** las tres tarjetas de condiciones y la lista «No incluye» pasan a dos listas de definición («Cómo se usa» y «No incluye»), sin bordes laterales. Etiquetas en minúscula («a definir»).
- **Prototipo:** en Canales, Puntos y Referidos los tres números sueltos pasan a una frase con las cifras en negrita. Menú con estado activo en brand-wash (sin barrita lateral). Transición corta al cambiar de módulo. Piso tipográfico: nada por debajo de 10px (antes había 7–9px) y la mayoría de las etiquetas a 11px.
- **Accesibilidad:** gris medio a #5B6B80 (4,9:1 sobre el fondo; antes 4,3:1). Turnos llenos en #005CD4 con texto blanco (6:1).
- Sin franjas laterales de acento (se sacaron de la fuente). Sin cambios de precio, condiciones ni datos del ejemplo.


## Revisión v12 · Cinco paquetes y Analítica completa

Pedido: Canales queda corto, tiene que ser analítica en general (de dónde te visitan, canales, edades, todo lo que den Google Analytics y Search Console). Horarios libres pasa a ser parte de Pulse. Menos ítems en el menú: empaquetar donde corresponda.

- **Menú de 9 a 5:** Pulse (Tu semana · Horarios libres), Analítica (Visitas y canales · Resultados), Clientes, Campañas (Campañas · Automatizaciones · Plantillas), Fidelización. Cada paquete con pestañas internas. Los enlaces viejos (#canales, #horarios, #plantillas…) abren el paquete y la pestaña correctos.
- **Analítica (reemplaza Canales):** relato del mes; de dónde llegan las reservas (incluido en el plan); quiénes te visitan (edad, género, primera vez o ya te conocían, ciudad, dispositivo); qué servicios miran y cuántos reservan, con el caso Alisado (muchas visitas, pocas reservas); cuándo te visitan (pico domingo de 20 a 23 h, con botón a Campañas); de la visita a la reserva (2.140 → 1.050 → 412 → 244, y las 168 sin terminar conectadas con la receta de Resultados); qué buscan en Google. Nota de fuentes al pie.
- **Datos coherentes:** 2.140 visitas (suma de canales), 244 reservas online, receta de reservas sin terminar con 21 envíos y 7 reservas (igual que Resultados).
- **Documento:** tabla Qué suma por paquete (6 filas en lugar de 9), pasos de Cómo funciona, mapa y guías de «Ver cómo se conecta» con 5 paquetes, resumen del ejemplo.
- **Para decidir:** Flash ya tiene una Analítica de ventas y reservas (¿pestaña ahí o dentro de Marketing?); hoy Cyclone solo lee visitas y fuentes de GA4: Search Console no está conectado y edad/género requieren Google signals y revisar la política de privacidad. Precio y consumo se juntaron en una sola decisión.


## Revisión v13 · Cada cosa en su lugar de Flash

Pedido: Pulse con dos secciones no tiene sentido; Horarios libres probablemente merece su módulo. Revisar a fondo el empaquetado para que todo tenga sinergia.

Relevamiento de Flash y Cyclone (navegación real): Pulse es una tarjeta en Inicio; Clientes y Analítica están en «Mi negocio»; «Marketing y comunicación» ya tiene Mensajes automáticos (incluye un recordatorio para volver a reservar), Descuentos (códigos, Precios dinámicos, Ofertas beta), Tarjetas de regalo, Fidelización (beta), Contenido IG (ya calcula horarios libres para historias), Seguimiento y Reseñas. No existen: campañas, lista de espera, referidos entre clientes, recuperación de reservas sin terminar, reporte de reservas por canal (el dato existe en bookings.channel) ni pantalla de fuentes de visita (GA4 ya las calcula), ni Search Console.

Criterio: PRO+ no agrega un menú aparte. Potencia cinco lugares que ya existen y suma solo dos secciones nuevas.

- **Inicio › Pulse:** una sola vista, sin pestañas. Cada oportunidad abre la acción que corresponde.
- **Mi negocio › Clientes:** grupos, base contactable e invitación preparada.
- **Mi negocio › Analítica:** pestaña Marketing (visitas y canales) y Resultados.
- **Marketing › Campañas (nueva):** invitaciones puntuales a un grupo.
- **Marketing › Mensajes automáticos:** pestañas De marketing (automatizaciones y recetas), De tus reservas (lo que ya existe, igual que hoy) y Plantillas. El recordatorio para volver puede pasar a la receta «Invitar a volver».
- **Marketing › Horarios libres (nueva):** oferta de último momento y lista de espera, con atajos a lo que ya existe: Precios dinámicos si el hueco se repite y Contenido IG para la historia.
- **Marketing › Fidelización:** club incluido, más referidos entre clientes.

Documento: tabla «Qué suma» con siete filas que dicen dónde vive cada cosa, pasos de Cómo funciona, guías y mapa de lectura con siete lugares, y ocho decisiones internas (se suman Mensajes automáticos y Horarios libres como modelo nuevo sobre Ofertas).
