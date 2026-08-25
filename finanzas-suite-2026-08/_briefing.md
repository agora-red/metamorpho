# Finanzas — solución end-to-end (v3, from scratch)

> **Actualización 2026-08-06 · el módulo pasó a llamarse “Finanzas”.** El nombre “Cobros” colisionaba con
> `Medios de cobro` (un ítem que ya existe en el rail) y dejaba afuera gastos y caja. La propuesta de naming e IA
> completa —con las alternativas evaluadas y el regrupamiento de Actividad y Analítica— vive en
> `docs/design-studio-outputs/finanzas-naming-ia-2026-08/`. Dentro del módulo también cambiaron dos vistas:
> **Caja** (era “Arqueo de caja”). El resto de este documento sigue
> vigente tal cual; donde dice “Cobros” como nombre del módulo, leer “Finanzas”.

**Pedido de JP (2026-08-04):** solución end-to-end para (i) análisis y gestión de **cobranzas**, (ii) **arqueo de caja**, (iii) **ingresos y gastos**. Base funcional: el prototipo `cobros-prototype-2026-07`, pero **rehecha desde cero**, más robusta, con **estructura de Square** y **lenguaje visual de Airbnb**, contemplando nuestro modelo de negocio (servicios, productos, cursos online, capacitaciones) y nuestros medios de cobro (efectivo, transferencia, Mercado Pago).

- **Tipo**: prototipo funcional de producto — `index.html` self-contained
- **Audiencia**: interna (JP + producto + ingeniería) — insumo para el PRD
- **Entregable**: 6 vistas navegables, datos derivados de un ledger único, interacciones reales

---

## 1. Qué cambia respecto de v2 (por qué "desde cero" y no un retoque)

v2 resolvía **reporting** de plata: mirabas lo que ya pasó. Los 3 pilares que pide este pedido son **operación**: cobrar lo que falta, cerrar la caja, y controlar el resultado. Tres cambios estructurales:

| | v2 (`cobros-prototype-2026-07`) | v3 (este) |
|---|---|---|
| **Cobranzas** | Un tile "Por cobrar $166.500" suelto | Módulo propio: aging, estados, acciones (link MP / recordatorio WA / registrar cobro), cobranza recurrente de planes, tasa de recupero |
| **Arqueo** | Total contado a mano, sin contexto | Sesión de caja real (apertura/fondo/paid-in/paid-out/cierre), **diferencia en vivo**, motivo obligatorio sobre umbral, historial derivado del ledger |
| **Ingresos y gastos** | Tabla de gastos + categorías | **Resultado base caja** mes a mes por categoría, gastos recurrentes con vencimiento, origen del dinero, comisiones de cobro estimadas |
| **Datos** | `R.hoy/semana/mes` hardcodeados por rango | **Un solo ledger** (`MOVS`) del que se derivan TODOS los números por rango. Nada puede descuadrar por construcción |

Lo que **sí se conserva** de v2 (5 rondas de feedback ya lo validaron): la paleta categórica por medio de pago, la separación Estado (Actividad) vs. Acreditación, la honestidad "confirmado / API / estimado", el drill-down universal, el toggle de persona, y la cascada de neto.

---

## 2. Arquitectura de información (base Square)

Square separa lo que en Ágora hoy está mezclado: **Transactions** (ledger) · **Invoices** (cobranzas) · **Banking** (dónde está la plata) · **Cash drawers** (arqueo) · **Reports** (análisis). v3 adopta esa separación con 6 vistas:

| Vista | Equivalente Square | Qué resuelve | Pilar |
|---|---|---|---|
| **Resumen** | Reports › Sales summary | Cascada de neto + tendencia + composición | análisis |
| **Cobranzas** | Invoices (unpaid/overdue) | Qué te deben, quién, hace cuánto, y qué hacés al respecto | **i** |
| **Ventas** | Transactions | Ledger unificado con filtros ricos + export | análisis |
| **Ingresos y gastos** | Reports › Accounting + Cost of goods | Resultado base caja, categorías, recurrentes | **iii** |
| **Arqueo de caja** | Cash Management + Cash drawer reports | Cerrar el día con el efectivo contado | **ii** |

