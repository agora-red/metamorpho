---
name: "Metamorpho · Ágora"
description: "Sistema editorial Frost para experiencias web autocontenidas, claras y sustentadas en evidencia real del producto."
colors:
  primary-blue: "#0067E0"
  primary-blue-deep: "#004EA8"
  primary-blue-soft: "#EAF3FF"
  human-coral: "#D92D47"
  human-coral-deep: "#B4233C"
  human-coral-soft: "#FFECEF"
  confirmation-green: "#067647"
  confirmation-green-deep: "#055D39"
  confirmation-green-soft: "#E7F8F1"
  ink: "#101828"
  copy: "#344054"
  muted: "#667085"
  line: "#DCE5F0"
  control-border: "#7588A3"
  surface: "#FFFFFF"
  field-surface: "#FBFCFE"
  canvas: "#F4F7FB"
  disabled-surface: "#EAECF0"
  disabled-text: "#98A2B3"
  frosted-chrome: "rgba(244, 247, 251, .88)"
typography:
  display:
    fontFamily: "Manrope, sans-serif"
    fontSize: "clamp(2.65rem, 5.8vw, 5.7rem)"
    fontWeight: 800
    lineHeight: 0.98
    letterSpacing: "-0.04em"
  headline:
    fontFamily: "Manrope, sans-serif"
    fontSize: "clamp(1.3rem, 2vw, 2rem)"
    fontWeight: 700
    lineHeight: 1.15
    letterSpacing: "-0.025em"
  title:
    fontFamily: "Manrope, sans-serif"
    fontSize: "clamp(1.2rem, 2vw, 1.8rem)"
    fontWeight: 700
    lineHeight: 1.18
    letterSpacing: "-0.025em"
  lead:
    fontFamily: "Manrope, sans-serif"
    fontSize: "clamp(1.03rem, 1.65vw, 1.42rem)"
    fontWeight: 400
    lineHeight: 1.48
    letterSpacing: "normal"
  body:
    fontFamily: "Manrope, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: "normal"
  label:
    fontFamily: "Manrope, sans-serif"
    fontSize: "0.78rem"
    fontWeight: 800
    lineHeight: 1.2
    letterSpacing: "0.04em"
rounded:
  badge: "9px"
  action: "13px"
  control: "14px"
  media: "20px"
  panel: "24px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "12px"
  md: "18px"
  lg: "24px"
  xl: "32px"
  2xl: "48px"
  screen-inline: "clamp(24px, 7vw, 112px)"
components:
  button-primary:
    backgroundColor: "{colors.primary-blue}"
    textColor: "{colors.surface}"
    typography: "{typography.label}"
    rounded: "{rounded.control}"
    padding: "12px 18px"
    height: "44px"
  button-primary-hover:
    backgroundColor: "{colors.primary-blue-deep}"
    textColor: "{colors.surface}"
    rounded: "{rounded.control}"
  button-primary-disabled:
    backgroundColor: "{colors.disabled-surface}"
    textColor: "{colors.disabled-text}"
    rounded: "{rounded.control}"
  icon-action:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.action}"
    size: "44px"
    height: "44px"
    width: "44px"
  frosted-navigation:
    backgroundColor: "{colors.frosted-chrome}"
    textColor: "{colors.ink}"
    padding: "0 clamp(20px, 4vw, 64px)"
    height: "72px"
  evidence-frame:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.media}"
    padding: "0"
    width: "100%"
  surface-card:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.panel}"
    padding: "clamp(28px, 4vw, 48px)"
  text-field:
    backgroundColor: "{colors.field-surface}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.control}"
    padding: "14px 16px"
---

# Design System: Metamorpho · Ágora

## Overview

**Creative North Star: "El Estudio Editorial Frost"**

Metamorpho convierte cada output de Ágora en una sala editorial luminosa: un canvas frío y silencioso, superficies blancas y una jerarquía tipográfica que permite entender la propuesta antes de detenerse en el detalle. El sistema debe sentirse profesional sin volverse corporativo, y cercano sin apoyarse en ornamento infantil.

La evidencia manda. Las capturas reales y ya saneadas del producto son el material principal; el diseño les da contexto, procedencia y aire en lugar de competir con ellas. Azul, coral y verde forman una gramática funcional: acción y orientación, humanidad y énfasis, confirmación y disponibilidad.

**Key Characteristics:**

- Canvas frío claro con superficies blancas nítidas.
- Manrope de alto contraste jerárquico y lectura directa en español.
- Capturas reales tratadas como evidencia, con procedencia visible.
- Acentos semánticos escasos, accesibles y deliberados.
- Controles táctiles con estados de teclado, hover y disabled inequívocos.

## Colors

La paleta Frost usa neutros azulados como atmósfera y reserva los tres acentos para orientar, humanizar y confirmar.

