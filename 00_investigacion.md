# 00 · Investigación previa — ITESHU

> Documento de evidencia de la Tarea 0. Todos los colores y URLs fueron extraídos
> e inspeccionados directamente de los sitios oficiales (HTML + CSS + píxeles del logo)
> el día de elaboración de este prototipo. **Ningún color ni imagen fue inventado.**

---

## 1. Colores institucionales REALES de iteshu.edu.mx

### 1.1 Fuente: CSS oficial del sitio (`/iteshu/css/opd.css`)

| Hex | Rol real en el sitio | Dónde se encontró |
|---|---|---|
| `#1B396A` | **Azul institucional primario** (navbar, footer `c_gob_azul`) | `opd.css` líneas 233, 258 |
| `#bc955b` | **Dorado / bronce** (borde inferior de 4px del navbar) | `opd.css` línea 234 |
| `#0b231e` | Verde muy oscuro (barra superior gob.mx) | `opd.css` + HTML inline |
| `#611232` | Vino (Gobierno del Estado, clase `c_gob_vino`) | `opd.css` línea 268 |
| `#691B31` | Vino oscuro (hover del menú) | `opd.css` línea 245 |
| `#092432` | Azul-verde muy oscuro (secciones `#oferta_educativa` y `#estudiantes`) | `opd.css` líneas 296, 309 |
| `#222851` | Azul marino (tema del chat oficial de Facebook) | HTML `theme_color="#222851"` |
| `#032b78` | Azul (iconos fijos de accesos) | `opd.css` línea 478 |
| `#d6d3d3` | Gris claro (borde inferior del footer, fondo del titular) | `opd.css` líneas 264, 273 |
| `#f8f8f8` | Gris de fondo (secciones servicios, contacto, bolsa de trabajo) | `opd.css` líneas 321, 326, 342, 466 |
| `#555555` | Gris de texto base | `opd.css` línea 439 |
| `#cc181e` | Rojo (youtube / marcador) | `opd.css` líneas 348, 372 |
| `#ca682d` | Naranja (área de negocios) | `opd.css` líneas 403, 405, 433 |

### 1.2 Fuente: píxeles del logo oficial (`/iteshu/images/header/iteshu.png`)

Análisis de píxeles dominantes (PIL, fondo blanco removido):

| Hex | Muestras | Interpretación |
|---|---|---|
| `#000e51` | 43+29 px | Azul marino del texto "ITESHU" |
| `#006e4d` | 27 px | Verde del acento del logo |

### 1.3 Paleta definitiva para el prototipo (solo colores reales)

```
Primario   #1B396A   (azul institucional — header, footer, botones)
Oscuro     #092432   (secciones de contraste — oferta educativa)
Marino     #222851   (acentos, overlines, hover)
Dorado     #bc955b   (acento premium — bordes, CTAs secundarios, detalles)
Verde      #006e4d   (acento de sustentabilidad — tema central del discurso)
Vino       #611232   (detalles institucionales del Estado de Hidalgo)
Neutros    #f8f8f8 · #d6d3d3 · #555555 · #ffffff
```

---

## 2. Logo oficial y escudo

| Elemento | URL real (verificada HTTP 200) |
|---|---|
| Logo ITESHU (header) | `https://www.iteshu.edu.mx/iteshu/images/header/iteshu.png` |
| Escudo Estado de Hidalgo (footer) | `https://www.iteshu.edu.mx/iteshu/images/footer/footer_escudo.png` |

---

## 3. Imágenes reales de iteshu.edu.mx (todas verificadas HTTP 200)

### 3.1 Carreras / oferta educativa (`/iteshu/images/ofertaEducativa/`)

| Imagen | URL |
|---|---|
| Ingeniería Mecatrónica | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/mecatronica.jpg` |
| Ingeniería en Sistemas Computacionales | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/sistemasc.jpg` |
| Ingeniería en Gestión Empresarial | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/IGEM.jpg` |
| Ingeniería en Administración | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/administarcion.jpg` |
| Ingeniería en Energías Renovables | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/energias.jpg` |
| Ingeniería en Innovación Agrícola Sustentable | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/innovacion.jpg` |
| Ingeniería Industrial | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/industrial.jpg` |
| Arquitectura | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/arquitectura.jpg` |
| Gastronomía | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/gastronomia.jpg` |
| Maestría en Ingeniería Mecatrónica (MIM) | `https://www.iteshu.edu.mx/iteshu/images/ofertaEducativa/MIM.jpg` |

### 3.2 Noticias reales del sitio (junio 2026)

| Imagen | URL |
|---|---|
| Convocatoria Maestría en Desarrollo Regional e Innovación Tecnológica | `https://www.iteshu.edu.mx/iteshu/images/noticias/2026/Junio/023.jpg` |
| Vinculación con educación básica (boletín 022) | `https://www.iteshu.edu.mx/iteshu/images/noticias/2026/Junio/boletin-022.jpg` |

### 3.3 Instalaciones y servicios (`/iteshu/images/alumnos/`)

