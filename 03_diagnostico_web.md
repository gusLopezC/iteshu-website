# 03 · Diagnóstico UX de iteshu.edu.mx vs. propuesta

> Diagnóstico basado en inspección directa del sitio (HTML + CSS oficiales,
> `00_investigacion.md`) y en referencias de portales institucionales modernos.
> Cada problema se contrasta con la solución implementada en `index.html`.

---

## Resumen ejecutivo

iteshu.edu.mx es un sitio institucional correcto en contenido, pero está
**diseñado para el área administrativa, no para el aspirante**. Su portada
prioriza avisos de licitación sobre la oferta educativa, oculta las carreras en
menús profundos y carece de un camino de conversión hacia la admisión. La
propuesta conserva la identidad y el contenido, y reorganiza todo alrededor de
la experiencia del futuro estudiante, con la claridad de un portal institucional moderno.

---

## Problemas concretos (6-8) y contraste con la propuesta

### P1 · La portada prioriza trámites administrativos sobre oferta educativa
- **Evidencia:** el slider principal de `https://www.iteshu.edu.mx/iteshu/` está
  compuesto casi en su totalidad por imágenes de licitaciones públicas
  (`LP-ITESHU-E1-2024`, `LP-ITESHU-E2-2024`, juntas de aclaración, etc.). Las
  carreras no aparecen en la primera pantalla.
- **Consecuencia:** un aspirante no sabe en 5 segundos qué se estudia en el
  ITESHU (regla de los 5 segundos de UX).
- **Propuesta:** el hero muestra el campus y un CTA único "Quiero ser
  aspirante"; las convocatorias viven en su propia sección ordenada
  ("Noticias / Convocatorias")
  y `#Agenda` separadas del contenido principal.

### P2 · La oferta educativa está oculta en un menú desplegable multicapa
- **Evidencia:** las carreras se alcanzan vía menú → "OFERTA EDUCATIVA" →
  "ESCOLARIZADA" → página con imágenes. Tres niveles de navegación para el
  contenido más importante de la institución.
- **Consecuencia:** fricción de descubrimiento; en móvil el menú de Bootstrap 3
  es aún más difícil de operar.
- **Propuesta:** la oferta educativa es una **sección de portada en grid
  visual** (imagen real + nombre + descripción breve + botón), visible sin
  ningún clic, como grid de tarjetas.

### P3 · Textos extensos sin jerarquía visual
- **Evidencia:** secciones como "NOTICIAS" muestran párrafos largos justificados
  con `text-align: justify` y altura limitada a 70px por CSS
  (`opd.css`: `.noticia{height:70px; overflow:hidden}`), es decir, el sitio
  corta el texto en lugar de resumirlo.
- **Consecuencia:** se pierde el mensaje; leer en pantalla es fatigoso.
- **Propuesta:** tarjetas con títulos cortos, extractos de 1-2 líneas y
  enlace "Ver más", con abundante whitespace.

### P4 · Carrusel principal con prioridades mezcladas y sin CTA
- **Evidencia:** el carrusel mezcla becas, licitaciones, protocolos y fichas de
  maestría, sin jerarquía ni llamado a la acción; el usuario debe esperar el
  ciclo automático (`autoplayTimeout: 2500` en los carruseles owl).
- **Consecuencia:** el contenido clave compite con el ruido; el visitante no
  sabe qué hacer.
- **Propuesta:** un hero estático con mensaje fuerte y un único CTA
  primario; los avisos secundarios se organizan en secciones con título claro.

### P5 · No existe un camino de conversión para aspirantes
- **Evidencia:** no hay botón "Quiero ser aspirante" ni una ruta visible
  "Admisión → Ficha → Examen → Inscripción"; la página de inscripción se
  publica como imagen (`Proceso_de_inscripcion.png`) dentro de la lista de
  avisos.
- **Consecuencia:** el objetivo principal del sitio (reclutar aspirantes) no
  tiene apoyo de UI.
- **Propuesta:** CTA persistente en hero, header y footer; sección
  "Servicios / Accesos rápidos" con card "Admisión" y card "Convocatorias";
  cards de portales (Portal Alumno, Moodle)
  ("Portal", "Correo", "Bibliotecas").

### P6 · Performance y peso del sitio
- **Evidencia:** el sitio carga Bootstrap 3 completo, `w3.css`, jQuery, owl
  carousel, js-image-slider, SDK de Facebook, Photo-Sphere-Viewer y múltiples
  modales con contenido duplicado; las noticias aparecen dos veces en el HTML
  (una vez en la portada y otra en el modal).
- **Consecuencia:** tiempos de carga altos, sobre todo en el móvil rural donde
  vive la mayoría de aspirantes.
- **Propuesta:** un solo `index.html` con Tailwind CDN, imágenes con
  `loading="lazy"`, `width/height` definidos para evitar layout shift, sin
  librerías pesadas; el prototipo pesa una fracción del sitio actual.

### P7 · Experiencia móvil deficiente
- **Evidencia:** el CSS oculta el buscador en pantallas menores a 996px
  (`style.css`: `@media (max-width: 996px){#buscador{display:none}}`), el menú
  colapsa a un hamburguesa de Bootstrap 3 difícil de usar, y las tablas/modales
  no están pensadas para móvil.
- **Consecuencia:** el segmento más importante (aspirantes jóvenes, 100% móvil)
  recibe la peor experiencia.
- **Propuesta:** diseño **mobile-first**: menú hamburguesa funcional con
  cierre por overlay, grid que colapsa de 4→2→1 columnas, tipografía legible,
  botones grandes táctiles.

### P8 · Navegación sin anclas claras ni estructura "de portada"
- **Evidencia:** la portada mezcla secciones sin jerarquía de navegación
  (avisos → noticias → estudiantes → acreditaciones → oferta), y el menú
  principal no coincide con las secciones visibles de la página.
- **Consecuencia:** el usuario no sabe dónde está ni a dónde puede ir.
- **Propuesta:** menú fijo con anclas reales (Oferta Educativa, Admisión,
  Campus, Noticias, Contacto) que corresponden a secciones de la misma página,
  como un header fijo con menú claro.

---

## Tabla resumen problema → solución

| # | Problema actual | Solución en `index.html` |
|---|---|---|
| P1 | Portada llena de licitaciones | Hero con campus + CTA "Quiero ser aspirante"; convocatorias en sección propia |
| P2 | Oferta oculta en menú profundo | Grid visual de carreras en portada, a un clic |
| P3 | Texto justificado cortado por CSS | Cards con extractos cortos + whitespace |
| P4 | Carrusel mezclado sin CTA | Hero estático con CTA único |
| P5 | Sin ruta de conversión aspirante | CTAs persistentes + cards Admisión/Convocatorias/Portales |
| P6 | Sitio pesado (múltiples frameworks) | Un HTML ligero, lazy loading, sin librerías pesadas |
| P7 | Móvil deficiente | Mobile-first, hamburguesa funcional, botones táctiles |
| P8 | Sin anclas ni jerarquía | Menú fijo con anclas a secciones reales de la página |
