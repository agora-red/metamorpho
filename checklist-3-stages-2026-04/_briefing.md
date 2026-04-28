# Setup Checklist v3 · 3 etapas · 24 tareas

Spec de implementación para la nueva versión del checklist `Configurá tu negocio` que se despliega desde el header del dashboard. Reemplaza la lista plana actual (`SETUP_TASK_IDS` en `develop`) por una agrupación en **3 etapas** con tareas colapsables, instructivos guiados (steppers) y deep-links a apps externas.

> **Mockup interactivo**: [`docs/checklist-3-stages-proposal.html`](./checklist-3-stages-proposal.html) — abrirlo en el browser para ver el comportamiento real (toggle por etapa, scroll a steppers, hover/focus states, smart URLs).

---

## 1 · Resumen ejecutivo

- **24 tareas** distribuidas en 3 etapas (9 / 6 / 9)
- **11 ya existen** en `SETUP_TASK_IDS` de `develop`; **13 son candidatas** nuevas que reutilizan features ya shipeadas
- **6 tareas son skippables** (eliminables del checklist) · 18 son obligatorias
- **5 tareas tienen stepper instructivo** con deep-links a apps externas (IG, WA Business, WA share) o al messenger de Intercom
- **Sin tiempos estimados** — el badge del trigger muestra etapa actual + % en lugar de "X minutos restantes"

---

## 2 · Estructura de etapas

| Etapa | Nombre | Foco | Tareas |
|-------|--------|------|--------|
| 1 | **Configurá tu Ágora** | Página, catálogo, comunicación, señas y disponibilidad | 9 |
| 2 | **Obtené tus primeras reservas** | Compartir la página y activar canales de captación | 6 |
| 3 | **Activá y escalá tu negocio** | Rituales operativos, segmentación de clientes y nuevos canales de venta | 9 |

### Comportamiento del panel

- Solo **una etapa abierta por defecto**: la activa (la primera incompleta).
- Etapas completadas → header colapsado, num circle en verde con check.
- Etapas futuras → header colapsado, num circle gris con número.
- Click en cualquier header de etapa → toggle expandir/colapsar (independiente, no es accordion exclusivo).

### Header del trigger (top-right del dashboard)

- Reemplazar el "tiempo estimado" actual por el formato:
  `<X> pendientes · etapa <N> de 3` + porcentaje completado.
- Ejemplo: `13 pendientes · etapa 2 de 3 · 48%`.

---

## 3 · Tabla maestra · 24 tareas

Convenciones:

- **Confirmación**:
  - `Auto · back` → query al estado del vendor (avatar, social_apps, payments, etc.) confirma la tarea sin acción explícita.
  - `Stepper` → wizard guiado dentro del checklist; la tarea se marca completa al cerrar el último paso.
- **Skip**: si es `Sí`, el botón de eliminar (ícono basurero) aparece al hover y el vendor puede sacar la tarea de su checklist.
- **Estado**: `Hoy` ya existe en `SETUP_TASK_IDS` en `develop`; `Candidata` requiere agregarse.

### Etapa 1 · Configurá tu Ágora (9)

| # | Task ID | Label | Confirmación | Skip | Estado |
|---|---------|-------|--------------|:----:|:------:|
| 1 | `profile_photo` | Agregar foto de perfil | Auto · back | No | Hoy |
| 2 | `social_media` | Agregá tus redes sociales | Auto · back | No | Hoy |
| 3 | `image_gallery` | Agregar galería de imágenes a tu página | Auto · back | No | Hoy |
| 4 | `cancellation_policy` | Configurá tu política de cancelación | Auto · back | No | Candidata |
| 5 | `deposit_policy` | Configurá tu política de señas | Auto · back | No | Hoy |
| 6 | `service_categories` | Organizar tu catálogo en categorías | Auto · back | Sí | Candidata |
| 7 | `google_calendar` | Conectar Google Calendar | Auto · back | No | Hoy |
| 8 | `upload_clients` | Subir base de clientes | Stepper | Sí | Hoy |
| 9 | `configure_messages` | Configurá los mensajes automáticos a clientes | Auto · back | Sí | Hoy |