### Primary

- **Azul Ágora** (`primary-blue`): acción principal, foco de teclado, enlaces y orientación activa.
- **Azul Profundo** (`primary-blue-deep`): estado hover o pressed del azul principal; nunca reemplaza la tinta en texto largo.
- **Azul Hielo** (`primary-blue-soft`): selección o información de baja intensidad sobre fondos claros.

### Secondary

- **Coral Humano** (`human-coral`): énfasis editorial, conexión humana y contrapunto puntual al azul.
- **Coral Profundo** (`human-coral-deep`): texto semántico sobre fondos claros o coral suave cuando se necesita más contraste.
- **Coral Niebla** (`human-coral-soft`): avisos humanos y fondos de énfasis sin peso de alerta severa.

### Tertiary

- **Verde Confirmación** (`confirmation-green`): disponibilidad, éxito y evidencia confirmada.
- **Verde Profundo** (`confirmation-green-deep`): hover de acciones positivas.
- **Verde Niebla** (`confirmation-green-soft`): halo o superficie de confirmación discreta.

### Neutral

- **Tinta Frost** (`ink`): títulos y contenido de máxima prioridad.
- **Texto Editorial** (`copy`): párrafos, explicaciones y contenido secundario legible.
- **Texto Calmo** (`muted`): metadatos y ayudas, nunca información esencial aislada.
- **Línea Fría** (`line`): bordes, divisores y definición suave entre superficies.
- **Borde de Control** (`control-border`): contorno perceptible de campos en reposo.
- **Superficie Nítida** (`surface`): tarjetas, controles y marcos de evidencia.
- **Superficie de Campo** (`field-surface`): fondo apenas diferenciado para entradas editables.
- **Canvas Frost** (`canvas`): fondo base frío y claro.
- **Superficie Deshabilitada** (`disabled-surface`) y **Texto Deshabilitado** (`disabled-text`): estados inactivos que siguen siendo reconocibles.
- **Cromo Frost** (`frosted-chrome`): navegación persistente translúcida sobre contenido.

### Named Rules

**The One Lead Accent Rule.** Cada región tiene un acento dominante; azul, coral y verde no compiten con el mismo peso visual.

## Typography

**Display Font:** Manrope (with sans-serif)
**Body Font:** Manrope (with sans-serif)
**Label Font:** Manrope (with sans-serif)

**Character:** Una sola familia sostiene una voz contemporánea, cercana y precisa. El carácter editorial aparece en los saltos grandes de escala, el peso firme y el espaciado negativo de títulos, no en una segunda tipografía ornamental.

### Hierarchy

- **Display** (800, escala fluida, altura de línea compacta): una promesa o idea dominante; limitar a unas 17 letras promedio por línea y usar balance de texto.
- **Headline** (700, escala fluida, altura de línea 1.15): encabezados de módulos y argumentos de segundo nivel.
- **Title** (700, escala fluida, altura de línea 1.18): nombres de capacidades, tarjetas o bloques de evidencia.
- **Lead** (400, escala fluida, altura de línea 1.48): explicación introductoria; mantener un ancho máximo cercano a 68 caracteres.
- **Body** (400, base de 1rem, altura de línea 1.5): contenido corriente y controles.
- **Label** (800, compacto, tracking positivo): metadatos, categorías y microcopy; las mayúsculas son opcionales y se reservan para textos breves.

### Named Rules

**The Editorial Compression Rule.** Los títulos son grandes, cortos y apretados; el cuerpo recupera aire y nunca imita esa densidad.

## Layout

El sistema trabaja con un contenedor amplio de hasta 1380px y una variante de lectura de hasta 1120px, ambos centrados. El borde horizontal es fluido (`screen-inline`) para conservar aire desde desktop hasta tablet; los grupos internos repiten intervalos de 8, 12, 18, 24, 32 y 48px.

En superficies anchas, texto y evidencia pueden convivir en columnas asimétricas para que la captura conserve autoridad. A 980px las composiciones complejas pasan a una columna; a 700px se compactan navegación, tipografía y padding, y los objetivos táctiles conservan al menos 44px. El orden de lectura del DOM debe seguir siendo correcto cuando desaparece la grilla.

Las imágenes de producto mantienen su proporción, no se recortan si eso oculta información y deben poder leerse sin zoom en el ancho de destino. Las capturas de teléfono pueden convivir con desktop sólo cuando aclaran una adaptación real, no como decoración.

## Elevation & Depth

Frost combina capas tonales con sombras ambientales. El canvas y la superficie blanca producen la mayor parte de la separación; los bordes fríos definen controles y capturas. Las sombras quedan para objetos que deben leerse como piezas apoyadas sobre el canvas o para estados interactivos, nunca para cada bloque de contenido.

### Shadow Vocabulary

