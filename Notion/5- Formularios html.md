---
notion-id: 2a0ac26b-dee7-80d1-af47-c5eaa95a32b2
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 2a0ac26b-dee7-8055-a42b-fa0595fa3a9c
Blocking: []
Categoria: ""
---
### 1. ¿Qué es un Formulario?

Un formulario es un componente interactivo esencial que permite **recopilar información del usuario** para ser procesada por un servidor.

- **Etiqueta Principal:** `<form>...</form>`
- **Función:** Facilita la comunicación entre el usuario y la aplicación web (el "backend").
- **Usos Comunes:** Procesos de registro (sign-up), inicio de sesión (login), barras de búsqueda, encuestas, procesos de pago, etc.

---

### 2. La Estructura Base: La Etiqueta `<form>`

La etiqueta `<form>` envuelve todos los campos y tiene dos atributos principales que definen su comportamiento:

- `action`: Define la **URL del backend** (el "endpoint" o script en el servidor) a la cual **se enviarán los datos** recopilados cuando el usuario presione el botón de envío.
- `method`: Define el método HTTP que se usará para enviar los datos. El más común es `post`, que se utiliza para enviar datos para ser procesados o guardados.

---

### 3. Componentes Esenciales de un Formulario

- `<input>`: Es el elemento principal para que el usuario ingrese datos. Es una etiqueta auto-cerrada. Su comportamiento cambia drásticamente según su atributo `type`.
- `<label>`: Es el texto descriptivo que acompaña a un input. Es **fundamental para la accesibilidad**.
- `<button type="submit">`: Es el botón que, al ser presionado, **dispara el **`**action**` del formulario y envía todos los datos.
    - *Alternativa:* `input type="submit"`, aunque `<button>` es más flexible y recomendado.

---

### 4. Accesibilidad: La Importancia de `<label>`

El `label` asocia un título o texto descriptivo a un campo específico del formulario.

- **Implementación:** Se conecta usando el atributo `for` (en el `<label>`) que debe coincidir con el atributo `id` (en el `<input>`).
- **Ejemplo:**HTML
`<label for="nombre_usuario">Nombre:</label>
<input type="text" id="nombre_usuario" name="nombre_usuario">`
- **Beneficios:**
    1. **Accesibilidad:** Los lectores de pantalla (screen readers) anuncian el `label` cuando el `input` está enfocado, permitiendo al usuario saber qué debe ingresar.
    2. **Usabilidad:** Aumenta el área "clicable". El usuario puede hacer clic tanto en el campo como en el texto del `label` para activar el `input`.

---

### 5. Tipos de Campos Comunes (`<input>` y `<textarea>`)

- `<input type="text">`: Campo de texto simple para datos alfanuméricos.
- `<input type="email">`: Valida automáticamente que el texto ingresado tenga un formato de email válido (que contenga `@` y un dominio).
- `<input type="tel">`: Optimizado para la entrada de números de teléfono.
- `<input type="file">`: Permite al usuario seleccionar un archivo de su dispositivo para subirlo.
    - *Atributo complementario:* `accept` (ej: `accept="image/png, image/jpeg"` para limitar los tipos de archivo).
- `<input type="range">`: Muestra un control deslizante (slider), útil para seleccionar un valor en un rango (ej: volumen). Requiere atributos `min` y `max`.
- `<textarea>`: **No es un **`**<input>**`. Es una etiqueta separada (`<textarea>...</textarea>`) diseñada para **texto largo** (mensajes, comentarios, descripciones). Se le puede definir el tamaño con los atributos `rows` (filas) y `cols` (columnas).

---

### 6. Atributos Clave de los Inputs

- `name`: El **identificador clave** que usa el servidor para saber qué dato está recibiendo. (Ej: `<input name="nombre">` enviará el dato como `nombre=valor_ingresado`).
- `placeholder`: Muestra un texto de ejemplo *dentro* del campo, que desaparece automáticamente cuando el usuario empieza a escribir.
- `title`: Muestra un *tooltip* (mensaje emergente) cuando el usuario posa el cursor sobre el elemento. Mejora la accesibilidad y sirve para dar pistas.

---

### 7. Validación Nativa de HTML5

Son atributos que permiten al navegador validar los datos *antes* de enviarlos al servidor.

- `required`: Es un atributo booleano. El formulario **no se puede enviar** si este campo está vacío o (en tipos como `email`) es inválido.
- `pattern`: Permite definir una **expresión regular (regex)** para una validación mucho más estricta (ej: un formato específico de DNI o código postal).
- `minlength` / `maxlength`: Define el número mínimo y máximo de caracteres permitidos (para `type="text"`).
- `min` / `max`: Define el valor numérico mínimo y máximo (para `type="number"` o `type="range"`).

---

### 8. Agrupación de Campos (Estructura)

- `<fieldset>`: Etiqueta que **agrupa semánticamente** un conjunto de campos relacionados (ej: "Datos Personales", "Datos de Dirección"). El navegador suele dibujar un recuadro a su alrededor.
- `<legend>`: Define el **título** de un `<fieldset>`. Debe ser el primer elemento hijo dentro del `fieldset`.
