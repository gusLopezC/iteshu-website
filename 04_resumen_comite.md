# 04 · Resumen para el comité

**Proyecto:** Rediseño de la presencia web del ITESHU — identidad 100% institucional, experiencia de portal moderno
**Entregable clave:** `index.html` (prototipo funcional de una página)
**Fecha:** 2026

---

## Argumentos técnicos principales

### 1. Identidad institucional intacta (cero riesgo de marca)
- Colores extraídos exclusivamente del CSS y del logo oficiales de iteshu.edu.mx:
  `#1B396A` (azul institucional), `#092432`, `#bc955b` (dorado), `#006e4d`,
  `#611232`, `#0b231e`. Verificados píxel a píxel contra el sitio real
  (`00_investigacion.md`).
- Logo oficial (`images/header/iteshu.png`) y 16+ fotografías reales del sitio
  (carreras, biblioteca, incubadora, noticias, mapa oficial), todas verificadas
  HTTP 200. **Cero placeholders, cero imágenes inventadas.**

### 2. La claridad de un portal institucional moderno
- Hero con CTA único; 6 accesos rápidos en tarjetas; oferta educativa en grid
  visual de portada; noticias y convocatorias separadas; campus con mapa y
  contacto; footer institucional limpio. Misma estructura de tarjetas, botones y
  whitespace que hacen navegable el portal.

### 3. Rendimiento y ligereza
- Un solo archivo HTML (Tailwind CDN, sin Bootstrap/jQuery/sliders/SDK).
- Imágenes con `loading="lazy"`, `width/height` definidos (cero layout shift),
  `preconnect` a recursos críticos. El sitio actual carga Bootstrap 3, w3.css,
  owl carousel, js-image-slider y Facebook SDK.

### 4. Accesibilidad y calidad técnica
- Menú hamburguesa funcional con `aria-expanded`/`aria-controls`, salto de
  navegación, foco visible, `prefers-reduced-motion`, textos alternativos en
  todas las imágenes. HTML validado sin errores de etiquetas; JS sin errores de
  consola; probado en escritorio y móvil (390px).

---

## Cómo mejora la conversión de aspirantes

| Fricción actual | En la propuesta | Impacto esperado |
|---|---|---|
| Las carreras están ocultas tras un menú de 3 niveles | Grid visual de portada, visible sin clics | Menos abandono por no encontrar la oferta |
| No existe "Quiero ser aspirante" | CTA persistente en header, hero, admisión y footer | Ruta de conversión siempre visible |
| La portada muestra licitaciones | Hero con mensaje + foto real + CTA único | Primer impacto correcto (regla de los 5 segundos) |
| Textos largos cortados por CSS | Cards con extractos cortos y enlace "Ver más" | Mensaje legible en segundos |
| Sin ruta de admisión | Sección "Admisión en 4 pasos" + ficha en línea | Aspirantes guiados de ficha a inscripción |
| Móvil deficiente | Diseño mobile-first, menú funcional | Captura del segmento 100% móvil |

**Conclusión:** el prototipo conserva la marca y el contenido real del ITESHU y
los reorganiza con la arquitectura de conversión de las grandes universidades
públicas: **identidad intacta, claridad institucional, foco total en el aspirante.**