### Etapa 2 · Obtené tus primeras reservas (6)

| # | Task ID | Label | Confirmación | Skip | Estado |
|---|---------|-------|--------------|:----:|:------:|
| 1 | `link_in_bio` | Agregar enlace a tu bio de Instagram | Stepper | Sí | Hoy |
| 2 | `wa_business_autoreply` | Activar respuesta automática en WhatsApp Business | Stepper | Sí | Candidata |
| 3 | `share_whatsapp` | Compartir tu página por WhatsApp | Stepper | Sí | Candidata |
| 4 | `create_discount` | Crear tu primer descuento | Auto · back | Sí | Candidata |
| 5 | `request_tutorial` | Solicitar instructivo para clientes | Stepper | Sí | Hoy |
| 6 | `first_manual_booking` | Ingresar tu 1ra reserva manual | Auto · back | No | Hoy |

### Etapa 3 · Activá y escalá tu negocio (9)

| # | Task ID | Label | Confirmación | Skip | Estado |
|---|---------|-------|--------------|:----:|:------:|
| 1 | `first_payment` | Recibir tu 1er cobro online | Auto · back | No | Candidata |
| 2 | `confirm_attendance` | Confirmar asistencia de un cliente | Auto · back | No | Candidata |
| 3 | `confirm_payment_received` | Confirmar recepción de un cobro | Auto · back | No | Candidata |
| 4 | `booking_notes` | Agregar notas a tus reservas | Auto · back | No | Candidata |
| 5 | `client_tags` | Usar etiquetas para segmentar clientes | Auto · back | No | Candidata |
| 6 | `enable_wa_messages` | Activar mensajes automáticos por WhatsApp | Auto · back | No | Candidata |
| 7 | `add_service_addon` | Agregar un add-on a un servicio | Auto · back | No | Candidata |
| 8 | `block_dates` | Bloquear horarios o feriados en que no vas a estar disponible | Auto · back | No | Candidata |
| 9 | `create_first_gift_card` | Creá tu 1ra tarjeta de regalo | Auto · back | No | Candidata |

---

## 4 · Detalle por tarea

> Una línea por tarea con el objetivo de negocio + cómo se confirma desde back. Útil para que el equipo entienda qué query/flag dispara el complete.

### Etapa 1

- **`profile_photo`** — Que tu foto/logo aparezca en página, búsquedas y notificaciones. *Auto: `users.avatar_url IS NOT NULL` o `vendor_storefronts.storefront_avatar_url IS NOT NULL`.*
- **`social_media`** — Visibilidad de IG/TikTok/FB en la página. *Auto: `count(vendor_social_apps WHERE link != '') > 0`.*
- **`image_gallery`** — Trabajos previos como prueba social. *Auto: `count(vendor_galleries WHERE items != '[]') > 0`.*
- **`cancellation_policy`** — Reglas claras → reduce disputas. *Auto: campo cancellation_policy seteado en vendor o services.*
- **`deposit_policy`** — Reduce no-shows con cobro adelantado. *Auto: `vendors.is_down_payment_enabled = true`.*
- **`service_categories`** — Agrupar servicios afines para mejor descubrimiento. *Auto: `count(service_categories WHERE vendor_id = $1) > 0`.*
- **`google_calendar`** — Sincronizar bloqueos externos para evitar overbooking. *Auto: `vat.first_google_calendar_sync_at IS NOT NULL`.*
- **`upload_clients`** — Migrar histórico de clientes (flujo asistido por Intercom). *Stepper. Marcar complete cuando soporte sube el archivo (manual desde admin).*
- **`configure_messages`** — Personalizar tono de recordatorios y confirmaciones. *Auto: `count(vendor_message_templates WHERE customized = true) > 0`.*

### Etapa 2

