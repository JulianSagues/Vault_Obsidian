---
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/HTML|HTML]]"
Blocking: []
Categoria: ""
---
### 1. Concepto Clave: Rutas (Paths)

![[image 43.png]]

Antes de insertar multimedia, es fundamental entender las rutas. El atributo `src` (source) es el que indica dónde se encuentra el archivo (imagen, video, etc.).

- **Ruta Absoluta:** Es una dirección URL completa, incluyendo el protocolo (`https`://). Se usa para contenido alojado en otros sitios web.
    - Ejemplo: `https://www.sitioexterno.com/imagen.jpg`
- **Ruta Relativa:** Es la ubicación del archivo en relación al archivo HTML actual. Se usa para archivos que están *dentro* de tu propio proyecto (en la misma carpeta o en subcarpetas).
    - Ejemplo: `assets/imagenes/mi-foto.png`

---

### 2. Imágenes

![[image 44.png]]

- **Etiqueta:** `<img>` (es una etiqueta de autocierre, no necesita `</img>`).
- **Atributos Clave:**
    - `src`: La ruta (relativa o absoluta) del archivo de imagen.
    - `alt`: (Texto Alternativo). **Esencial para accesibilidad** y SEO. Describe la imagen para usuarios que no pueden verla (por discapacidad o si la imagen no carga).
- **Otros Atributos Útiles:**
    - `width` / `height`: Permiten definir un ancho y alto para la imagen (aunque se recomienda hacerlo con CSS).
    - `loading="lazy"`: Mejora la optimización. La imagen solo se cargará cuando el usuario esté a punto de verla (haciendo scroll), en lugar de cargarla al inicio.

---

### 3. Video

![[image 45.png]]

- **Etiqueta:** `<video>...</video>` (esta sí tiene etiqueta de cierre).
- **Atributo Esencial:**
    - `controls`: **Es el atributo más importante.** Añade los controles de reproducción (play, pausa, volumen, línea de tiempo, pantalla completa).
- **Dos formas de cargar la fuente:**
    1. **Simple:** Con el atributo `src` en la misma etiqueta:
`<video src="video.mp4" controls></video>`
    2. **Recomendada (Avanzada):** Usando la etiqueta `<source>` *dentro* de `<video>`. Esto permite ofrecer múltiples formatos (ej: .mp4, .webm) para asegurar la compatibilidad con todos los navegadores.HTML
`<video controls>
  <source src="video.mp4" type="video/mp4">
  Tu navegador no soporta el video HTML5.
</video>`
- **Otros Atributos Útiles:**
    - `autoplay`: El video se reproduce automáticamente al cargar la página.
    - `muted`: Silencia el video. (Nota: La mayoría de navegadores modernos **requieren** que el video esté en `muted` para que `autoplay` funcione).
    - `loop`: El video se vuelve a reproducir en bucle al terminar.
    - `poster`: Muestra una imagen (miniatura) mientras el video carga o antes de darle play.

---

### 4. Audio

![[image 46.png]]

- **Etiqueta:** `<audio>...</audio>`
- **Funcionamiento:** Es prácticamente idéntico al de video.
- **Atributo Esencial:**
    - `controls`: Añade la barra de reproducción de audio.
- También puede usar el atributo `src` o la etiqueta `<source>` interna para compatibilidad.
- **Otros Atributos:** `autoplay`, `loop`, `muted`, `preload` (permite que el navegador vaya precargando el audio).

---

### 5. Enlaces (Hipervínculos)

![[image 47.png]]

- **Etiqueta:** `<a>...</a>` (Anchor o Ancla). El texto *dentro* de la etiqueta es lo que el usuario ve y en lo que puede hacer clic.
- **Atributo Principal:**
    - `href`: (Hypertext Reference). Indica la URL o destino al que el enlace debe dirigir.

### Tipos de Enlaces (según el `href`)

1. **Enlace Externo:** Apunta a un sitio web diferente.
    - Ejemplo: `<a href="https://www.google.com">Ir a Google</a>`
2. **Enlace Interno:** Apunta a otra página *dentro de tu mismo sitio web* o a una sección específica de la página actual.
    - Ejemplo (otra página): `<a href="contacto.html">Contacto</a>`
    - Ejemplo (sección): `<a href="#seccion-uno">Ir a Sección 1</a>`
3. **Enlaces Especiales:**
    - Correo: `<a href="mailto:ejemplo@correo.com">Enviar correo</a>` (abre el cliente de correo del usuario).
    - Teléfono: `<a href="tel:+123456789">Llamar</a>` (inicia una llamada en dispositivos móviles).

### Atributos Importantes de `<a>`

- `target="_blank"`: **Muy importante.** Hace que el enlace se abra en una **nueva pestaña** del navegador. Es una práctica recomendada para enlaces externos, para que el usuario no abandone tu sitio.
- `download`: Indica al navegador que el archivo enlazado (ej: un PDF, un .zip) debe ser descargado en lugar de navegado.
- `nofollow`: Es una instrucción para los motores de búsqueda (SEO) para que no "sigan" ese enlace (no le pasen autoridad).