**Descartado explícitamente de Square** (ya relevado en `docs/square-explore/DOSSIER.md`): el arqueo atado a cajón físico (Ágora no tiene ni tendrá hardware — el nuestro es 100% software) y el modelo de *transfer batches* (MP nos da disponible/por liberarse continuo, que le queda mejor a nuestro caso).

**Saldos, eliminada** (decisión JP, 18/ago): era una vista propia con el timeline de liberaciones de MP, la
acreditación estimada del posnet y el explicador de certeza. Lo que sobrevive es el strip **"Dónde está la plata
ahora"** dentro de Resumen. Un saldo pasa a ser un resumen, no una sección.

**Sin ledger de acreditación** (decisión JP, 18/ago): se sacó la distinción *disponible / por liberarse* de Mercado
Pago y la acreditación estimada de las tarjetas — de todo el módulo, no solo de la vista. Cayeron con eso el campo
`settle`/`rel` del ledger, la columna y el filtro de Acreditación en Ventas, los chips por fila y el concepto
del glosario. El strip de saldos queda con **dos tiles**: efectivo en caja y por cobrar, que son los únicos que el
módulo puede afirmar — uno se cuenta y el otro se registra. Cuándo Mercado Pago o el banco liberan la plata es un
dato que hoy no tenemos, y el módulo dejó de fingir que sí.

---

## 3. Los tres pilares en detalle

### i. Análisis y gestión de cobranzas

Un **cobrable** (receivable) es plata de algo **ya entregado** que quedó sin cobrar. Solo dos orígenes lo generan:

| Origen | Cómo nace el cobrable |
|---|---|
| Servicio (turno) | Seña cobrada, saldo pendiente |
| Producto | Entregado "a cuenta" |

**Los que NO generan cobrable** (decisión JP, 20/ago — *"solo permitimos pago online para esos assets"*): los
**cursos**, las **capacitaciones**, los **descargables** y las **gift cards** se cobran 100% online y por
adelantado —sin pago no hay acceso, así que la venta nunca puede quedar a medias—. Los **planes mensuales** se
cobran solos por Mercado Pago: si el cobro falla se reintenta y, si sigue fallando, el plan se pausa. En ningún
caso queda un saldo que perseguir, así que no ensucian la lista.

La regla está codificada, no solo escrita: `ORIGENES_CON_SALDO = ['servicio', 'producto']` filtra la lista, y el
modal *Registrar cobro* esconde el campo "¿queda saldo pendiente?" cuando el tipo de venta elegido es de pago
online (muestra en su lugar por qué no aplica).

> **Nota de modelado (20/ago):** en Ágora **Eventos y Capacitaciones son el mismo asset** — el nav muestra un
> nombre u otro según el plan (`isEventPlan`), pero ambos van a `/eventos`. En el prototipo estaban separados;
> se unificaron. **Descargables** faltaba y se agregó.

**Filtro por fecha** (pedido JP, 20/ago): Por cobrar toma el mismo selector de período que el resto del módulo,
y **el rango filtra por fecha de la venta** (no de vencimiento: no existe). Como el saldo total es un *balance* y
no un flujo, el KPI **Total por cobrar** no se recorta con el rango — muestra el total abierto y desglosa cuánto
viene de ventas del período y cuánto de antes, con un atajo *Ver los N* que abre el rango a **Todo**.

**Sin seguimiento y sin vencimientos** (decisión JP, 18/ago): V1 no persigue el cobro. Se sacaron las fechas de
vencimiento, los estados de seguimiento (recordado / prometido), los recordatorios automáticos y la lógica de
incobrables. La vista se llama **Por cobrar**, no "Cobranzas": es una foto de cuánto falta entrar y de quién, no
una agenda. Cuando el cliente paga, se registra el cobro y la fila se cierra. La palabra "Cobranzas" queda
reservada para cuando exista la gestión.

### ii. Arqueo de caja

Modelo de **sesión** (ya existe en la DB: `cash_sessions` / `cash_movements` / `cash_audit_log`):