- **Ambient Panel** (`0 22px 60px -28px rgba(16, 24, 40, .32)`): paneles principales, tarjetas elevadas y capturas de producto.
- **Ambient Control** (`0 10px 28px -16px rgba(16, 24, 40, .24)`): acciones compactas, indicadores flotantes y feedback transitorio.
- **Blue Action Lift** (`0 14px 28px -16px rgba(0, 95, 213, .72)`): acción primaria con elevación moderada; desaparece en disabled.

### Named Rules

**The Frost Surface Rule.** Primero separar con tono y borde; sumar sombra sólo cuando la capa o el estado necesita una lectura espacial inequívoca.

## Shapes

Los controles son suavemente rectangulares: 13px para acciones compactas y 14px para botones y campos. Las capturas usan 20px y los paneles de mayor escala 24px, de modo que el radio crece con el volumen del objeto. Las píldoras completas se reservan para puntos, indicadores y estados pequeños; no convierten todo el contenido en cápsulas.

Los bordes son finos, fríos y continuos. Los marcos de evidencia recortan su contenido al mismo radio visual cuando el recurso lo necesita, y las composiciones evitan geometrías decorativas que puedan confundirse con controles.

## Components

Los componentes se sienten táctiles y seguros: superficies limpias, texto firme y cambios de estado visibles sin depender sólo del color.

### Buttons

- **Shape:** rectángulo suavemente redondeado (`control`), con altura táctil mínima de 44px.
- **Primary:** Azul Ágora sobre Superficie Nítida, tipografía de label y padding compacto de 12px por 18px.
- **Hover / Focus:** elevación vertical de 2px y Azul Profundo en hover; foco exterior de 3px en Azul Ágora con offset de 3px; transición espacial de 250ms con la curva Frost.
- **Disabled:** Superficie Deshabilitada, Texto Deshabilitado, sin sombra ni desplazamiento.
- **Icon action:** 44 × 44px, superficie blanca, borde frío y radio de acción; el icono nunca sustituye su nombre accesible.

### Cards / Containers

- **Corner Style:** radio de panel para contenedores y radio de media para capturas.
- **Background:** Superficie Nítida sobre Canvas Frost.
- **Shadow Strategy:** Ambient Panel sólo en piezas elevadas; los grupos editoriales comunes pueden ser planos.
- **Border:** Línea Fría de 1px cuando el límite necesita definición adicional.
- **Internal Padding:** fluido entre 28 y 48px en paneles protagonistas; reducir con intención en mobile.

### Inputs / Fields

- **Style:** Superficie de Campo, texto Tinta Frost, Borde de Control de 1px y radio de control.
- **Focus:** anillo exterior Azul Ágora de 3px con offset de 3px; el caret también usa Azul Ágora.
- **Error / Disabled:** los errores combinan mensaje textual, borde y tono; disabled reduce contraste sin perder la forma del control.

### Navigation

- **Style:** cromo translúcido sobre Canvas Frost, borde inferior frío y blur de fondo; la marca ocupa el primer punto de lectura.
- **States:** acciones compactas de 44px con label accesible, hover elevado y foco visible.
- **Responsive:** se compacta a 64px de alto en mobile y elimina texto auxiliar antes que iconos o acciones esenciales.

### Evidence Frames

- **Style:** captura real sobre superficie blanca, borde Línea Fría, radio de media y Ambient Panel.
- **Provenance:** una etiqueta discreta identifica entorno o naturaleza de la imagen sin tapar información relevante.
- **Integrity:** usar sólo recursos saneados para publicación; una ilustración o mockup debe nombrarse como tal y nunca presentarse como prueba comercial.

## Do's and Don'ts

### Do:

- **Do** mostrar producto real y saneado como evidencia antes de sumar explicación extensa.
- **Do** usar Azul Ágora para acción y orientación, Coral Humano para énfasis humano y Verde Confirmación para estados confirmados.
- **Do** conservar objetivos táctiles de al menos 44px, foco visible y orden de lectura correcto con teclado.
- **Do** mantener el canvas frío, las superficies blancas y una jerarquía tipográfica inequívoca en desktop y mobile.
- **Do** respetar `prefers-reduced-motion` y convertir animaciones en cambios prácticamente instantáneos.

### Don't:

- **Don't** inventar testimonios, cifras, estados de producto o evidencia que no estén aprobados para publicación.
- **Don't** usar capturas como decoración: deben ser legibles, pertinentes y llevar contexto de procedencia cuando corresponda.
- **Don't** repartir azul, coral y verde con la misma intensidad dentro de una región.
- **Don't** llenar la experiencia de tarjetas, píldoras o sombras cuando tipografía, espacio y borde ya resuelven la jerarquía.
- **Don't** ocultar foco, depender sólo del color para comunicar un estado ni reducir objetivos interactivos por debajo de 44px.
