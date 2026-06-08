# Páginas modulares · Bloques

**Tipo:** Prototipo interactivo (propuesta de diseño)
**Fecha:** Junio 2026

## Qué es

Propuesta para que un profesional pueda crear **páginas-destino libres y modulares** en su storefront — un tipo de página nuevo, aparte de la landing principal, con su propia URL (`agora.red/<username>/<slug>`).

Es la evolución del actual `/bio`: hoy esa página existe pero es rich-text plano, enterrado en "Más info" y difícil de encontrar. La propuesta la generaliza: la persona crea **bloques** a partir de sus links (turnos, servicios, cursos, productos, gift cards) y compone páginas propias. La landing principal **no se toca** — sólo gana un botón que apunta a la página nueva, igual que el "Conoce más" de hoy.

## Qué muestra el prototipo

- **Gestor "Páginas"** (panel izquierdo): lista de páginas-destino, cada una con su URL, estado y caso de uso. Resuelve el "difícil de encontrar".
- **Editor de bloques** (centro): agregar / mover / ocultar / borrar bloques, editar textos inline.
- **Vista en vivo** (derecha): la página renderizada en su propia URL, con el Estilo aplicado.
- **3 ejemplos fuertes y distintos**: Promos de junio (campaña), Masterclass de Trenzas (landing de evento), Conoce más (la `/bio` migrada).
- **9 tipos de bloque**: Destacado · Botones · Grilla · Galería · Video · Datos · FAQ · Texto · Título.
- **6 Estilos reales** del storefront (Crema, Rosé, Noir, Salvia, Terracota, Tinta) — re-skin en vivo, con sus tipografías (Fraunces / Playfair / Cormorant).

## Modelo de datos propuesto

- Tabla `vendor_pages` (slug + `blocks` JSONB) — sin migración por cada tipo de bloque.
- Los bloques reusan el `LinkI` actual (type, title, url, description).
- Surface en la landing vía un `VendorLink` (mecanismo que ya existe).
- Render en Nightwing como `/[vendor_username]/[pageSlug]` (generaliza el actual `bio/page.tsx`).

## Notas

- Datos de muestra ficticios (vendor de prueba "centrodepelo", contenido inventado). Sin métricas reales ni PII.
- Imágenes vía Unsplash CDN.