1. **Apertura** — fondo inicial, quién abre, hora.
2. **Durante el día** — cobros en efectivo (paid in), gastos y retiros en efectivo (paid out). Todo lo que no es efectivo **no se arquea** pero se muestra como contexto del día.
3. **Cierre** — cálculo del esperado (`fondo + cobros ef − gastos ef − retiros`) vs. el **total contado**, que se carga a mano; la diferencia se calcula en vivo y el **motivo es obligatorio** si supera el umbral configurable. (El conteo por denominación se evaluó y se descartó — decisión JP, 20/ago.)
4. **Historial** — cada cierre queda como fila navegable con quién abrió/cerró, esperado, contado, diferencia y motivo; más la **diferencia acumulada del período** (la métrica que detecta el faltante sistemático).

Solo el efectivo se arquea. La caja se lee 100% del ledger (una corrección posterior reacomoda los totales del día, pero el snapshot del cierre queda intacto como registro histórico).

### iii. Ingresos y gastos

- **Resultado base caja** (percibido, no devengado) mes a mes: ingresos por tipo de venta → total; gastos por categoría → total; **neto**. Con delta vs. mes anterior.
- **Comisiones al equipo** — cada profesional tiene un esquema (% sobre servicios y packs, % menor sobre
  productos). La comisión **se devenga con cada cobro** y se **paga** en una liquidación que entra al ledger como
  gasto de "Sueldos y comisiones". El saldo de cada uno es `devengado − pagado`, sin fecha de corte. Vive como
  sub-vista de *Ingresos y gastos* (solo persona "local con equipo"); el esquema se configura en Equipo. Con esto,
  la línea "Sueldos y comisiones" del resultado deja de ser un monto inventado y pasa a derivarse del ledger.
- **Sin costo de cobro** (decisión JP, 18/ago) — se sacó todo cálculo de comisión de Mercado Pago. MP la informa
  en `fee_details`, pero Cyclone todavía no la persiste, y la del posnet propio no la vemos nunca. Antes que mostrar
  un porcentaje inventado, el módulo no descuenta nada y lo dice en la cascada. Como consecuencia, "Neto del período"
  es un único número: el KPI del Resumen, el cierre de la cascada y el pie del resultado dan idéntico.
- **Categorías** gestionables (alquiler, insumos, sueldos y comisiones, servicios, marketing, impuestos, mantenimiento, otros).
- **Gastos recurrentes** con próximo vencimiento y registro en un click.
- **Origen del dinero**: todo gasto declara de dónde sale (Caja / Banco / Mercado Pago) — es lo que mantiene el arqueo y los saldos consistentes.

### Vocabulario — una palabra por concepto

El módulo venía usando "venta" y "cobro" como sinónimos, y eso hacía que dos números correctos
parecieran contradictorios. Como es **base caja**, todo lo que muestra es plata que entró, así que
donde decía "ventas" ahora dice **cobrado**: `Ventas del período` → `Cobros del período`,
`Por tipo de venta` → `Cobrado por tipo de venta`, `Ventas por profesional` → `Cobrado por profesional`,
`Total ingresos` → `Total cobrado`.

La distinción que había que declarar: una **venta** es el hecho comercial (existe aunque no te hayan
pagado), un **cobro** es el movimiento de plata (tiene su propia fecha y medio). Una venta puede
generar dos cobros en meses distintos — por eso "Cobrado" de un período nunca es igual a "lo que
vendiste" en ese período, y los dos números están bien.

La vista **Conceptos** (7ª tab) declara los 16 términos del módulo agrupados en cuatro bloques, cada
uno con qué es, **con qué NO hay que confundirlo** y **un ejemplo concreto** — no un "lo ves en X":
una referencia de navegación no enseña nada, un caso sí. Arranca con la venta de Antonella dibujada como
una barra partida en **seña cobrada** y **saldo pendiente**, más el cobro del saldo como un tercer
momento: es la forma más directa de mostrar que una venta no es un cobro. No tiene filtro de rango: un
glosario no depende del período.

---

## 4. Medios de cobro — decisión explícita

JP nombró tres: **efectivo, transferencia, Mercado Pago**. Son los tres de primera clase en toda la UI (paleta, arqueo, saldos, cascada).

