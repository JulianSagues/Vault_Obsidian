---
notion-id: 2a7ac26b-dee7-80ed-8708-d0a306e4afbf
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 2a7ac26b-dee7-809e-8a5b-cc54fb66c369
Blocking: []
Categoria: ""
---
### 🎯 El Problema: Endpoints Rígidos

![[image 48.png]]

Una API que no puede recibir datos de entrada es inútil. No podríamos buscar un usuario por su ID, filtrar productos por categoría, o crear un nuevo registro. Este video soluciona eso.

---

### 💡 Las 3 Formas de Recibir Datos en Spring Boot

![[image 49.png]]

![[image 50.png]]

![[image 51.png]]

![[image 52.png]]

Spring Boot nos da tres anotaciones principales para capturar datos, cada una con un propósito específico:

| **Anotación** | **Propósito** | **Ejemplo de URL** | **Uso Típico** |
| --- | --- | --- | --- |
| `**@PathVariable**` | Captura valores **desde la ruta** (path) de la URL. | `GET /usuarios/123` | **Obligatorio.** Para identificar un recurso específico (ej. un ID). |
| `**@RequestParam**` | Captura valores **desde la query string** (después del `?`). | `GET /productos?cat=tech` | **Opcional.** Para filtros, paginación o búsquedas. |
| `**@RequestBody**` | Captura un objeto **JSON completo** desde el **cuerpo** de la petición. | `POST /usuarios` | **Obligatorio.** Para enviar datos complejos (crear/actualizar un recurso). |

---

### ✨ La Magia de Jackson: ¿Cómo funciona `@RequestBody`?

![[image 53.png]]

Spring Boot usa una librería llamada **Jackson** (incluida por defecto con el *starter web*).

- **Deserialización:** Cuando envías un JSON a un *endpoint* con `@RequestBody`, Jackson lee el JSON y lo **convierte automáticamente en un objeto Java** (un POJO o un `Map`).
- **Serialización:** Cuando devuelves un objeto Java, Jackson lo convierte automáticamente en un JSON de respuesta.

---

### 💻 Demostración Práctica

En el video, se crea un `UsuarioController` para probar las tres formas.

**Importante:** Se usa `@RequestMapping("/usuarios")` a nivel de la clase. Esto significa que todas las URLs de los métodos dentro de este controlador comenzarán con `/usuarios`.

### 1. Prueba `@PathVariable`

- **Endpoint:**Java
`@GetMapping("/{id}")
public Map<String, String> obtenerUsuario(@PathVariable String id) {
    // ...lógica...
    return Map.of("id_recibido", id);
}`
- **Prueba en Postman:**
    - **Acción:** `GET`
    - **URL:** `http://localhost:8080/usuarios/123`
    - **Resultado:** Spring captura `"123"` de la URL y lo inyecta en la variable `id`. La respuesta es `{"id_recibido": "123"}`.

### 2. Prueba `@RequestParam`

- **Endpoint:**Java
`@GetMapping
public Map<String, String> buscar(
    @RequestParam(required = false) String categoria,
    @RequestParam(defaultValue = "0") String pagina
) {
    return Map.of("categoria", categoria, "pagina", pagina);
}`
- **Prueba en Postman:**
    - **Acción:** `GET`
    - **URL:** `http://localhost:8080/usuarios?categoria=admin&pagina=2`
    - **Resultado:** `{"categoria": "admin", "pagina": "2"}`.
    - *Nota:* Postman tiene una pestaña "Params" para agregar esto fácilmente.

### 3. Prueba `@RequestBody`

- **Endpoint:**Java
`@PostMapping
public Map<String, Object> crearUsuario(@RequestBody Map<String, Object> nuevoUsuario) {
    // ...lógica...
    return Map.of("recibido", nuevoUsuario);
}`
- **Prueba en Postman:**
    - **Acción:** `POST`
    - **URL:** `http://localhost:8080/usuarios`
    - **Pestaña Body:** Se selecciona `**raw**` y tipo `**JSON**`.
    - **Se envía:**JSON
`{
  "nombre": "Juan",
  "email": "juan@mail.com"
}`
    - **Resultado:** La respuesta contiene el JSON que se envió: `{"recibido": {"nombre": "Juan", "email": "juan@mail.com"}}`.

---

### ⚠️ Errores Comunes

- Olvidar la anotación (`@PathVariable`, `@RequestParam`) en el parámetro del método.
- Enviar un JSON mal formateado en el `RequestBody` (causa un **Error 400 Bad Request**).
- Probar con la aplicación Spring Boot apagada.

---

### ✅ Conclusión y Próximos Pasos

- Con estas 3 anotaciones (`@PathVariable`, `@RequestParam`, `@RequestBody`) ya se puede manejar la gran mayoría de casos de uso para recibir datos.
- **Próximo Video:** El código en el controlador está creciendo. Es hora de organizarlo profesionalmente separando la lógica en capas: **Controller, Service y Repository**.
