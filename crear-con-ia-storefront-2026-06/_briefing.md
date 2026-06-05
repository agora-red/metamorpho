# Briefing — Crear con IA (storefront) · prototipo interactivo

**Tipo:** prototipo de producto navegable (no deck/landing).
**Para:** JP / Fermin — sentir el flujo antes de construirlo en código real.
**Audiencia:** interno. NO publicar al gallery público (feature no lanzada).

## Problema
Hoy el "Crear con IA" del editor de página (Flash /mi-pagina) es un clasificador que elige
1 de 8 plantillas hardcodeadas. Es ciego: pide el Instagram pero ni lo mira, decide solo con
nombre+categoría+bio. Se siente vacío.

## Visión que prototipamos
Experiencia mágica con **preview en vivo** que se transforma con cada decisión.

### 4 momentos
1. **Seed automático** — la IA "lee" el Instagram y extrae una paleta de SUS fotos. Nunca arranca de cero.
2. **Calibración A/B** (Akinator de diseño, no formulario) — 2 mini-previews vivos, "¿cuál te representa más?".
   Cada pick muta el preview central. Ejes: protagonista, personalidad, clima.
3. **Variantes** — 2-3 finales coherentes derivadas de su identidad, para ELEGIR.
4. **Reveal narrado** — la página se arma contando el porqué de cada decisión.

## Caso de ejemplo
Studio Lumière — nail art & beauty (Palermo). Avatar, servicios con precio, galería.

## Decisiones de diseño
- Frost-glass de Ágora en el chrome de la app.
- El storefront del preview usa fuentes propias (Playfair/Cormorant/Outfit/Montserrat) — es la
  página del vendor, no chrome de Ágora; las fuentes son parte de lo que cambia.
- Self-contained, JS vanilla, transiciones reales sobre CSS custom properties.
- Imágenes Unsplash con fallback a gradiente derivado de la paleta (nunca se rompe el "wow").