`CashMethodE` además tiene `credit_card` / `debit_card` / `prepaid_card` — el **posnet propio del negocio**, que Ágora no procesa pero sí registra (migración `1784200000000`). El prototipo los agrupa como **"Tarjeta (posnet propio)"**, visibles en el ledger y en acreditación estimada, marcados como plata que Ágora no ve entrar. Ignorarlos rompería las sumas de los negocios que ya los usan. **A confirmar con JP**: si se sacan, es borrar un grupo, no rediseñar.

---

## 5. Dirección visual — Airbnb sobre marca Ágora

Se abandona el glassmorphism de v2 (peleaba con la nitidez que pide Airbnb) y se adopta:

- **Fondo blanco puro** en toda página y bloque de texto, sin gradientes ni blobs — cumple `feedback_design_no_gradients` y `feedback_design_text_contrast` de una.
- **Superficies por hairline**, no por color: `1px solid #e9e9e9` + radio 16px + 24–28px de padding. Sombra **solo en hover** de lo clickeable (lift de 2px).
- **Barra de filtros tipo píldora**, sticky, con blur — el patrón de búsqueda de Airbnb aplicado a rango/medio/estado/profesional.
- **Panel resumen sticky a la derecha** (el "price breakdown" de Airbnb) en el detalle de cobranza y en el conteo del arqueo.
- **Botón secundario outline negro** (`Mostrar todo`), primario en `--primary` de Ágora.
- **Tipografía**: Montserrat display para números y títulos, Space Mono para labels técnicos, fechas y códigos. Números siempre `tabular-nums`.
- **Coral `#ff4658`** reservado a vencido/alerta (es el rojo que Airbnb usa para lo urgente, y es color de marca Ágora).

**Paleta categórica por medio de pago** — heredada de v2 y **re-validada** con `dataviz/validate_palette.js` sobre blanco (5 slots, ALL CHECKS PASS, peor par adyacente ΔE 12.7 deutan / 19.5 normal):
`efectivo #0d8f74` · `Mercado Pago #0072fb` · `transferencia #8a6d00` · `crédito #7c5cff` · `débito #0089b3`.
Reservada **exclusivamente** a medio/destino. Las magnitudes van en azul único; el aging de cobranzas usa rampa secuencial de urgencia con etiqueta directa (nunca color solo).

---

## 6. Cómo está construido el prototipo

- **Un solo ledger** (`MOVS`, ~1.100 movimientos generados con PRNG sembrado sobre 2026-06-01 → 2026-08-04) del que se derivan KPIs, cascada, charts, breakdowns, saldos, P&L y arqueo. **Ningún número está hardcodeado**: cambiar el rango recalcula todo desde la misma fuente, así que no puede haber descuadre entre vistas.
- **Cobrables** (`RECV`) y **historial de cierres** (`SESSIONS`) sí están escritos a mano — necesitan especificidad narrativa (cliente, motivo, promesa de pago).
- Interacciones reales: filtros + orden + búsqueda + paginado en Ventas, drill-down desde cualquier métrica, drawer de detalle de cobranza, modales de gasto/cobro, **conteo de arqueo con diferencia en vivo**, toggle de persona (local con equipo / profesional independiente) y de rango.
- Sin dependencias externas salvo Google Fonts. Charts en SVG inline con tooltip propio.

---

## 7. Qué queda fuera del prototipo (y por qué)

- **Comisiones al equipo**: se muestran como gasto (categoría "Sueldos y comisiones"), no como módulo — la gestión vive en su propio módulo (decisión de la Ronda 4 de v2).
- **Facturación / AFIP**: es otro problema (devengado, fiscal). Cobros es base caja.
- **Multi-sucursal**: el filtro existe en la barra pero con una sola sucursal cargada.
- **Conciliación bancaria automática**: requiere feed bancario, no lo tenemos.
</content>
</invoke>

### Espacios seguros — el layout no salta entre navegaciones

Pedido JP (24/ago): *"mantener espacios seguros, evitar saltos visuales entre navegaciones como el cambio
en un toggle por cantidad de renglones"*. El módulo tenía cuatro fuentes de reflow, todas medidas y cerradas:

