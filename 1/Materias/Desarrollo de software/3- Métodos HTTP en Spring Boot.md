---
Parent item:
  - "[[Materias/Desarrollo de software/API REST SPRING BOOT\\|API REST SPRING BOOT]]"
---
### 🔁 Repaso: Los 4 Métodos HTTP Principales (CRUD)

El video repasa la responsabilidad de cada método, que son la base de cualquier API REST:

![[Assets/image 457.png|image 457.png]]

|   |   |   |   |
|---|---|---|---|
|Método|Operación (CRUD)|Anotación en Spring Boot|Descripción|
|**GET**|**Read** (Leer)|`@GetMapping`|Consulta datos. Es seguro y no cambia nada en el servidor.|
|**POST**|**Create** (Crear)|`@PostMapping`|Envía datos para crear un nuevo recurso.|
|**PUT**|**Update** (Actualizar)|`@PutMapping`|Reemplaza _completamente_ un recurso existente.|
|**DELETE**|**Delete** (Borrar)|`@DeleteMapping`|Elimina un recurso existente de forma permanente.|

Exportar a Hojas de cálculo

---

### 💻 Implementación en Spring Boot: Anotaciones

Spring Boot simplifica la implementación con anotaciones específicas para cada método (todas son atajos de la anotación `@RequestMapping` general):

![[Assets/image 1 49.png|image 1 49.png]]

- `@GetMapping`

- `@PostMapping`

- `@PutMapping`

- `@DeleteMapping`

Un mismo controlador puede tener métodos para las cuatro operaciones, y Spring se encarga de dirigir la petición al método correcto según el verbo HTTP utilizado.

![[Assets/image 2 46.png|image 2 46.png]]

### El Concepto de "Path Variable" (Variables de Ruta)

Un punto clave es que `PUT` y `DELETE` (y a veces `GET`) necesitan saber _sobre qué recurso específico_ actuar. Esto se logra pasando un identificador (como un ID) directamente en la URL.

- **Ejemplo de URL:** `/api/ejemplo/{id}`

- En el código, se captura ese `{id}` para saber a qué recurso actualizar o eliminar.

---

### 🚀 Pruebas en Postman (La Demostración)

  

En el video, se crea un controlador con cuatro _endpoints_ para probar cada método.

**Importante:** La URL base es la misma (`/api/ejemplo`), pero la API responde de forma diferente según el método HTTP seleccionado en Postman.

1. **Prueba GET**
    
    - **Acción:** `GET`
    
    - **URL:** `http://localhost:8080/api/ejemplo`
    
    - **Resultado:** Devuelve un JSON (ej. `{"mensaje": "Respuesta GET"}`) y un **Status 200 OK**.
    

1. **Prueba POST**
    
    - **Acción:** `POST`
    
    - **URL:** `http://localhost:8080/api/ejemplo`
    
    - **Resultado:** Devuelve un JSON (ej. `{"mensaje": "Recurso creado"}`) y un **Status 200 OK**.
    
    - _(Nota: En este ejemplo básico aún no se envía un "body" o cuerpo con datos, eso se verá en el próximo video)._
    

1. **Prueba PUT (con Path Variable)**
    
    - **Acción:** `PUT`
    
    - **URL:** `http://localhost:8080/api/ejemplo/5` (El `5` es el ID).
    
    - **Resultado:** Devuelve un JSON (ej. `{"mensaje": "Recurso 5 actualizado"}`) y un **Status 200 OK**.
    

1. **Prueba DELETE (con Path Variable)**
    
    - **Acción:** `DELETE`
    
    - **URL:** `http://localhost:8080/api/ejemplo/5` (El `5` es el ID).
    
    - **Resultado:** Devuelve un JSON (ej. `{"mensaje": "Recurso 5 eliminado"}`) y un **Status 200 OK**.
    

---

### ⚠️ Errores Comunes

- **Probar con el método incorrecto:** Dejar el método en `GET` (que es el defecto de Postman) cuando se quiere probar `POST`, `PUT` o `DELETE`.

- **Olvidar el ID en la URL:** Intentar llamar a `PUT` o `DELETE` sin el ID (ej. `/api/ejemplo` en lugar de `/api/ejemplo/5`). Esto resultará en un **Error 404 Not Found** porque la ruta no coincide.

- **Probar con la aplicación apagada:** Postman dará un error de "Could not send request" si el servidor de Spring Boot no está corriendo.

---

### ✅ Conclusión y Próximos Pasos

- Se aprendió a implementar las cuatro operaciones básicas de una API REST (`GET`, `POST`, `PUT`, `DELETE`) usando las anotaciones correspondientes.

- Se comprobó en Postman cómo la misma URL puede gestionar diferentes acciones según el método HTTP.

- **Próximo Video:** El paso clave que falta: **cómo recibir datos** en los _endpoints_ (Path Variables, Parámetros de Consulta y, lo más importante, el cuerpo o **Request Body** en formato JSON) para que `POST` y `PUT` sean realmente útiles.