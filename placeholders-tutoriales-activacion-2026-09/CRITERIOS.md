# Placeholder + Tutorial de primera activación · Criterios

Contrato para decidir **qué va y por qué** en cada pieza. Sale de las reglas de wording de `launch-copy` (skill de `/feature-launch`) y del copy que ya está en producción. Los bocetos (`index.html`) se validan contra estos criterios con un lint automático (presupuestos de palabras + palabras prohibidas).

## 0 · Principios

1. **Una sola casa por dato.** Cada dato vive en un único paso. Si aparece en dos, uno sobra.
2. **Placeholder = por qué. Tutorial = cómo.** El placeholder vende el valor; el tutorial enseña el mecanismo y prepara la decisión. Ninguna frase se repite entre los dos.
3. **Copy existente primero.** Antes de escribir texto nuevo se busca el que ya usa Flash (landing, novedad in-app, empty state). Solo se escribe nuevo donde un paso no tiene fuente. Toda pieza nueva se marca.
4. **Solo lo verificable.** Nada que el producto no haga hoy. Las limitaciones no se prometen ni se esconden: se aplican las reglas de la sección 4.
5. **Ningún dato inventado presentado como real.** Los montos, nombres y horarios de los casos son ejemplos y se marcan «Ejemplo».

## 1 · Cuántos pasos tiene el tutorial (regla determinística)

```
pasos = 2
      + 1  si la feature tiene costo, o consume un recurso medido  (→ «Costo y consumo»)
      + 1  si hay algo que decidir o tener antes de activar        (→ «Para activar»)
```

Rango 2–4. Ninguna otra cosa agrega pasos. Profundidad ≠ cantidad de información: es cantidad de decisiones y de plata (o de recursos que se gastan).

| Feature | Costo o consumo | Decisión / requisito previo | Pasos |
|---|---|---|---|
| Reseñas | Gratis, pero el pedido por WhatsApp descuenta un mensaje del pack de mensajes | Sí: dónde viven las reseñas | **4** |
| Gift Cards | No (Ágora no cobra). La comisión de Mercado Pago va como nota en «Para activar» | Sí: Mercado Pago conectado | **3** |
| Precios dinámicos | No | No: «Activar» abre un asistente de 3 pasos que ya es la configuración | **2** |
| Catálogo de productos | Sí: cargo fijo mensual (por país; Ágora UP y Car lo incluyen) | No (no se encontró ningún requisito previo). El CTA va en el paso de costo | **3** |

Orden fijo cuando existen: **Cómo funciona → Caso práctico → Costo y consumo → Para activar**. El costo y el consumo van antes de activar para que se decida con todo a la vista. El CTA principal vive siempre en el último paso que exista.

## 2 · Contrato por paso

### Paso «Cómo funciona» (siempre, siempre primero)
- **Responde:** ¿qué pasa, en qué orden y quién lo hace?
- **Va:** el mecanismo de punta a punta en 3 momentos. Un momento = un actor + una acción. Cierra con el resultado que el negocio ve.
- **No va:** costos, requisitos, excepciones, límites, configuración, ejemplos con datos.
- **Prueba:** si se borra el paso siguiente, este igual se entiende. Después de leerlo, el negocio puede explicar la feature en una frase.
- **Presupuesto:** título ≤ 8 palabras · bajada ≤ 25 · 3 momentos de ≤ 20 palabras cada uno.