| Qué saltaba | Por qué | Cómo se resolvió |
|---|---|---|
| El header, 25px al entrar y salir de Caja | La bajada (pill de caja abierta) solo existe en esa vista | `min-height` reserva el renglón en todas |
| El panel de filtros, al tocar un toggle de la vista | Ingresos y gastos sacaba el campo *Profesional* en la sub-vista Categorías | El set de campos es fijo por vista; el filtro aplica en las tres |
| El panel, al activar o limpiar el filtro de *Tipo* en Ventas | Ese campo aparece solo si llegaste con un tipo elegido desde el Resumen | Slot reservado (`.ffield.hold`) que ocupa su lugar cuando no está |
| El box de filtros, a cada cambio | *Limpiar filtros* aparecía y desaparecía | Siempre presente, deshabilitado cuando no hay nada que limpiar |
| El ancho del contenido, al entrar a Conceptos | Sin filtros, la vista pasaba a ancho completo | La columna se reserva siempre dentro de Finanzas |
| Mobile: el contenido arrancaba 47px más abajo en 3 vistas | Las vistas con tres botones wrappeaban a dos filas | Los botones se reparten el ancho en una sola fila |

Además la navegación entre vistas resetea el scroll de forma instantánea, no animada: con `smooth` el
contenido ya se había cambiado y la página se deslizaba después, que se lee como un salto.

**Verificado:** el alto del header y el inicio del contenido son idénticos en las 7 vistas, en 1440, 1200 y
390px. El panel de filtros no cambia de alto por ninguna acción dentro de una misma vista.

### Acciones — una por sección, donde vive el dato que crean

Diagnóstico del estado actual en Flash (`CashRegister.tsx`): las 6 acciones viven juntas en Caja, pero
**5 de las 6 aceptan transferencia o Mercado Pago**, o sea que no mueven el cajón. La única con el medio
fijado en efectivo es *Retiro de efectivo*. Además *Ingresar venta* navega afuera (`/productos/ingresar-venta`)
y *Pago por comisiones* pide un monto libre, sin relación con el devengado.

Y falta la contracara del retiro: para reponer el fondo hay que usar *Registrar ingreso*, que lo cuenta como
ingreso del negocio e infla el resultado.

**Criterio:** cada acción vive donde vive el dato que crea. Caja solo suma lo que mueve el cajón físico; el
resto llega solo, porque si el medio es efectivo el movimiento entra al arqueo por el mismo ledger.

| Sección | Acciones | Gating |
|---|---|---|
| Resumen | — | es lectura |
| Ventas | **Registrar venta** · Exportar | — |
| Por cobrar | **Registrar cobro** · Exportar | — |
| Ingresos y gastos | **Registrar ingreso** · **Registrar gasto** (ambas primarias) · Exportar | — |
| Comisiones | **Liquidar comisiones** · Exportar | solo venue |
| Caja | **Reposición de fondo** · **Retiro de efectivo** | `cash_register_enabled` + caja abierta |
| Conceptos | — | es documentación |

*Registrar venta* y *Registrar cobro* dejan de ser el mismo modal: la primera da de alta una venta y, si queda
saldo, crea el cobrable; la segunda no pregunta qué vendés —la venta ya existe— y solo toma cuánto entra y con
qué medio, validando contra el saldo abierto. *Liquidar comisiones* precarga el devengado menos lo pagado en vez
de pedir un monto libre. *Reposición de fondo* y *Retiro de efectivo* suben y bajan el efectivo esperado **sin
tocar el resultado** (van al array `EXTRA`, separado del ledger de resultado).

Abrir y cerrar caja siguen en la vista, no en el header: ahí vive el flujo instructivo de la sesión.

**Un ingreso manual no es una venta.** Entra al resultado y al arqueo, pero se excluye de Ventas y del selector
de *Registrar venta*. Si apareciera en las dos, el total de ventas dejaría de cerrar contra el ledger.

### Ingresos y gastos — por qué queda en una sección y no en dos

Pregunta de JP (24/ago): *"¿mejoraría si separamos ingresos y gastos en dos secciones? Queda raro
resultado · gastos · categorías, sin un espacio propio para ingresos y con categorías relacionado
exclusivamente a los gastos."* El diagnóstico es correcto; la solución no es partir la sección.