- **`link_in_bio`** — Convertir tráfico orgánico de IG en reservas. *Stepper.*
- **`wa_business_autoreply`** — Cada DM entrante se convierte en una reserva. *Stepper. Sin confirmación automática (Meta no expone API para verificar greeting message).*
- **`share_whatsapp`** — Activación viral en la base de clientes existente del vendor. *Stepper. Sin confirmación automática (no podemos confirmar que envió).*
- **`create_discount`** — Cupón de bienvenida para acelerar primera reserva. *Auto: `count(discounts WHERE vendor_id = $1) > 0`.*
- **`request_tutorial`** — Pedir asset gráfico para enseñar a clientes a reservar (asistido por Intercom). *Stepper. Marcar complete cuando soporte envía el asset.*
- **`first_manual_booking`** — Probar el flow real con un caso conocido. *Auto: `vat.first_business_booking_at IS NOT NULL`.*

### Etapa 3

- **`first_payment`** — Validar el cobro end-to-end con dinero real. *Auto: `count(payments WHERE status = 'succeeded' AND vendor_id = $1) > 0`.*
- **`confirm_attendance`** — Marcar al cliente como asistió → base para reportes de no-shows y reseñas automáticas. *Auto: `count(bookings WHERE attendance_confirmed_at IS NOT NULL) > 0`.*
- **`confirm_payment_received`** — Marcar manualmente cobros offline (efectivo, transferencia). *Auto: `count(payments WHERE method = 'offline' AND received_at IS NOT NULL) > 0`.*
- **`booking_notes`** — Anotar contexto del cliente en cada reserva (alergias, preferencias). *Auto: `count(bookings WHERE notes IS NOT NULL AND notes != '') > 0`.*
- **`client_tags`** — Etiquetar clientes (VIP, primera vez, suscriptor) para segmentación. *Auto: `count(client_tags WHERE vendor_id = $1) > 0`.*
- **`enable_wa_messages`** — Pasar recordatorios y confirmaciones de email a WhatsApp. *Auto: `wa_packs activo` + `notification preferences.wa_enabled = true`.*
- **`add_service_addon`** — Sumar extras opcionales a un servicio (sube ticket promedio). *Auto: `count(service_addons WHERE service_id IN (SELECT id FROM services WHERE vendor_id = $1)) > 0`.*
- **`block_dates`** — Cargar feriados, vacaciones o franjas sin atención. *Auto: `count(vendor_blocked_dates WHERE vendor_id = $1) > 0`.*
- **`create_first_gift_card`** — Sacar la primera gift card al mercado. *Auto: `count(gift_cards WHERE vendor_id = $1) > 0`.*

---

## 5 · Steppers · instructivos paso a paso

5 tareas usan el componente `StepperModal` ya existente en Flash. Para cada una se especifica el copy de cada paso, los **smart URLs / deep links** que abren las apps externas, y las hookups a Intercom donde corresponde.

### 5.1 · `wa_business_autoreply` — Activar respuesta automática en WhatsApp Business

**Subtítulo**: *Convierte cada DM entrante en una reserva: el cliente que escribe pidiendo turno recibe al instante el link de tu agenda online y cómo reservar.*

**Paso 1 · Confirmá que estás usando WhatsApp Business**
> Esto solo funciona con la app **WhatsApp Business** (no la versión normal). Es gratuita y la conseguís en Play Store o App Store. Si todavía usás WhatsApp normal, descargá Business y migrá tu cuenta antes de seguir.

**Paso 2 · Abrí "Mensaje de bienvenida"**
> **En Android:** tocá los 3 puntos arriba a la derecha → **Herramientas para empresas** → **Mensaje de bienvenida**.
> **En iPhone:** abajo tocá la pestaña **Ajustes** → **Herramientas para empresas** → **Mensaje de bienvenida**.

**CTA**: `[Abrir WhatsApp Business →]` `href="whatsapp://"`

**Paso 3 · Activá el switch y pegá este texto**
> Tocá el switch **"Enviar mensaje de bienvenida"** para activarlo. Después tocá el cuadro de texto y reemplazá el contenido por este mensaje:

```
¡Hola! Gracias por escribirme 🙌
Para reservar tu turno entrá a 👉 www.agora.red/{username}

Ahí podés:
1️⃣ Ver mis servicios y precios
2️⃣ Elegir el horario que más te conviene
3️⃣ Reservar al instante

Ante cualquier duda te respondo apenas pueda. ¡Te espero!
```

> Tocá **OK** (o **Guardar**) para confirmar el texto.

