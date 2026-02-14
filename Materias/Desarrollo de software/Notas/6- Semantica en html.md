---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/HTML\\|HTML]]"
---
### 1. ¿Qué es la Semántica en HTML?

La semántica se refiere al **significado** de las cosas. En HTML, esto implica usar etiquetas que **describan claramente su propósito y el contenido** que albergan, en lugar de usar etiquetas genéricas que solo definen su apariencia.

El HTML semántico responde al "**¿Qué es esto?**" y no solo al "**¿Cómo se ve?**".

- **Ejemplo:** Usar `<header>` en lugar de `<div class="encabezado">`.
    
    - `<div>` es genérico, no significa nada.
    
    - `<header>` le dice explícitamente al navegador, a los desarrolladores y a los motores de búsqueda: "Este es el encabezado de la página".
    

### 2. Ventajas del HTML Semántico

1. **Mejora la Accesibilidad:**
    
    - Es la ventaja más destacada.
    
    - Los lectores de pantalla (screen readers) y otras tecnologías asistivas pueden interpretar correctamente la estructura de la página.
    
    - Esto permite a usuarios con discapacidades navegar el sitio de forma lógica (ej: saltar directamente a la navegación o al contenido principal).
    

1. **Optimización para Motores de Búsqueda (SEO):**
    
    - Los "rastreadores" (bots) de motores de búsqueda como Google entienden mejor la jerarquía y la relevancia del contenido.
    
    - Al entender qué es el título, qué es la navegación y qué es el contenido principal, pueden indexar la página de forma más precisa y mejorar su posicionamiento.
    

1. **Facilita el Mantenimiento:**
    
    - El código es mucho más legible y limpio para los desarrolladores.
    
    - Es fácil ubicar dónde comienza y termina cada bloque de la página (`<header>`, `<main>`, `<footer>`, etc.) para realizar modificaciones.
    

### 3. Los Elementos Centrales de la Estructura Semántica

Estas etiquetas reemplazan a los `<div>` genéricos para definir la estructura principal de una página web:

- `<header>`: El encabezado. Generalmente contiene el logo, el título del sitio y, a veces, la navegación principal.

- `<nav>`: La sección de navegación. Contiene los enlaces principales del sitio (ej: "Inicio", "Servicios", "Contacto").

- `<main>`: **El contenido principal y único** de la página. Todo el contenido que no se repite en otras páginas (como el header o el footer) debe ir aquí. **Solo debe haber un** `**<main>**` **por página.**

- `<section>`: Define una agrupación temática de contenido _dentro_ del `<main>` (ej: una sección "Servicios", una sección "Formulario de Contacto").

- `<aside>`: Define contenido complementario o relacionado que no es parte del flujo principal del `<main>` (ej: una barra lateral con horarios, datos de contacto, enlaces relacionados).

- `<footer>`: El pie de página. Generalmente contiene información de copyright, enlaces secundarios, información de contacto, etc.

### 4. Comparación: Divs vs. Semántica

Así se ve la diferencia en el código:

### ❌ El Método Antiguo (y malo) con `<div>`

HTML

`<body> <div class="header"> <h1>Mi Sitio Web</h1> </div> <div class="nav"> <ul>...</ul> </div> <div class="main-content"> <div class="contact-form">...</div> <div class="sidebar">...</div> </div> <div class="footer"> <p>&copy; 2025</p> </div> </body>`

### ✅ El Método Moderno (y correcto) con Semántica

HTML

`<body> <header> <h1>Mi Sitio Web</h1> </header> <nav> <ul>...</ul> </nav> <main> <section> <h2>Formulario</h2> ... </section> <aside> <h3>Horarios</h3> ... </aside> </main> <footer> <p>&copy; 2025</p> </footer> </body>`

Ambos pueden _verse_ igual con CSS, pero la versión semántica es infinitamente superior para la accesibilidad, el SEO y el mantenimiento.

### 5. ¿Qué es el SEO?

- **SEO** son las siglas de **Search Engine Optimization** (Optimización para Motores de Búsqueda).

- Es el conjunto de técnicas usadas para mejorar la visibilidad y el posicionamiento de un sitio web en los resultados de búsqueda (como Google).

- Usar HTML semántico es una de las técnicas fundamentales del SEO, ya que **ayuda a los buscadores a entender de qué trata tu página**.

- Otras prácticas semánticas que ayudan al SEO (mencionadas en videos anteriores) son:
    
    - Usar el atributo `alt` en las imágenes (`<img>`).
    
    - Usar la etiqueta `<label>` en los formularios (`<form>`).
    
    - Tener una correcta jerarquía de encabezados (`<h1>`, `<h2>`, etc.).