**Contra separarlas:** el valor de la vista es que los dos lados se miden con el **mismo criterio**
(base caja) y en el mismo lugar. Separadas, el neto se queda sin casa —o hay que inventarle una tercera
sección—, y "Ingresos" en el rail choca de frente con **Ventas**: serían dos entradas para la misma plata
con criterios distintos, que es justo la confusión que el módulo viene resolviendo.

**Lo que sí estaba mal era el eje del toggle:** mezclaba un análisis de los dos lados (Resultado), uno de
un solo lado (Gastos) y un ABM de configuración (Categorías). Ahora el eje es uno solo:

| | Qué muestra |
|---|---|
| **Resultado** | El neto: ingresos − devoluciones − gastos, mes a mes |
| **Cobros** | El lado que entra: el detalle de cada cobro, uno por fila |
| **Gastos** | El lado que sale: por categoría, de dónde salió, más la lista |

**Categorías salió del toggle.** Es configuración de los gastos, no una vista: se abre desde el desglose por
categoría, dentro de Gastos. Un ABM no compite por atención con dos vistas de análisis.

La sub-vista **Ingresos** también cierra un hueco que abrimos al sacar los ingresos manuales de Ventas: eran
el único movimiento del ledger sin ningún lugar donde verse listado. Ahora tienen el suyo, con un aviso que
explica por qué no aparecen en Ventas. Los tres desgloses reconcilian: total = por tipo = por medio.

**La pestaña se llama Cobros, no Ingresos** (JP, 24/ago). *Ingreso* es la línea del resultado; *cobro* es el
hecho que la compone, y la pestaña lista hechos: una fila por cada vez que entró plata. Además evita que la
pestaña repita el nombre de la sección, que era parte de lo que se leía raro. Cada fila trae el detalle
completo —fecha y hora, concepto, cliente, tipo de venta, profesional, medio, a qué cuenta entró, y si lo
capturó Ágora o lo cargó el negocio a mano— y se abre en la ficha del movimiento.

*Cómo se registró* se deriva del medio, no de un campo suelto: **automático** son los cobros online y los de
Mercado Pago, que Ágora captura sola; **a mano** el efectivo, las transferencias y el posnet, que carga el
negocio. En el dataset da 246 / 309, así que la columna separa de verdad.

**Cobros queda solo con la tabla** (JP, 24/ago). Los desgloses por tipo y por medio ya viven en Resumen; acá
repetían el mismo corte y empujaban el detalle —que es lo que la pestaña aporta— abajo del pliegue.

**Ventas: el tipo de venta pasa a columna propia**, ordenable, con chip coral para distinguir las devoluciones.
Antes era un subtítulo gris debajo del concepto, mezclado con el nombre del cliente. Junto con la columna vuelve
el **filtro de Tipo de venta** como filtro fijo del panel (multi-select), correlativo a la columna — revierte la
decisión del 17/ago de sacarlo, que lo dejaba visible solo si llegabas con un tipo elegido desde el Resumen.
Con el filtro fijo desaparece también el slot reservado `.ffield.hold`: el panel ya no cambia de alto.
La opción *Ingresos manuales* no está en el filtro porque no son ventas y no entran en esta lista.

### Split final: Cobros · Gastos · Resultado (JP, 24/ago)

*Ingresos y gastos* se parte en **tres secciones del rail**, y el toggle de sub-vistas desaparece:

```
Resumen · Ventas · Por cobrar · Cobros · Gastos · Comisiones · Resultado · Caja · Conceptos
```

Esto revierte mi recomendación de mantenerlas juntas, y con razón: mi objeción principal era que "Ingresos"
en el rail chocaba con Ventas y que el neto se quedaba sin casa. Las dos cosas se caen solas acá — la sección
se llama **Cobros**, que no se confunde con Ventas, y el neto tiene su propia sección, **Resultado**, en vez
de ser una pestaña adentro de otra cosa.

