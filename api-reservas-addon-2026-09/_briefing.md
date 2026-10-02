# Conexiones Ágora — propuesta vigente

Actualización: 2 de octubre de 2026 (revisión de UI/UX y wording).

## Objetivo y audiencia
Propuesta para el equipo de Ágora, escrita para profesionales sin conocimientos técnicos. Un adicional transversal de conexiones: integraciones propias en ChatGPT, Zapier, Make y n8n, más API para sistemas propios. Esta definición reemplaza el recorrido anterior de copiar contexto, configurar GPT Actions o usar pedidos HTTP genéricos.

## Alcance propuesto
- Conectar la propia cuenta y autorizar datos. Ágora construye y mantiene conectores reutilizables; cada profesional elige sus destinos y automatizaciones.
- Agenda, disponibilidad, catálogo, clientes e información de ventas/cobros. Cambios de reservas y clientes desde automatizaciones y API. ChatGPT comienza con consultas.
- Avisos de cambios, historial, filtros, permisos por negocio y sucursal, revocación y control del adicional desde el servidor.
- Precio a validar: ARS 20.000 por mes y negocio, adicional al plan. Impuestos y condiciones pendientes. Servicios externos cobrados por cada proveedor.
- Cupos propuestos: 5.000 consultas y 100 cambios exitosos diarios por negocio, compartidos entre herramientas. Se elimina el tope previo de dos conexiones; capacidad de avisos y conexiones simultáneas pendiente de dimensionar antes de fijar la oferta.
- Piloto propuesto: reserva reprogramada actualiza su fila en Google Sheets mediante Zapier, sin duplicados.

## Presentación
Revisión de UI/UX y wording (2 de octubre de 2026). El recorrido sigue el orden en que lo lee alguien sin contexto:
1. **Portada**: qué es en una frase, botón a los ejemplos y a las decisiones, y un resumen «En 30 segundos» (qué es, para qué, cuánto, estado).
2. **01 · Qué permite**: tres tareas (preguntar, no cargar dos veces, operar desde afuera) y cinco ejemplos nombrados por resultado, no por herramienta. Cada ejemplo muestra cómo se configura, una maqueta ilustrativa y «Qué necesitás».
3. **02 · Cómo funciona**: activar → conectar → elegir permisos; la regla del adicional (con / sin); tabla de qué datos se ven y cuáles se cambian; glosario de seis palabras.
4. **03 · Límites**: 5.000 consultas, 100 cambios, 1 negocio, y qué pasa al llegar al límite.
5. **04 · Qué no incluye**, con el porqué de cada exclusión.
6. **05 · Precio**: tarjeta de precio con lo incluido, piloto y lo pendiente para publicar.
7. **06 · Para decidir**: las tres preguntas, destacadas.
8. **Anexo técnico** al final y plegado: resumen de la API (11 consultas, 5 cambios, 11 avisos), explorador de 16 operaciones y 11 avisos, protección del acceso, reglas, pruebas antes de cobrar y requisitos de cada plataforma.

Vocabulario unificado: adicional, integración, consulta, cambio, aviso, API. El alcance comercial (precio, límites, operaciones, exclusiones y decisiones) no cambió. Rutas y payloads siguen siendo un contrato propuesto, no endpoints disponibles.

Los ejemplos son independientes, ficticios y sin solicitudes externas. No son capturas de Flash ni interfaces oficiales de terceros. La marca usa Montserrat, Frost y el SVG oficial de Ágora.

## Publicación y requisitos
La presencia en los catálogos requiere desarrollo y revisión de cada plataforma. Zapier y n8n requieren textos de sus conectores en inglés; el nodo verificado de n8n tiene código público. ChatGPT admite acceso a una cuenta paga existente, sin vender suscripciones dentro del plugin ni recargos exclusivos de ese canal. Las acciones disponibles se validan por proveedor.

La API administrativa interna no forma parte de esta propuesta. No incluye procesar tarjetas, ejecutar devoluciones, fichas sensibles, stock, comisiones, cursos, recurrencias, planes mensuales o packs. Algunas de estas capacidades ya existen en Ágora; aquí se delimita exclusivamente su acceso mediante las nuevas integraciones.

## Evidencia de esta revisión
339 comprobaciones del prototipo en 1280, 390 y 360 px: cinco recorridos y las cuatro vistas de cada operación; JSON parseable, sin desborde de página ni errores JavaScript. Montserrat cargada. Teclado, copia exacta, expansión y enlaces antiguos comprobados. Capturas completas y vistas por proveedor inspeccionadas; corregido espaciado del título móvil. Además, 24 comprobaciones específicas del catálogo: búsqueda sin tildes, filtros, selección, estado vacío, error por adicional inactivo y apertura/reapertura desde el enlace. Capturas del resumen, acceso y catálogo inspeccionadas en escritorio y móvil. No se probaron conectores o APIs productivas.

## Estado
La versión anterior está publicada en GitHub Pages (Metamorpho, con noindex) desde el commit 9340586. Esta revisión todavía no se publicó: por incluir funcionalidades no lanzadas y un precio propuesto, requiere autorización explícita antes del push. No contiene métricas internas ni datos de clientes.
