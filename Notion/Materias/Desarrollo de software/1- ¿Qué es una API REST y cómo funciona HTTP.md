---
base: "[[Notion/Materias/Desarrollo de software/Desarrollo de software.base]]"
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Desarrollo de software/API REST SPRING BOOT|API REST SPRING BOOT]]"
Blocking: []
Categoria: ""
---
**🎯 ¿Por qué necesitamos APIs?**

![[image 393.png]]


Hoy en día, ninguna aplicación trabaja sola. Un frontend (como React) necesita datos de un backend; un e-commerce se compone de microservicios (pagos, usuarios, envíos) que deben comunicarse.
**REST** actúa como el **"idioma común"** o el conjunto de reglas predecibles que permite que todos estos sistemas (clientes y servidores) hablen entre sí de manera clara y estandarizada, evitando un caos de integración.
**
🚀 Conceptos Fundamentales: API y REST**

![[image 394.png]]

**
1. ¿Qué es una API?**

• **API** (Application Programming Interface - Interfaz de Programación de Aplicaciones).
• Es un conjunto de reglas que define cómo dos programas pueden hablar entre sí.
**
2. ¿Qué es REST?**

• **REST** (Representational State Transfer - Transferencia de Estado Representacional).
• **No es un framework ni una librería**, es un **estilo arquitectónico**: un conjunto de principios o reglas para diseñar APIs web.
• **El concepto clave:** En REST, todo se organiza alrededor de **"Recursos"** (un recurso puede ser un usuario, un producto, una orden, etc.).
• Cada recurso se identifica con una **URL única**:
    ◦ `/users` → Representa la *colección* de todos los usuarios.
    ◦ `/users/123` → Representa a un *usuario específico* (con ID 123).
**
🏛️ Principios Clave de REST**


![[image 395.png]]


Para que una API sea considerada "RESTfull", debe seguir varios principios. Los cuatro más importantes son:
1. **Cliente-Servidor:** El cliente (frontend, app móvil) pide información y el servidor (backend) responde. Las responsabilidades están separadas.
2. **Stateless (Sin Estado):** Cada petición es independiente. El servidor no "recuerda" peticiones anteriores del mismo cliente. Esto hace que la API sea mucho más fácil de escalar.
3. **Interfaz Uniforme:** Se deben usar los métodos estándar de HTTP (GET, POST, etc.) siempre de la misma forma. No se deben inventar métodos (ej. `/crearUsuario`).
4. **Recursos Identificables:** Cada "cosa" (recurso) tiene su propia URL única.
**
⚙️ ¿Cómo operamos? Los Métodos HTTP (Verbos)**


![[image 396.png]]


REST reutiliza los métodos estándar del protocolo HTTP para definir qué acción queremos realizar sobre un recurso. Los más comunes son:**MétodoAcciónEjemplo de URLDescripciónGETLeer**`GET /users/123`Obtiene la información del usuario con ID 123.**POSTCrear**`POST /users`Crea un nuevo usuario (los datos van en el cuerpo).**PUTReemplazar**`PUT /users/123`Reemplaza *completamente* el usuario con ID 123.**DELETEBorrar**`DELETE /users/123`Elimina el usuario con ID 123.**Clave:** Una API RESTful usa `POST /users` para crear. Una API que no sigue REST podría usar algo como `POST /createNewUser`, lo cual no es estándar y genera confusión.
**
📬 ¿Qué recibimos? Códigos de Estado HTTP**


![[image 397.png]]


Cada respuesta del servidor incluye un **código numérico (Status Code)** que nos dice qué pasó. Es fundamental saber leerlos:

![[image 398.png]]


• **Respuestas **`**2xx**`** (Éxito):**
    ◦ `**200 OK**`: Todo salió bien (la respuesta a un `GET`).
    ◦ `**201 Created**`: El recurso se creó con éxito (la respuesta a un `POST`).
• **Respuestas **`**4xx**`** (Error del Cliente):**
    ◦ `**400 Bad Request**`: El cliente mandó algo mal (ej. un JSON mal formado).
    ◦ `**404 Not Found**`: El recurso que se pidió no existe (ej. `GET /users/9999`).
• **Respuestas **`**5xx**`** (Error del Servidor):**
    ◦ `**500 Internal Server Error**`: Algo falló *dentro* del servidor (un bug en nuestro backend).
**
📦 El Formato de Datos: JSON**


![[image 399.png]]


**JSON** (JavaScript Object Notation) es el formato estándar de facto para intercambiar datos en las APIs REST.
• **¿Por qué?**
    1. Es **liviano** y viaja rápido por la red.
    2. Es **fácil de leer** para los humanos.
    3. Es nativo de JavaScript y tiene librerías en todos los lenguajes (Java, Python, etc.).
**
🛠️ Herramienta Práctica: Postman**


![[image 400.png]]


• **¿Qué es?** Es una herramienta (una "navaja suiza") indispensable para probar APIs.
• Permite enviar peticiones HTTP (`GET`, `POST`, `PUT`, `DELETE`) a cualquier URL, ver la respuesta del servidor (el JSON) y el código de estado (el `200`, `404`, etc.).
• **Demo del Video:** El video muestra cómo instalar Postman y hacer una primera prueba exitosa usando una API pública (la de Rick and Morty) con un `GET` a un personaje.

![[image 401.png]]


**
✅ Conclusión y Próximos Pasos**

• **Resumen:** REST es un estilo de arquitectura, basado en Recursos (URLs) y que usa HTTP (Verbos) para definir acciones, Códigos de Estado para respuestas y JSON para los datos.
• **Próximo Video:** Se creará el primer *endpoint* REST (`@RestController`) en Spring Boot y se probará localmente usando Postman.
