---
Parent item:
  - "[[Materias/Desarrollo de software/HTML\\|HTML]]"
---
![[Assets/image 67.png|image 67.png]]

### 1. Elementos Básicos de Formato

Este video profundiza en las etiquetas de texto, expandiendo lo visto en el video anterior.

![[Assets/image 1 41.png|image 1 41.png]]

### Encabezados (`<h1>` - `<h6>`)

- Son los títulos y subtítulos de la página.

- **Jerarquía:** Van del `<h1>` (más importante) al `<h6>` (menos importante).

- **Regla Clave (Semántica y SEO):** Solo debe existir **un** `**<h1>**` **por página**, ya que define el tema principal para los motores de búsqueda (Google, etc.).

- Las etiquetas `<h2>` al `<h6>` sí se pueden repetir para estructurar el contenido en secciones y subsecciones.

### Párrafos (`<p>`)

- Define un bloque de texto.

- El navegador añade automáticamente un espaciado (margen) antes y después de cada párrafo.

### Saltos de Línea (`<br>`)

- Inserta un salto de línea simple.

- Es una etiqueta "vacía" o "autocerrada" (no necesita cierre como `</br>`).

- Se usa _dentro_ de otro elemento (como un `<p>`) para forzar que el texto continúe en la línea siguiente sin crear un nuevo bloque de párrafo.

---

![[Assets/image 2 39.png|image 2 39.png]]

### 2. Elementos de Énfasis Textual

Es importante diferenciar entre etiquetas que dan **importancia semántica** (le dicen al navegador _qué es_ el texto) y las que solo dan un **formato visual**.

### Negrita

- `<strong>`: **Énfasis semántico.** Indica que el texto es importante, serio o urgente. Los navegadores y lectores de pantalla lo interpretan como tal.

- `<b>`: **Énfasis visual.** Simplemente pone el texto en negrita sin añadirle una importancia semántica especial.

### Cursiva

- `<em>`: **Énfasis semántico.** (Emphasis). Indica un énfasis verbal, como cambiar el tono de voz.

- `<i>`: **Énfasis visual.** Se usa para textos en otro idioma, términos técnicos, nombres de barcos, etc., sin un énfasis especial.

---

### 3. Otros Énfasis y Formatos

- `<mark>`: Resalta el texto, como si se usara un **marcador o resaltador**.

- `<ins>`: Indica texto que ha sido **insertado** en el documento. Los navegadores suelen mostrarlo **subrayado**.

- `<u>`: **Subrayado** simple. Es puramente visual.

- `<del>`: Indica texto que ha sido **eliminado** del documento. Los navegadores lo muestran **tachado**.

- `<small>`: Hace que el texto se vea con una **fuente más pequeña**. Útil para "letra pequeña", comentarios o derechos de autor.

- `<span>`: Es un contenedor genérico _en línea_ (inline). No hace nada por sí mismo, pero es muy útil para agrupar texto y aplicarle estilos con CSS después.

- `<hr>`: (Horizontal Rule). Crea una **línea horizontal** que ocupa todo el ancho disponible. Se usa para separar secciones o temas temáticamente.

![[Assets/image 3 33.png|image 3 33.png]]

---

### 4. Repaso de Herramientas y Ejecución

- **Editor Recomendado:** Visual Studio Code.

- **Extensión Clave: Live Server**.

- **Flujo de trabajo:**
    
    1. Instalar la extensión "Live Server" en VS Code.
    
    1. Crear tu archivo (ej: `index.html`).
    
    1. Hacer clic en "Go Live" (usualmente en la barra inferior de VS Code).
    
    1. Esto abre tu página en el navegador. Cada vez que guardes el archivo (Ctrl+S), el navegador se actualizará automáticamente para mostrar los cambios en tiempo real.
    

### 5. Jerarquía Visual vs. Estilos

- El video aclara que, por defecto, el navegador aplica estilos visuales basados en la semántica de la etiqueta.

- Por eso, un `<h1>` se ve más grande que un `<h2>`, y así sucesivamente hasta el `<h6>`.

- Esto **no son estilos CSS** (que se verán más adelante), sino la forma en que el navegador interpreta la importancia jerárquica de cada encabezado.

Ejemplo con las etiquetas mostradas:

![[Assets/image 4 26.png|image 4 26.png]]

  

Lo que tira:

![[Assets/image 5 19.png|image 5 19.png]]