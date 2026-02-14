---
notion-id: 2a5ac26b-dee7-8058-8ff2-f4eb259c0f56
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 2a5ac26b-dee7-80da-9597-ebc120e56de4
Blocking: []
Categoria: ""
---
### 🛠️ ¿Qué es Spring Initializr?

![[image 18.png]]

- Es una **herramienta web oficial** (disponible en `start.spring.io`) que genera la estructura inicial de un proyecto Spring Boot.
- Evita la necesidad de configurar todo manualmente.
- Permite seleccionar:
    - El gestor de dependencias (Maven o Gradle).
    - El lenguaje (Java, Kotlin, etc.).
    - La versión de Spring Boot.
    - La metadata del proyecto (Group, Artifact).
    - Los "starters" (dependencias) iniciales.

---

### 👣 Paso a Paso: Creación del Proyecto

![[image 19.png]]

El video sigue estos pasos para generar la aplicación:

1. **Ir a **`**start.spring.io**`.
2. **Configurar la Metadata:**
    - **Project:** Gradle (la elección del video).
    - **Language:** Java.
    - **Spring Boot:** La última versión estable (no "snapshot").
    - **Group:** Identificador de la organización (ej. `com.ejemplo`).
    - **Artifact:** Nombre de la aplicación (ej. `mi-primer-springboot`).
    - **Packaging:** JAR (lo más común en Spring Boot).
    - **Java:** Versión 17 (recomendada para Spring Boot 3).
3. **Añadir Dependencias (Starters):**
    - **Spring Web:** Esencial para crear aplicaciones web y APIs. Incluye automáticamente el servidor **Tomcat embebido** y Spring MVC.
    - **Spring Boot DevTools:** Una dependencia opcional muy útil para desarrollo, ya que permite "hot reload" (recarga automática de cambios).
4. **Generar y Abrir:**
    - Se hace clic en "Generate" para descargar un archivo `.zip`.
    - Se descomprime el archivo.
    - Se abre la carpeta resultante con el IDE. El IDE (IntelliJ, en este caso) se encarga de "buildear" el proyecto y descargar las dependencias (toma unos segundos).

---

### 📂 Estructura del Proyecto Generado

![[image 20.png]]

El video explica la estructura de carpetas principal:

- `src/main/java/{nombre-del-paquete}`: Contiene todo el código fuente de Java.
    - Aquí se encuentra la **clase principal** (ej. `MiPrimerSpringbootApplication.java`).
- `src/main/resources`: Contiene archivos de configuración.
    - `application.properties`: Archivo clave para configurar la aplicación (puerto, base de datos, etc.).
- `src/test/java`: Carpeta para las pruebas unitarias.
- `build.gradle` (o `pom.xml` si se usó Maven): Archivo que gestiona todas las dependencias del proyecto (como los starters que se agregaron).

---

### ❤️ El Corazón de la Aplicación: @SpringBootApplication

![[image 21.png]]

La clase principal (la que tiene el método `main`) es lo más importante al arrancar.

- Esta clase tiene la anotación `@SpringBootApplication`.
- Esta única anotación es un "combo" que en realidad combina otras tres anotaciones esenciales:
    1. `**@Configuration**`**:** Indica que la clase puede contener configuraciones de Spring (definición de Beans).
    2. `**@EnableAutoConfiguration**`**:** Le dice a Spring Boot que configure automáticamente la aplicación basándose en las dependencias (starters) que encontró.
    3. `**@ComponentScan**`**:** Le dice a Spring que busque automáticamente otros componentes (como Controladores, Servicios, etc.) en el mismo paquete y los registre.

---

### 🚀 Ejecutando la Aplicación (La Prueba)

5. **Ejecución:** Se corre el método `main` de la clase principal desde el IDE.
6. **Consola:** Se debe ver el "banner" de Spring y los logs de inicio.
7. **Confirmación:** El mensaje clave en la consola es: **"Tomcat started on port(s): 8080"**. Esto confirma que el servidor web está corriendo.
8. **Prueba en Navegador:**
    - Al abrir `localhost:8080` en el navegador, se muestra un **error 404 (Whitelabel Error Page)**.
    - **¡Esto es normal y esperado!** Significa que el servidor funciona, pero como todavía no se ha creado ningún *endpoint* (ninguna URL), no hay nada que mostrar.

---

### ✅ Conclusión y Próximos Pasos

- **Logro:** Se aprendió a usar Spring Initializer, se revisó la estructura base del proyecto y se confirmó que la aplicación arranca correctamente.
- **Próximo Video:** Se profundizará en qué pasa "detrás de escena" al arrancar, explorando el **Application Context**, el concepto de **Beans** y la **Inyección de Dependencias**.

![[image 22.png]]