| Sección | Qué muestra | Acciones |
|---|---|---|
| **Cobros** | Cada vez que entró plata, una por fila, con el detalle completo | Exportar · Registrar ingreso |
| **Gastos** | Cada salida, por categoría y de qué cuenta salió | Exportar · Registrar gasto |
| **Resultado** | El neto mes a mes + comisiones sin liquidar | Exportar |

*Registrar ingreso* queda en Cobros y no se renombra a "Registrar cobro": eso ya es la acción de **Por cobrar**,
que cierra un saldo existente. Acá se da de alta plata que entró y no viene de una venta.

Los tiles del Resumen ahora linkean a la sección donde el número coincide exactamente: *Cobrado* → Cobros
(antes iba a Ventas, que da $39.577.000 porque excluye los ingresos manuales), *Gastos* → Gastos,
*Neto del período* → Resultado. Verificado: $40.180.100 − $46.200 − $2.695.900 = $37.438.000 en las tres.

### El Resumen deja de solo contar: qué hacer, y de dónde sale la plata (JP, 25/ago)

Se sacó la caja de total del panel de filtros en las 6 secciones que la tenían: repetía un número que
la vista ya muestra. El panel filtra; los números viven en la vista.

**Necesita tu atención.** El Resumen contaba qué pasó, no qué hacer. Ahora abre con un bloque de líneas
accionables, cada una derivada del ledger o del estado de la caja — si el hecho no es cierto, la línea no
existe. Ocho reglas:

| # | Dispara cuando | Manda a |
|---|---|---|
| 1 | Hay ventas entregadas con saldo (marca cuántas no pagaron ni seña) | Por cobrar |
| 2 | Hay comisiones devengadas sin liquidar *(solo venue)* | Comisiones |
| 3 | La caja quedó abierta | Caja |
| 4 | El último arqueo no coincidió (con el motivo) | Caja |
| 5 | El resultado del período es negativo | Resultado |
| 6 | Una categoría de gasto creció ≥50% contra el período anterior de igual largo y pesa ≥8% del total | Gastos |
| 7 | Un gasto fijo cuyo día habitual ya pasó no está registrado este mes | Registrar gasto |
| 8 | Se registró efectivo con la caja cerrada (entra en el próximo arqueo) | Caja |

Quedó **fuera a propósito** la antigüedad de la deuda (decisión del 6/ago: V1 no persigue cobranzas) y
cualquier métrica acumulada de diferencias de caja (decisión del 12/ago). La regla 4 mira solo el último
cierre, que es un hecho, no una tendencia.

**Qué te da la plata.** El corte por tipo de venta dice *Servicios 63%*, que es demasiado grueso para
decidir algo. La card nueva corta por **concepto** —qué servicio puntual— sobre lo cobrado del período, con
el porcentaje que concentran los seis primeros, y cada fila abre Ventas filtrado por ese concepto.

### Los filtros categóricos viven en la columna (JP, 25/ago)

*Tipo de venta*, *medio* y *profesional* en Ventas, *origen* y *profesional* en Por cobrar, y *profesional*
en Cobros salieron del panel y se filtran **desde la cabecera de su columna**: se filtra donde se lee el dato.

- **Un solo popover**, `position: fixed` colgado del `body`. La tabla vive dentro de un contenedor con
  `overflow-x`, así que un dropdown anclado adentro quedaría recortado. Se reposiciona solo en scroll,
  en resize y después de cada render, y elige abrir hacia arriba o hacia abajo según el espacio.
- **Estado visible sin abrirlo**: la cabecera activa se convierte en una pastilla azul con el número de
  opciones elegidas. Cada columna trae su propio *Limpiar*.
- **Una sola afordancia por cabecera**: las columnas filtrables dejaron de ser ordenables. Ordenar sigue
  donde sirve — fecha, cliente y monto. Filtrar una columna categórica vale más que ordenarla.
- **En mobile no cambia nada**: la tabla scrollea de costado, así que esos campos se quedan en el modal de
  filtros, donde son alcanzables. `panelSpec.cols` los saca del panel de desktop y los deja en el modal.

De paso, en Por cobrar *Origen* y *Profesional* pasaron a ser columnas propias: estaban escondidos en el
subtítulo del concepto y no se puede filtrar por una columna que no existe.

