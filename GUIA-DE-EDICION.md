# GUÍA DE EDICIÓN — PORTFOLIO ARKAIKA

Este portfolio es una web estática. Puedes modificarla sin pagar una plataforma ni instalar un gestor de contenidos.

## 1. Preparar el entorno

1. Extrae la carpeta `portafolio-arkaika-editable` del ZIP. **No edites directamente dentro del ZIP.**
2. Instala Visual Studio Code: https://code.visualstudio.com/
3. En Visual Studio Code: **Archivo > Abrir carpeta** y selecciona la carpeta extraída.
4. Abre `index.html`.
5. Para verla, abre el mismo `index.html` en Chrome, Edge o Firefox. Después de guardar (`Ctrl + S`), actualiza el navegador (`F5`).
6. Antes de experimentar, duplica la carpeta como copia de seguridad.

**Atajo útil:** `Ctrl + F` busca una palabra; `Ctrl + H` permite reemplazar. En Mac suele ser `Cmd` en lugar de `Ctrl`.

## 2. Estructura

- `index.html`: textos de la portada, galería, biografía, contacto, colores, diseño y comportamiento.
- `assets/logo-arkaika.png`: imagen del logo.
- `assets/estructura-cubierta.png`: captura actual del modelo 3D; es provisional.
- `LEEME.txt`: notas del primer paquete.

En `index.html` he añadido comentarios como `<!-- PORTADA -->`, `<!-- PROYECTOS -->`, etc. Puedes buscarlos para ir a cada bloque.

## 3. Cambiar textos

En el HTML, cambia **solo el texto visible entre etiquetas**, respetando símbolos como `<`, `>`, comillas y las etiquetas de apertura/cierre.

Ejemplo de la portada:

```html
<h1>El pasado, en <span class="accent">nuevas dimensiones.</span></h1>
```

Sustituye las palabras, pero mantén `h1` y `span` para conservar el formato.

Otros lugares:
- Busca `class="hero-lead"`: introducción.
- Busca `id="sobre-mi"`: biografía.
- Busca `id="herramientas"`: lista de programas.
- Busca `id="contacto"`: contacto.
- Busca `class="brand-name"`: nombre superior de la web.

## 4. Cambiar o añadir imágenes

Copia las imágenes en `assets` y usa un nombre simple sin espacios, por ejemplo `levantamiento-muro.jpg`.

Ejemplo:

```html
<img src="assets/levantamiento-muro.jpg" alt="Modelo fotogramétrico de un muro histórico" loading="lazy">
```

- `src` es la **ruta real** a la imagen. El nombre y la extensión deben coincidir exactamente, con mayúsculas y minúsculas.
- `alt` es una descripción breve, útil para accesibilidad.
- Usa JPG o WebP para renders/fotografías; PNG cuando sea importante preservar transparencias o imágenes sin pérdida.
- Para cambiar la imagen de portada, busca `class="hero-image-wrap"`.
- Para cambiar el logo, sustituye el archivo manteniendo su nombre o modifica `src="assets/logo-arkaika.png"`.

El modelo de cubierta aparece **dos veces**: en la portada y en la primera tarjeta. Cambia ambas rutas si quieres sustituirlo en ambos sitios.

## 5. Añadir un proyecto NUEVO

En `index.html`, busca `class="project-grid"`. Dentro encontrarás tarjetas `<article class="project" ...> ... </article>`.

Copia una tarjeta real completa, desde `<article...>` hasta su correspondiente `</article>` (no uses las tarjetas con `placeholder`) y pégala **justo antes de** `</div>` que cierra `project-grid`.

Luego modifica: `data-category`, `data-details`, imagen, `alt`, número, categoría visible, título y resumen.

Ejemplo listo para personalizar:

```html
<article class="project" data-category="fotogrametria"
  data-details="Objetivo: documentar una pieza arqueológica. Método: captura fotográfica y procesamiento con Metashape. Resultados: [completar].">
  <div class="project-art">
    <img src="assets/mi-proyecto.jpg"
         alt="Vista del modelo fotogramétrico de mi proyecto" loading="lazy">
    <span class="project-number">02</span>
  </div>
  <div class="project-info">
    <div class="project-meta">Fotogrametría · Trabajo propio</div>
    <h3 class="project-title">Título del nuevo proyecto</h3>
    <p class="project-desc">Resumen breve del trabajo y su interés.</p>
    <button class="project-link" data-open-project type="button">
      Ver proyecto <span aria-hidden="true">↗</span>
    </button>
  </div>
</article>
```

**Importante:** sustituye `mi-proyecto.jpg` por la imagen real y reescribe el ejemplo; no publiques datos de un proyecto que no hayas realizado.

Filtros disponibles (escríbelos exactamente así en `data-category`):
- `modelado` → **Modelado 3D**
- `fotogrametria` → **Fotogrametría**
- `civil` → **Planimetría/CAD**
- `documentacion` → **Documentación/QGIS**
- `tfg` → **TFG**

En esta nueva versión el botón **Ver proyecto** abre una ficha generada con la información de **esa tarjeta**. El texto largo se toma de `data-details`; si lo dejas vacío, usa la descripción breve. Si quieres adjuntar varias imágenes por trabajo o un modelo giratorio, más adelante podremos ampliar las fichas.

### ¿Qué hago con los espacios reservados?

Las tarjetas con la clase `placeholder` son espacios reservados que puedes dejar mientras completas el portfolio. Para eliminarlas, borra cada bloque completo `<article class="project placeholder ..."> ... </article>` sin tocar los otros artículos.

## 6. Cambiar la paleta

Busca al comienzo de `<style>` el comentario `PALETA DE COLORES`. Verás variables CSS como:

```css
--bg: #F6F2EA;
--terracotta: #B76D50;
--sand: #C99F76;
--stone: #586A65;
```

Prueba a cambiar un solo valor cada vez, guarda y actualiza el navegador.

## 7. Añadir correo y redes

Dentro de `id="contacto"`, cambia el texto provisional por tus datos reales. Ejemplo de enlace (pon tu correo real):

```html
<a href="mailto:TU_CORREO@DOMINIO.COM">Escríbeme por correo</a>
```

Para otras páginas, usa `<a href="https://...">Ver perfil</a>`. Mantén privados los datos que no quieras publicar.

## 8. Problemas frecuentes

**No cambia la página:** guarda (`Ctrl + S`) y recarga (`Ctrl + R` / `F5`). Comprueba que has abierto el archivo correcto.

**No se muestra una imagen:** comprueba la carpeta `assets`, la extensión `.jpg` / `.png` / `.webp` y las mayúsculas.

**Una tarjeta no se filtra bien:** revisa que `data-category` coincida con su categoría: `modelado`, `fotogrametria`, `civil`, `documentacion` o `tfg`.

**Sale la misma información en todas las fichas:** asegúrate de que estás usando `index.html` de este ZIP nuevo, que contiene el botón `data-open-project` y el campo `data-details` en cada tarjeta.

**He roto algo del diseño:** recupera la copia de seguridad, o deshaz con `Ctrl + Z`.

## 9. Publicar después

Cuando estés conforme, podrás subir la carpeta a un alojamiento estático (GitHub Pages, Netlify o Cloudflare Pages), sin cambiar la estructura. Los archivos `.blend`, `.psx` y `.dwg` **no se muestran automáticamente en el navegador**: para un modelo 3D interactivo necesitarás una exportación web, como `.glb`, o un visor incrustado.

---

Sugerencia de orden: primero cambia título y biografía; después sustituye el render provisional de portada; luego añade **un** proyecto nuevo y comprueba el filtro y la ficha, antes de añadir el resto.