**Paso 4 · Definí destinatarios**
> Tocá **Destinatarios** y elegí **Todos los que no estén en mi libreta de contactos**. Esto hace que cada persona nueva que te escriba reciba el mensaje en cuanto manda el primer DM, sin que vos hagas nada.
> Tocá **Guardar** arriba a la derecha para terminar.

**CTA final**: `[Listo, ya lo configuré]` → marca complete en back.

---

### 5.2 · `link_in_bio` — Agregar enlace a tu bio de Instagram

**Subtítulo**: *Hace que el tráfico orgánico de IG (perfil, posts, stories) caiga en tu agenda online con un solo toque.*

**Paso 1 · Copiá tu link**
> Este es el link público de tu agenda: `www.agora.red/{username}`

**CTA**: `[Copiar link]` → `navigator.clipboard.writeText('https://www.agora.red/' + username)`

**Paso 2 · Andá a tu perfil de Instagram y tocá "Editar perfil"**
> En la app de Instagram: abajo a la derecha tocá tu foto para entrar a tu perfil. Después arriba tocá el botón **Editar perfil**.

**CTA**: `[Abrir Editar perfil en Instagram →]` `href="https://www.instagram.com/accounts/edit/"`

**Paso 3 · Tocá la sección "Enlaces"**
> Dentro de "Editar perfil" vas a ver una fila que dice **Enlaces** (o "Links" si tenés Instagram en inglés). Tocala para entrar a la pantalla de enlaces.
> *Si todavía aparece el campo viejo "Sitio web", también podés pegar ahí el link directamente y saltear los pasos siguientes — Instagram va a migrarlo solo a la sección Enlaces más adelante.*

**Paso 4 · Tocá "+ Agregar enlace externo"**

**Paso 5 · Pegá tu link y poné un título**
> En el campo **URL**, pegá `www.agora.red/{username}`.
> En el campo **Título del enlace**, escribí algo como **Reservá tu turno** o **Mi agenda online**.
> Tocá **Listo** arriba a la derecha.

**Paso 6 · Volvé a "Editar perfil" y guardá**
> Tocá **Listo** (arriba a la derecha) para guardar los cambios. Verificá entrando a tu perfil que el link aparezca debajo de tu bio.

**CTA final**: `[Listo, ya lo agregué]`

---

### 5.3 · `share_whatsapp` — Compartir tu página por WhatsApp

**Subtítulo**: *Avisarle a los clientes que ya tenés en WA que ahora pueden reservar online — el primer empuje viral.*

**Paso 1 · Mensaje pre-armado**
```
¡Hola! Te cuento que ahora tenés mi agenda online 🙌

Reservá tu turno cuando quieras desde 👉 www.agora.red/{username}
Elegís el servicio, ves mis horarios y reservás al instante.

¡Te espero!
```

**Paso 2 · Compartilo con tus contactos**
> Tocá el botón para abrir WhatsApp con el mensaje ya pegado. Después elegí los contactos a los que querés mandárselo (empezá por tus clientes habituales) y mandalo.

**CTA**: `[Compartir por WhatsApp →]` `href="https://wa.me/?text=<URL-encoded-message>"`

URL canónica: `https://wa.me/?text=` con el mensaje URL-encoded (incluyendo emojis y newlines como `%0A`). Reemplazar `{username}` antes de encodear.

---

### 5.4 · `upload_clients` — Subir base de clientes (asistido)

**Subtítulo**: *Te ayudamos a migrar tu histórico de clientes para que puedas usar campañas, segmentaciones y mensajes masivos desde el día uno. **Esta tarea no es self-service**: la hacemos nosotros por vos.*

**Paso 1 · Lo subimos nosotros**
> No tenés que normalizar nada ni adaptar columnas. Mandanos el listado en el formato que tengas — Excel, CSV, contactos exportados del celular, una hoja de Google, una agenda escaneada — y nosotros lo cargamos a tu cuenta.

**Paso 2 · Contactanos desde el messenger**
> Tocá el botón abajo para abrir una conversación con nuestro equipo de soporte (Intercom). Va con un mensaje pre-armado — solo tenés que adjuntar tu archivo y enviarlo.