| Imagen | URL |
|---|---|
| Biblioteca | `https://www.iteshu.edu.mx/iteshu/images/alumnos/biblioteca.jpg` |
| Incubadora de innovación / CIIE-ITESHU | `https://www.iteshu.edu.mx/iteshu/images/alumnos/incubadorainnovacion.jpg` |
| Moodle (plataforma virtual) | `https://www.iteshu.edu.mx/iteshu/images/alumnos/moodle-logo.jpg` |

### 3.4 Banners / convocatorias (`/iteshu/images/slide/`)

| Imagen | URL |
|---|---|
| Banner Maestría 2025 | `https://www.iteshu.edu.mx/iteshu/images/slide/banner--maestria2025.jpg` |
| Banner Fichas 2026 (aspirantes) | `https://www.iteshu.edu.mx/iteshu/images/slide/fichas2026.jpg` |
| Banner Maestría (fichas) | `https://www.iteshu.edu.mx/iteshu/images/slide/Banner-maestria.jpg` |
| Cafetería (tienda escolar) | `https://www.iteshu.edu.mx/iteshu/images/slide/CAfeteria2024.jpg` |

> Base de todas las URLs: `https://www.iteshu.edu.mx`. Se usan únicamente rutas
> oficiales; **prohibido** Unsplash/placeholders.

---

## 4. Datos de contacto reales (footer oficial)

- **Dirección:** Domicilio Conocido s/n, El Saucillo, Huichapan, Hidalgo, C.P. 42411
- **Teléfonos:** (01 761) 724 81 47 · 724 80 79 · 724 80 80 · 724 80 84
- **WhatsApp:** `https://api.whatsapp.com/send?phone=527617248147&text=Información sobre ITESHU`
- **Facebook:** `https://www.facebook.com/ITESHU`
- **Twitter/X:** `https://twitter.com/@ITSHuichapan`
- **Horario:** lunes a viernes, 8:30 a 17:00 hrs
- **Mapa oficial (embed ya usado por el sitio):**
  `https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3741.5369717297785!2d-99.71049928524931!3d20.31942408638685!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85d3bc3d8f22e947%3A0x2e6b2c1efad2535d!2sInstituto%20Tecnol%C3%B3gico%20Superior%20Huichapan!5e0!3m2!1ses-419!2smx!4v1614373783896`

---

## 5. Oferta educativa real (confirmada en el sitio)

**Escolarizada** (`/iteshu/content/ofertaeducativa/escolarizada/escolarizada.php`):
1. Ingeniería Mecatrónica
2. Ingeniería en Sistemas Computacionales
3. Ingeniería en Gestión Empresarial
4. Ingeniería en Administración
5. Ingeniería en Energías Renovables
6. Ingeniería en Innovación Agrícola Sustentable
7. Ingeniería Industrial
8. Arquitectura
9. Gastronomía

**Posgrado** (`/iteshu/content/ofertaeducativa/posgrado/Posgrado.php`):
- Maestría en Ingeniería Mecatrónica
- **Maestría en Desarrollo Regional e Innovación Tecnológica** (NUEVA — noticia
  oficial en la portada del sitio, junio 2026; dos LGAC: Desarrollo Regional
  Sostenible e Innovación Tecnológica e Industria 4.0). Texto oficial de la
  convocatoria disponible en el HTML de la portada.

---

## 6. Referencia de diseño (portales institucionales modernos)

El sitio usa Gantry 5 / UIkit. Secciones observadas:

1. **Header** (`#g-header`) — nav principal + menú móvil tipo offcanvas.
2. **Showcase / Hero** (`#g-showcase`) — slider de imágenes a sangre completa con
   CTAs ("Acceder", "Leer más...").
3. **Feature** (`#g-feature`, clase `fondo2`) — tarjetas de servicios/portales
   (Portal, correo, bibliotecas, movilidad, becas, bachilleres) con botones claros.
4. **Subfeature** (`#g-subfeature`) — franja secundaria de accesos.
5. **Main** (`#g-main`, clase `fondo19`) — contenidos con `jlcontentgrid`:
   - Noticias (cards con imagen + "LEER MÁS")
   - Convocatorias (`#Convocatorias`)
   - Agenda (`#Agenda`)
   - Campus (`#Campus`)
6. **Footer** (`#g-footer`) — institucional, enlaces masivos organizados, min-height alto.

**Firma visual que replicaremos:** mucho whitespace, tarjetas limpias con
imagen + título + botón, CTAs de acceso repetidos y evidentes, secciones
ancladas por id, tipografía legible, jerarquía clara.

---

## 7. Notas de diagnóstico (insumo para Tarea 3)

El sitio actual de ITESHU carga Bootstrap 3, carruseles propios, botones
`w3.css`, un slider de imágenes tipo "avisos/licitaciones" como contenido
principal, modales de Facebook SDK y múltiples scripts pesados; el contenido de
portada está dominado por convocatorias de licitación en lugar de oferta
educativa o experiencias de aspirantes. (Detalle y contraste en `03_diagnostico_web.md`.)
