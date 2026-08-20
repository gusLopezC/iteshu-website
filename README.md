# ITESHU · Prototipo Web estilo UAQ

Prototipo de landing page para el **Instituto Tecnológico Superior de
Huichapan**: identidad 100% institucional (colores, logo y fotografías reales de
iteshu.edu.mx) con la claridad de navegación de uaq.mx.

**Duración de la clase muestra:** 15 minutos · **Carreras:** 9 licenciaturas +
nueva Maestría en Desarrollo Regional e Innovación Tecnológica.

---

## Archivos del proyecto

| Archivo | Contenido |
|---|---|
| `index.html` | **Prototipo principal** (una página, HTML + Tailwind CDN) |
| `00_investigacion.md` | Evidencia: colores hex reales + URLs de imágenes verificadas |
| `01_esquema_clase.md` | Esquema cronológico de la clase (15 min) |
| `02_guion_clase.md` | Guion oral completo con tiempos y contacto visual |
| `03_diagnostico_web.md` | 8 problemas UX del sitio actual vs. la propuesta |
| `04_resumen_comite.md` | Resumen de 1 página para el comité |
| `presentacion.html` | Presentación opcional en Reveal.js (7 diapositivas) |

### Estructura del prototipo (secciones)
1. **Header sticky** — logo real, menú principal con **mega-menú "Oferta Educativa"**
   (todas las carreras + posgrado con enlaces reales), Admisión, Campus, Noticias,
   Contacto + CTA "Quiero ser aspirante" + menú hamburguesa completo en móvil.
2. **Menú institucional** — Identidad · Servicios al alumno · Servicios Escolares ·
   Vinculación · CONAC/LDF · Transparencia (las secciones reales del sitio oficial).
3. **Hero** — tipografía serif de autoridad, foto real, CTA y banda de programas
   en movimiento (chips).
4. **Marquee de acreditaciones** — logos reales CACECA, CACEI, OSHAS, ANFEI, ANUIES.
5. **Servicios / Accesos rápidos** — 6 cards estilo UAQ.
6. **¿Por qué ITESHU?** — acreditaciones, becas, vinculación y campus con datos reales.
7. **Oferta Educativa** — grid de 11 programas con **filtros por área**
   (Todas / Ingenierías / Arquitectura y Gastronomía / Posgrado).
8. **Maestría en Desarrollo Regional e Innovación Tecnológica** — sección destacada.
9. **Vinculación / Transferencia tecnológica** — patente 427385, deshidratador de
   manzana y convenio Legado Verde (proyectos reales del ITESHU).
10. **Admisión** — proceso en 4 pasos.
11. **Noticias / Convocatorias** — con imágenes reales.
12. **Vida estudiantil** — galería con fotos reales del campus.
13. **Campus / Ubicación** — mapa oficial + contacto real.
14. **CTA final** — conversión antes del footer.
15. **Footer** — institucional con accesos, enlaces reales, redes y escudo de Hidalgo.

### Animaciones incluidas en `index.html`
- **Entradas en cascada (stagger):** hero, tarjetas de servicios, carreras,
  admisión y noticias aparecen en secuencia con retardo progresivo.
- **Contadores animados** en el hero (9 programas · 2026 · 3+ acreditaciones).
- **Marquee de acreditaciones** con los logos reales del sitio (CACECA, CACEI,
  OSHAS, ANFEI, ANUIES) — pausa al pasar el cursor.
- **Barra de progreso de lectura** dorada en la parte superior.
- **Micro-interacciones:** botones con brillo (shine), flechas que se deslizan,
  badge flotante, anillo de pulso en WhatsApp, blobs de color animados en el hero.
- **Performance y accesibilidad:** solo `transform/opacity`, `prefers-reduced-motion`
  desactiva todas las animaciones, sin librerías adicionales.

---

## Cómo usar el día de la clase