**CTA**: `[Contactanos]` → `Intercom('showNewMessage', 'Hola, quiero migrar mi base de clientes a Ágora. Adjunto el archivo.')`

**Paso 3 · Listo en el día**
> En cuanto recibimos tu archivo lo procesamos y dejamos la base cargada en tu cuenta. Te avisamos por la misma conversación cuando esté lista — normalmente el mismo día hábil.

**Confirmación de la tarea**: el endpoint que carga la base desde el admin marca el task como complete.

---

### 5.5 · `request_tutorial` — Solicitar instructivo para clientes

**Subtítulo**: *Recibís un mini-tutorial en imágenes/video que mostrás a tus clientes para que aprendan a reservar online sin fricciones.*

**Paso 1 · Te armamos un instructivo a medida**
> Es un set de imágenes (o un video corto) explicando paso a paso cómo reservar en `www.agora.red/{username}`. Lo podés mandar por WA, mostrarlo en el local o pegarlo como historia de IG.

**Paso 2 · Contactanos para pedirlo**
> Tocá el botón abajo para abrir una conversación con nuestro equipo desde el messenger del dashboard (Intercom). Va con un mensaje pre-armado — solo tenés que enviarlo. Te respondemos con el instructivo en un par de horas hábiles.

**CTA**: `[Contactanos]` → `Intercom('showNewMessage', 'Hola, quisiera el instructivo para clientes con mi link de reservas.')`

**Confirmación de la tarea**: el endpoint admin que envía el asset marca el task como complete.

---

## 6 · Reglas de copy (cliente-facing)

Aplican a cualquier texto que el vendor envía o muestra a sus clientes (mensajes pre-armados de los steppers, body de auto-reply, instructivo, posts):

1. **Nunca mencionar Ágora como marca** — los negocios no comunican a sus clientes nada sobre la plataforma. Lead con frases tipo *"tengo una página"*, *"mi agenda online"*, *"ahora podés reservar online"*. Evitar *"estoy en Ágora"*, *"reservás por Ágora"*, *"vendido por Ágora"*.
2. **URL canónica** — siempre formato `www.agora.red/{username}`: con prefix `www.`, sin `https://`. Las apps modernas (WhatsApp, Instagram, browsers móviles) hipervinculan automáticamente `www.` y se lee más natural en un mensaje.
3. **Tono argentino** — vos, conjugaciones rioplatenses ("reservá", "elegí", "mandá"), emojis con moderación.

---

## 7 · Cambios necesarios

### 7.1 · cyclone (`/Users/jp/Documents/agora_repos/cyclone`)

**`src/database/models/VendorSetupTask.model.ts`**
- Extender `SETUP_TASK_IDS` con los **13 IDs candidatos** (manteniendo orden lógico por etapa).
- Agregar nuevo campo `stage` al model (1 | 2 | 3) o derivar el stage por map-lookup.
- Actualizar `SKIPPABLE_TASKS` — solo deben estar las 6 marcadas con `Skip = Sí` arriba.

**`src/repos/dashboard.repo.ts`**
- Extender `TASK_LABELS` con los nuevos labels (en español, "vos").
- Extender `backfillChecks` con las 13 queries de auto-confirmación detalladas en sección 4.
- Actualizar el shape de `BusinessSetupI` para incluir `stage` en cada task.
- Agregar endpoint `me/vendor/dashboard/setup-tasks/upload-clients/admin-complete` para que admin marque el task de subida de clientes una vez procesada.
- Idem para `request-tutorial/admin-complete`.

**`src/types/`**
- Actualizar `BusinessSetupTaskI` para incluir `stage: 1 | 2 | 3`.

### 7.2 · Flash (`/Users/jp/Documents/agora_repos/flash`)

**`src/containers/Dashboard/components/widgets/BusinessSetupWidget.tsx`**
- Reescribir layout del modal para agrupar tasks por `task.stage`.
- Implementar accordion-like behavior con state local `openStages: Record<number, boolean>`.
- Default open: la primera etapa con tareas pending.
- Reemplazar el botón texto `saltar` por ícono basurero (componente `IconButton` con tooltip "Eliminar de mi checklist").
- Header del trigger: cambiar `1 pendiente` por `<X> pendientes · etapa <N> de 3` + porcentaje.
- Para tasks con `stepper`: renderizar pill `Instructivo` antes del chevron y abrir `StepperModal` al click.