### Paso «Caso práctico» (siempre, siempre segundo)
- **Rótulo:** sin rubro, «Un caso práctico»; con rubro, «Un caso para tu salón» / «Un caso para tu barbería».
- **Responde:** ¿cómo me pasa esto a mí?
- **Va:** un solo caso que recorre los mismos momentos del paso 1, con datos concretos (persona, servicio, hora o monto).
- **No va:** ningún concepto nuevo respecto del paso 1; promesas o métricas de resultado («+30% de reservas»); testimonios inventados; cifras sin marcar «Ejemplo».
- **Prueba:** cambiar el rubro cambia solo los datos (nombre, servicio, hora, monto), nunca la mecánica. Cada acción del caso existe hoy en el producto.
- **Presupuesto:** título ≤ 10 palabras · historia ≤ 45.
- **Qué caso se muestra:**
  - Sin rubro asignado → caso neutro (un cliente, un servicio, sin vocabulario de rubro). Es el default.
  - Con rubro → caso del rubro con más servicios cargados en el negocio; si hay empate, el primero cargado.
  - Se escribe un caso por grupo de rubros: Salón (Peluquería, Uñas, Pestañas, Cejas…) y Barbería. Rubro sin caso escrito → neutro. Nunca se genera un caso en el momento.

### Paso «Costo y consumo» (solo si hay costo, o si consume un recurso medido)
- **Responde:** ¿qué es gratis, qué se paga o se gasta, y qué pasa si falta el recurso?
- **Va, en este orden:** qué no tiene costo · qué se paga o se consume · unidad (y monto, solo si es plata). El plan B por falta del recurso («Sin pack, sale por correo») solo va si cambia la decisión del negocio.
- **Una feature gratuita puede tener este paso** si gasta algo que el negocio ya paga aparte (ej.: cada pedido de reseña por WhatsApp descuenta un mensaje del pack). El título describe el paso, no lo pregona: «Por dónde sale y qué usa cada canal». No se usa «Es gratis…» ni «No consume nada».
- **No va:** beneficios ni persuasión. Un monto solo si es verificable; si varía por plan o moneda se marca para confirmar o se omite. No se muestra el precio de algo que la feature no vende.
- **Costos de terceros** que el negocio ya asume en cualquier cobro (comisión de Mercado Pago) **no** generan este paso: van como una nota en «Para activar».
- **CTA secundario:** solo si hay algo que contratar («Ver packs»). Nunca activa la feature.
- **Presupuesto:** título ≤ 8 · bajada ≤ 25 · cada fila ≤ 20 palabras.

### Paso «Para activar» (solo si hay algo que decidir o tener)
- **Responde:** ¿qué necesito decidir o tener antes de apretar el botón?
- **Va:** requisitos que bloquean, decisiones que definen el resultado y restricciones **irreversibles de verdad**. Máximo 3 ítems, cada uno con estado (falta / listo).
- **Irreversible = sin vuelta atrás.** Si hay salida, no va. Ejemplo: una tarjeta de regalo vendida no se edita, pero se puede pausar y crear otra, así que tipo y monto **no** van acá.
- **No va:** explicación de cómo funciona (eso es el paso 1); ajustes que se pueden cambiar después (van en la pantalla de configuración de la feature); restricciones con salida.
- **El CTA es el de activar**, idéntico al del placeholder. Solo se reemplaza si el requisito **impide activar** (Reseñas en Google exige perfil conectado → el botón pasa a «Conectar Google»). Si el requisito no impide activar, el CTA sigue siendo el de activar y el requisito lleva una acción secundaria (Gift Cards: crear la tarjeta no exige Mercado Pago, solo vender; el botón sigue siendo «Crear mi primera tarjeta» y el ítem trae «Conectar ahora»).
- **Si no hay nada que decidir ni tener** el paso no existe y el CTA va en el último paso existente.
- **Presupuesto:** título ≤ 8 · bajada ≤ 25 · hasta 3 ítems de ≤ 25 palabras.

## 3 · Contrato del placeholder (feature apagada)

Componente estático + CTA. Orden fijo:

| Elemento | Regla | Presupuesto |
|---|---|---|
| Chip de estado + rótulo | «Apagadas» / «Sin tarjetas» + nombre de la feature | — |
| Titular | El resultado para el negocio, en su idioma, con una frase enfatizada. Nunca solo el nombre de la feature | ≤ 12 palabras |
| Bajada | El mecanismo en una oración + qué hace el cliente | ≤ 40 palabras |
| Viñetas | 2–3. Cada una un beneficio distinto o un hecho de control | ≤ 15 palabras c/u |
| Costo | Una línea por costo o consumo, con chip: «Sin costo» / «Usa mensajes» / «Incluido». Sin detalle ni montos: van en «Costo y consumo» | 1 línea c/u |
| Visual | Lo que ve el cliente final | — |
| CTA | Verbo + objeto, **idéntico** al CTA del último paso del tutorial | ≤ 25 caracteres |

No van en el placeholder: pasos, requisitos, límites ni ejemplos con números.

## 4 · Limitaciones («Qué NO hace»)

Una limitación entra al tutorial solo si cumple una de dos:
1. **Bloquea la activación** → va en «Para activar».
2. **Corrige una expectativa que el paso 1 crearía** → se dice en positivo dentro del paso 1 (ej.: «La usa al reservar online», en vez de «no se puede usar en el mostrador»).

Todo lo demás va al artículo del Centro de Ayuda («Limitaciones actuales»).

## 5 · Wording (de `launch-copy`)

| Regla | Sí | No |
|---|---|---|
| Voseo argentino | «Subí», «elegís» | «Sube», «eliges» |
| Ágora con tilde | «Ágora» | «Agora» (salvo en URLs: agora.red) |
| Tu página | «aparece en tu página» | storefront, «tienda», «Mi tienda» |
| Planes mensuales | «planes mensuales» | «membresías» |
| Concreto | «Elegís qué servicios, qué franja y cuánto descuento» | «Aprovechá las nuevas opciones» |
| Sujeto explícito | «El cliente toca una calificación y deja su reseña» | «Tocá una estrella» (se lee como orden al negocio) |
| Acción del cliente | «califica», «deja su reseña» | «toca una estrella» |
| Sin negaciones de relleno | «Sale a todo cliente con correo.» | «…No consume nada.» / «Es gratis; …» |
| Sin planes B innecesarios | (se omite) | «Sin pack, sale por correo.», salvo que cambie la decisión |
| Verbos en presente, sujeto = el negocio o el cliente | «Le pedimos la reseña» | «La plataforma gestiona el envío» |
| Sin jerga técnica | «reserva», «turno», «horario» | checkout, slot, canje, onboarding, dashboard, feature, usuario |
| Sin adjetivos vacíos | — | fácil, simple, potente, increíble, aprovechá, optimizá |
| Sin exclamaciones ni muletillas | — | «¡…!», «Ojo:», «Tené en cuenta» |
| Números | «$45.000», «9 a 13 hs», «2 horas» | — |

Vocabulario del producto: **turno** (lo que ocurre), **reserva** (lo que hace el cliente), **pack de mensajes**, **Mensajes automáticos**, **Mercado Pago**.

## 6 · Procedencia del copy

| Pieza | Fuente |
|---|---|
| Reseñas: titular, bajada, viñetas, tres momentos, canales, selector de destino | `ReviewsLanding.tsx`, `ChannelRows.tsx`, novedad `resenas-verificadas` (recortado al presupuesto) |
| Gift Cards: bajada corta, CTA, alerta de Mercado Pago | `GiftCards.tsx` (empty state y alerta) |
| Precios dinámicos: bajada, ejemplo, microcopy, CTA | `DynamicPricingEmptyState.tsx` («locked to JP's exact wording») |
| Todo lo demás | **Nuevo**, marcado en el boceto con «Nuevo» |

## 7 · Pendientes de confirmación

- Titular de Precios dinámicos: hoy es solo «Precios dinámicos.» (texto fijo de JP). El boceto propone un titular de resultado que reutiliza su vocabulario; requiere OK de JP.
- «Incluido en tu plan» en Precios dinámicos: sale de un comentario de `Billing.tsx`, no de un chequeo en backend.
- Nombres de rubro: «Salón» agrupa Peluquería, Uñas, Pestañas y Cejas (los rubros con más servicios en la base). Barbería es un rubro propio.