### 1. Abrir el prototipo
- Doble clic en `index.html` (se abre en Chrome/Edge/Firefox).
- **Requiere internet:** las imágenes se cargan en vivo desde iteshu.edu.mx y
  Tailwind se carga por CDN.
- Atajos útiles: `Ctrl + Mayús + I` → DevTools → icono de móvil para simular
  pantalla de celular y mostrar el menú hamburguesa.

### 2. Comparar con la web actual
- Abrir en otra pestaña `https://www.iteshu.edu.mx/iteshu/`.
- Alternar con `Ctrl + Tab` para el contraste en vivo.
- **Ejercicio para la audiencia:** "¿Cuántos clics para encontrar Mecatrónica
  en el sitio actual?" vs. "a un clic en el prototipo".

### 3. Presentación opcional
- Abrir `presentacion.html` en el navegador.
- Navegar con flechas del teclado; `F` pantalla completa; `Esc` vista general.
- Las 7 diapositivas siguen los 4 bloques del esquema.

### 4. Tips de tiempo (clase de 15 min)
- 0:00–1:00 Elevator pitch · 1:00–7:00 Oferta educativa ·
  7:00–11:00 Diagnóstico · 11:00–15:00 Demo + cierre.
- Si vas retrasado: acortar el recorrido de la demo (bloque 4) antes que el
  diagnóstico (bloque 3) — el pitch y la oferta son innegociables.
- Respaldo: si la red falla, tener abiertas las capturas de `research/preview_*.png`.

---

## Checklist de verificación final

### ✅ Colores institucionales
- [ ] `#1B396A` azul institucional (header, hero, footer, botones) — del CSS oficial
- [ ] `#092432` sección oferta educativa — del CSS oficial
- [ ] `#bc955b` dorado (CTAs, acentos, marco) — del CSS oficial
- [ ] `#006e4d` verde (logo) · `#611232` vino · `#0b231e` barra gob.mx
- [ ] Sin colores inventados (evidencia en `00_investigacion.md`)

### ✅ Imágenes reales (todas iteshu.edu.mx, verificadas HTTP 200)
- [ ] Logo oficial `images/header/iteshu.png` (header + footer)
- [ ] 9 imágenes de carreras `images/ofertaEducativa/*.jpg`
- [ ] Fotos reales de instalaciones (biblioteca, incubadora)
- [ ] Fotos reales de noticias (convocatoria maestría, vinculación)
- [ ] Escudo Hidalgo + mapa oficial de Google Maps
- [ ] Sin Unsplash ni placeholders

### ✅ Secciones estilo UAQ
- [ ] Header sticky con menú + CTA "Quiero ser aspirante"
- [ ] Hero con foto real, título y subtítulo de sustentabilidad/transferencia
- [ ] Cards de servicios/accesos rápidos (Oferta, Portal, Admisión, Convocatorias, Moodle, Contacto)
- [ ] Oferta educativa en grid visual (9 carreras)
- [ ] Sección especial de la nueva Maestría (LGAC + convocatoria)
- [ ] Noticias / Convocatorias con imágenes reales
- [ ] Campus con mapa y datos de contacto reales
- [ ] Footer institucional limpio

### ✅ Responsividad e interactividad
- [ ] Mobile-first (probado a 390px)
- [ ] Menú hamburguesa funcional (abre/cierra, Esc, resize)
- [ ] Hovers elegantes en tarjetas
- [ ] Sin errores de consola (validado en Chrome headless)
- [ ] Accesibilidad básica (skip link, aria, alt, focus, reduced-motion)
- [ ] Imágenes lazy loading + dimensiones fijas (sin layout shift)
- [ ] Animaciones de entrada: stagger, contadores, marquee, barra de progreso
- [ ] Animaciones desactivadas con `prefers-reduced-motion`

---

*Colores y fotos extraídos e inspeccionados directamente de iteshu.edu.mx.
Ver `00_investigacion.md` para la evidencia completa.*
