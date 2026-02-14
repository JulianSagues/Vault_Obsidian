---
notion-id: 2a0ac26b-dee7-80ac-b16a-d5a26dd7ad0f
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 2a0ac26b-dee7-8055-a42b-fa0595fa3a9c
Blocking: []
Categoria: ""
---
![[image 9.png]]

### 1. ¿Qué es HTML?

- **Significado:** HTML son las siglas de **Hypertext Markup Language** (Lenguaje de Marcado de Hipertexto).
- **Hipertexto:** Se refiere a la forma en que las páginas web se vinculan entre sí (enlaces).
- **Marcado:** Indica que se usan **etiquetas** (tags) para definir la estructura y el significado del contenido (texto, imágenes, videos, etc.).
- **Aclaración Importante:** HTML **no es un lenguaje de programación**, es un **lenguaje de marcado**. Su función principal es *describir la estructura* del contenido, no crear lógica o algoritmos.

![[image 10.png]]

### 2. La Analogía del Esqueleto

Una buena forma de entender HTML es pensarlo como el **esqueleto de una casa**:

- Define la estructura base, los cimientos, las paredes y las habitaciones.
- Nos dice *dónde* va cada cosa (el título principal, un párrafo, una imagen).
- Esta estructura se crea *antes* de aplicar cualquier estilo (CSS, que sería la "pintura y decoración") o interactividad (JavaScript, que sería la "electricidad").

### 3. ¿Cómo Funciona?

El proceso desde el código hasta lo que ves en pantalla tiene tres pasos:

1. **Solicitud:** El navegador (Chrome, Firefox, etc.) solicita y recibe el archivo `.html` desde un servidor (cuando accedes a una URL) o desde tu computadora (localmente).
2. **Interpretación:** El navegador lee el archivo HTML línea por línea y procesa cada etiqueta para entender cómo debe organizar el contenido.
3. **Renderizado (Visualización):** Una vez interpretado, el navegador "dibuja" y muestra los elementos en la pantalla (un título más grande, un párrafo de texto, etc.) para que el usuario pueda verlos.

### 4. Estructura Básica de un Documento HTML

Todo archivo HTML sigue esta estructura fundamental:

![[image 11.png]]

- `<!DOCTYPE html>`: Declara que el documento es de tipo **HTML5** (la versión estándar actual).
- `<html>...</html>`: Es la etiqueta raíz que envuelve todo el contenido de la página. El atributo `lang="es"` indica que el idioma es español.
- `<head>...</head>`: Contiene **metadatos** (información *sobre* la página). **No es visible** para el usuario en la ventana principal.
- `<body>...</body>`: Contiene **todo el contenido visible** de la página web (títulos, textos, imágenes, enlaces, etc.).

![[image 12.png]]

### 5. El `<head>`: Los Metadatos

La sección `<head>` le da información importante al navegador:

- `<meta charset="UTF-8">`: Define la codificación de caracteres. Es fundamental para que se muestren correctamente caracteres especiales como la 'ñ' (soporta Unicode).
- `<meta name="viewport" ...>`: Indica al navegador cómo ajustar el ancho y el zoom inicial de la página. Es esencial para el **diseño responsivo** (que se vea bien en móviles, tablets y computadoras).
- `<title>...</title>`: Define el texto que aparece en la **pestaña del navegador**.

![[image 13.png]]

En el body va toda la estructura de mi pagina html.

![[image 14.png]]

![[image 15.png]]

![[image 16.png]]

### 6. Anatomía de una Etiqueta HTML

Las etiquetas son las instrucciones que usa HTML.

- **Etiqueta con cierre:** La mayoría tienen una etiqueta de apertura, contenido y una etiqueta de cierre.
    - Ejemplo: `<p>Este es el contenido del párrafo.</p>`
- **Etiqueta de autocierre (vacía):** Algunas etiquetas no necesitan cierre porque no "envuelven" contenido.
    - Ejemplo: `<img src="imagen.jpg" alt="descripción de la imagen">`
- **Atributos:** Son propiedades adicionales que definen el comportamiento o las propiedades de un elemento. (Ej: `src` y `alt` en `<img>`, o `lang` en `<html>`).

![[image 17.png]]

### 7. Primeras Etiquetas Clave (Dentro del `<body>`)

- `<h1>`: **Encabezado Principal.**
    - Es el título más importante de la página.
    - Es crucial para el **SEO** (motores de búsqueda) y para que el usuario entienda de qué trata la página.
    - **Recomendación:** Debe haber **solo un **`**<h1>**`** por página**.
- `<p>`: **Párrafo.**
    - Es el bloque fundamental para organizar el texto en la página.