---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/HTML\\|HTML]]"
---
### 1. ¿Qué es una Tabla y Cuándo Usarla?

![[Assets/image 448.png|image 448.png]]

Una tabla es una estructura que permite **organizar datos en filas y columnas**, facilitando la representación de información de manera ordenada.

- **Uso Correcto (Buena Práctica):**
    
    - Se deben usar **exclusivamente para datos tabulares**.
    
    - Ejemplos: Listas de productos, horarios, calendarios, resultados, datos estadísticos, información de contacto.
    

- **Uso Incorrecto (Mala Práctica):**
    
    - **Usar tablas para maquetar o diseñar** el layout de una página web. Esta era una técnica antigua, pero hoy se considera una mala práctica (para eso se usa CSS).
    
    - Crear formularios o elementos de navegación con ellas.
    

---

### 2. Elementos Básicos de una Tabla

![[Assets/image 1 40.png|image 1 40.png]]

Estos son los componentes fundamentales para crear cualquier tabla:

- `<table>`: La etiqueta principal que **envuelve toda la tabla**.

- `<tr>` (Table Row): Define una **fila** dentro de la tabla.

- `<th>` (Table Head): Define una celda de **encabezado** (el título de una columna). El texto aparece centrado y en negrita por defecto.

- `<td>` (Table Data): Define una celda de **datos** regular (el contenido de la tabla).

![[Assets/image 2 37.png|image 2 37.png]]

> Nota sobre border="1": En los ejemplos se usa el atributo border="1" dentro de la etiqueta <table>. Esto es solo una ayuda visual para el desarrollador para ver la separación de las celdas. Si se quita, la tabla sigue existiendo, pero sin bordes visibles. El estilo de bordes hoy en día se maneja con CSS.

---

### 3. Estructura Semántica (Avanzada)

![[Assets/image 3 31.png|image 3 31.png]]

Para tablas más complejas y semánticamente correctas (mejor para accesibilidad y SEO), la tabla se divide en tres secciones:

- `<thead>`: Agrupa las filas (`<tr>`) que contienen los **encabezados** (`<th>`).

- `<tbody>`: Agrupa las filas (`<tr>`) que contienen los **datos principales** del cuerpo (`<td>`).

- `<tfoot>`: Agrupa las filas (`<tr>`) que contienen la **información de resumen** o pie de página.

### Ventajas de usar `<thead>`, `<tbody>` y `<tfoot>`

![[Assets/image 4 25.png|image 4 25.png]]

- **Mejor Semántica:** Ayuda al navegador y a los motores de búsqueda a entender mejor la estructura de los datos.

- **Accesibilidad:** Fundamental para que los lectores de pantalla (screen readers) puedan interpretar y narrar la tabla correctamente a usuarios con discapacidad visual.

- **Estilos con CSS:** Facilita aplicar estilos diferentes a la cabecera, el cuerpo y el pie de la tabla.

- **Scroll en Tablas Largas:** Permite que el navegador mantenga visibles `<thead>` y `<tfoot>` mientras el usuario hace scroll solo por el `<tbody>`.

![[Assets/image 5 17.png|image 5 17.png]]

---

### 4. Atributos Especiales para Celdas

Permiten que una celda ocupe el espacio de varias columnas o filas.

- `colspan="3"`: (Column Span). Hace que una celda se expanda **horizontalmente** para ocupar el espacio de un número determinado de **columnas** (ej: 3 columnas).

![[Assets/image 6 16.png|image 6 16.png]]

  

![[Assets/image 7 15.png|image 7 15.png]]

  

- `rowspan="2"`: (Row Span). Hace que una celda se expanda **verticalmente** para ocupar el espacio de un número determinado de **filas** (ej: 2 filas).

![[Assets/image 8 13.png|image 8 13.png]]

  

![[Assets/image 9 12.png|image 9 12.png]]