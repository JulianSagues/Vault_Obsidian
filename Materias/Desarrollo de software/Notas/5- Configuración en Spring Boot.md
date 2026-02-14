---
Parent item:
  - "[[Materias/Desarrollo de software/Fundamentos de Spring Boot\\|Fundamentos de Spring Boot]]"
---
### 🎯 El Problema: "Hardcodear" Valores

![[Assets/image 69.png|image 69.png]]

- Poner valores fijos (como URLs de bases de datos, puertos o credenciales) directamente en el código es una mala práctica.

- **Problema:** Obliga a recompilar toda la aplicación por cada simple cambio (ej. al pasar de un entorno de desarrollo a uno de producción).

### 💡 La Solución: Configuración Externa

Spring Boot soluciona esto centralizando toda la configuración en archivos específicos, separados del código. Los dos formatos principales son:

### 1. `application.properties`

![[Assets/image 1 43.png|image 1 43.png]]

- **Formato:** Es el tradicional de Java. Usa una sintaxis simple de `clave=valor`.

- **Ejemplo:**Properties
    
    `server.port=8090 spring.application.name=demo-config`
    

### 2. `application.yml` (o `.yaml`)

![[Assets/image 2 41.png|image 2 41.png]]

- **Formato:** Es más moderno y legible. Utiliza **indentación** para crear una estructura jerárquica.

- Es ideal para configuraciones complejas o anidadas.

- **Ejemplo:**YAML
    
    `server: port: 8090 spring: application: name: demo-config`
    

> Nota: Ambos formatos logran exactamente lo mismo, es solo una preferencia de sintaxis. Si ambos archivos existen, .yml puede tener precedencia.

![[Assets/image 3 35.png|image 3 35.png]]

---

### 💉 Cómo Inyectar Valores de Configuración en el Código

Una vez definidos los valores en esos archivos, hay dos formas principales de usarlos en las clases de Spring (como Controladores o Servicios):

### 1. Con `@Value` (Para valores individuales)

![[Assets/image 4 28.png|image 4 28.png]]

- **Qué hace:** Inyecta un valor puntual de una propiedad.

- **Sintaxis:** Se usa la sintaxis de _placeholder_ (`${...}`).

- **Ejemplo:**Java
    
    `@Value("${spring.application.name}") private String applicationName; @Value("${server.port}") private int serverPort;`
    

### 2. Con `@ConfigurationProperties` (La mejor práctica para grupos)

![[Assets/image 5 20.png|image 5 20.png]]

- **Qué hace:** Mapea un grupo completo de propiedades (un prefijo) a una clase Java (un POJO).

- **Por qué es mejor:** Es más ordenado, mantenible, seguro (type-safe) y los IDEs ofrecen autocompletado y validación.

- **Ejemplo:**
    
    - **En** `**application.yml**`**:**YAML
        
        `app: info: name: MiApp version: 1.0.0`
        
    
    - **En una clase Java:**Java
        
        `@Component @ConfigurationProperties(prefix = "app.info") public class AppInfoProperties { private String name; private String version; // Getters y Setters necesarios }`
        
    
    - **En el Controlador (se inyecta la clase entera):**Java
        
        `private final AppInfoProperties appInfo; // Inyección por constructor (recomendado) public ConfigController(AppInfoProperties appInfo) { this.appInfo = appInfo; // Ahora se puede usar appInfo.getName() }`
        
    

---

### 🌍 Manejo de Entornos con Perfiles

![[Assets/image 6 18.png|image 6 18.png]]

Los **Perfiles** son la característica clave para manejar distintos entornos. Permiten tener configuraciones separadas para desarrollo (`dev`), pruebas (`test`) y producción (`prod`).

- **Cómo funcionan:** Se crean archivos de configuración específicos para cada perfil. Spring Boot cargará el archivo base (`application.yml`) y luego "sobrescribirá" los valores con los del perfil activo.
    
    - `application-dev.yml` (Ej. usa puerto 8081 y una base de datos en memoria H2).
    
    - `application-prod.yml` (Ej. usa puerto 9000 y una base de datos real).
    

- **Cómo activar un perfil:**
    
    ![[Assets/image 7 16.png|image 7 16.png]]
    

- Se define en el archivo principal `application.yml` (o `.properties`).

- **Ejemplo:**YAML
    
    `spring: profiles: active: dev`
    

- Al correr la aplicación con este perfil, se cargará `application.yml` y luego `application-dev.yml`. En el video, la app arranca en el puerto `8081` (de `dev`) en lugar del `9000` (de `prod`).

---

### ✅ Resumen y Próximos Pasos

- Se aprendió a usar `application.properties` y `application.yml` para externalizar la configuración.

- Se vieron las dos formas de inyectar valores: `@Value` (simple) y `@ConfigurationProperties` (robusto).

- Se entendió el concepto de **Perfiles** para manejar configuraciones de distintos entornos.

- **Próximo Video:** Se profundizará en la **Autoconfiguración**, los **Starters**, **DevTools** y la configuración de **Logs**.