### Comisiones: la curva del saldo (JP, 25/ago)

Las tarjetas por profesional invierten la jerarquía: arriba y grande, **lo que falta liquidarle**; abajo y
chico, **lo que cobró en el período** (cobros, no ventas). El número que decide una acción va primero.

Se agregó un lede que fija el alcance: **solo devengan comisión los servicios, sus adicionales y los
productos**. Cursos, capacitaciones, descargables y gift cards no tienen profesional asignado.

**El gráfico** es una sola serie: el saldo pendiente día a día del profesional o los profesionales
seleccionados. Sube con cada venta que devenga y **cae de golpe en cada liquidación**, que es el impacto que
se quería ver; los pagos van marcados con un punto coral y una guía punteada. Arranca del saldo real
acumulado antes del período, así que el último punto coincide exactamente con el saldo de la tarjeta —
verificado: $2.490.960 en las dos. Un solo eje, todo en pesos; tooltip por día; etiqueta directa en el
último valor en vez de rotular todos los puntos. Con rango "Hoy" no se dibuja: una curva de un punto no es
una curva.

**Las cabeceras filtrables** pasaron a llevar la pastilla siempre visible —fondo, borde, embudo y chevron—
en vez de aparecer recién en hover: una columna que filtra tiene que parecer un control desde el vamos.
Activa es azul llena con el contador. También se sacaron los márgenes negativos que la recortaban contra el
borde de la celda.

### El buscador es de la tabla, y Por cobrar deja de recortarse (JP, 25/ago)

**El buscador salió del panel** y pasó a ser una acción de la tabla: vive adentro de la card, arriba de la
cabecera, con el conteo de resultados a la derecha y un botón para limpiar. Mismo componente en desktop y en
mobile —también sale del modal de filtros— y ahora también está en **Cobros**, que no lo tenía. El foco se
mantiene mientras tipeás: el render reencuentra el input por `data-tsearch`.

**Por cobrar dejó de filtrar por período.** Al sacar el encabezado que explicaba el recorte (*"Ventas de 30
días · 2 cobrables anteriores no entran"*), mantener el rango habría escondido cobrables sin decirlo —
justo la contradicción entre cards que ya habíamos cerrado. El saldo abierto es un **balance**, no un flujo:
se muestran todos, siempre. Sin período y con los demás filtros ya en la tabla, la sección se queda sin
panel y la tabla usa el ancho completo: **1140 px contra 856**.

Esto revierte el pedido del 24/ago de sumarle el filtro de fechas. Volver a ponerlo es una línea, pero
entonces vuelve a hacer falta decir en pantalla qué queda afuera.

### El selector de fechas manda, y el panel lateral desaparece (JP, 25/ago)

El filtro de fechas pasa a ser una **barra del ancho del contenido** —el mismo que la tabla— y al abrirla
despliega el picker de producción: **atajos a la izquierda** (Todo · Hoy · Ayer · Últimos 7 días · Últimos
30 días · Mes actual · Mes anterior, las mismas etiquetas que `CalendarDatePicker`) y **calendario a la
derecha**, donde dos clicks arman un rango a medida (`RANGES.custom`). En mobile los atajos pasan a una fila
de pills que scrollea, como en producción.

Con la fecha arriba, el buscador dentro de la tabla y las categóricas en las cabeceras, **el panel lateral
se quedó sin nada**: se eliminó, junto con el modal de filtros de mobile y el botón *Filtros* del header. Lo
único que quedaba —Profesional y Sucursal— va en la misma barra, a la derecha de la fecha. Resultado: **todas
las secciones usan el ancho completo** y hay un solo lugar donde se filtra. Caja y Por cobrar no muestran
barra: no se filtran por período.

**Gastos pierde el filtro por profesional**: un gasto del negocio no es de nadie en particular.

**Cobros, Gastos y Resultado abren con la respuesta.** Cada una encabeza con la pregunta que la sección
contesta y el número en display: *¿Cuánto cobré en este período?* $40.270.100 · *¿Cuánto gasté?* $2.695.900
—con la categoría más pesada al lado— · *¿Cuál fue mi resultado?* $37.528.000, en coral si da negativo.