**`src/containers/Dashboard/components/widgets/stepperConfigs.ts`**
- Agregar configs para `wa_business_autoreply`, `share_whatsapp`, `upload_clients`, `request_tutorial` (más el ya existente `link_in_bio` actualizado al nuevo flow de IG).
- Cada step config debe soportar:
  - `title`, `body` (markdown ligero o JSX)
  - `copyableText` (string opcional, render como bloque de copia)
  - `cta`: `{ label, href? | onClick? }` con tipos `external-link` | `intercom` | `complete`

**Smart URL helpers**
- `whatsapp://` para abrir WhatsApp Business (paso 2 de `wa_business_autoreply`).
- `https://www.instagram.com/accounts/edit/` (paso 2 de `link_in_bio`).
- `https://wa.me/?text=<encoded>` con el mensaje pre-armado (CTA final de `share_whatsapp`).
- `Intercom('showNewMessage', '<prompt>')` para `upload_clients` y `request_tutorial`. Verificar que `window.Intercom` existe antes de invocar.

---

## 8 · Decisiones a tomar antes de implementar

1. **Path canónico de la URL** — el spec usa `www.agora.red/{username}`. Confirmar que la redirect de `agora.red/{username}` → `www.agora.red/{username}` está en place (Cloudflare rule) o agregarla.
2. **Smart URL de WhatsApp Business** — `whatsapp://` abre la app WhatsApp default, que puede ser Business o normal según lo que el usuario tenga instalado. ¿Aceptable o queremos instrucciones explícitas si no abre WA Business?
3. **Migración de tasks existentes** — para vendors actuales con tasks legacy, ¿cómo mapear? Propuesta: nuevo backfill que asigna stage según el ID y completa los 13 nuevos según queries de estado actual del vendor.
4. **Nombre del trigger** — actualmente "Configurá tu negocio". La etapa 1 ahora se llama "Configurá tu Ágora" — son distintos pero similares. ¿Renombrar el trigger a "Tu checklist" o similar para evitar choque?
5. **Comportamiento al saltear (skip)** — hoy el skip es soft-delete (set status=skipped). ¿Mantener o pasar a hard-delete del vendor_setup_tasks row para reducir clutter en queries?
6. **Confirmación de `wa_business_autoreply` y `share_whatsapp`** — ambas dependen de declaración del vendor (no podemos validar desde back). El click en "Listo" del último step marca complete. ¿Aceptable o querés que requieran un sanity check (ej: el vendor mandó un mensaje de prueba al número del bot)?

---

## 9 · Testing manual

Antes del merge:

- [ ] Vendor recién creado → ve el panel con etapa 1 abierta, 0/9 done, las 6 etapas/9 totales no skippables sin botón de eliminar.
- [ ] Backfill al primer login → tasks ya completadas (avatar, social_apps, gallery, gcal, etc.) aparecen en verde.
- [ ] Click en `wa_business_autoreply` → abre stepper, paso 2 botón "Abrir WhatsApp Business" lanza la app (en mobile).
- [ ] Click en `link_in_bio` → stepper, paso 2 botón abre `https://www.instagram.com/accounts/edit/` (en mobile redirige a la app, en desktop abre web).
- [ ] Click en `share_whatsapp` → stepper, último botón abre `wa.me` con el mensaje URL-encoded correctamente (probar con username con caracteres especiales).
- [ ] Click en `upload_clients` y `request_tutorial` → stepper, botón "Contactanos" abre Intercom con el mensaje pre-armado.
- [ ] Eliminar tarea skippable → desaparece del checklist; `count` de la etapa baja en 1.
- [ ] Toggle de etapa → expande/colapsa correctamente, body scrollea internamente sin empujar el resto.
- [ ] Etapa 100% completa → header colapsa automáticamente, num circle pasa a verde con check.
- [ ] Tabla `users` con `avatar_url` que apunta a `default_user_image` → `profile_photo` queda como pending (no falso positivo).
