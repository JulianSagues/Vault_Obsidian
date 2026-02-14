---
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Fundamentos de Spring Boot|Fundamentos de Spring Boot]]"
Blocking: []
Categoria: ""
---
### 🎯 El Problema Original (Spring Framework Clásico)

![[image.png]]

Antes de Spring Boot, configurar un proyecto con Spring Framework (o Java EE) era un proceso complejo y lento:

- **Configuraciones Eternas:** Requería archivos XML gigantescos y de mantenimiento manual.
- **Gestión de Dependencias:** Era necesario descargar, manejar y compatibilizar versiones de dependencias manualmente.
- **Servidor Externo:** Había que instalar y configurar un servidor de aplicaciones (como Tomcat) por separado.
- **Curva de Aprendizaje:** Exigía entender una gran cantidad de configuraciones antes de poder escribir lógica de negocio, lo que podía tomar días para un simple "hola mundo".


### 🛠️ Spring Framework vs. Spring Boot

### 1. ¿Qué es Spring Framework? (La Base)

![[image 1.png]]

- Es un contenedor de **Inversión de Control (IoC)** y **Inyección de Dependencias (DI)**.
- Provee herramientas para construir aplicaciones empresariales robustas y modulares (gestión de transacciones, programación orientada a aspectos, etc.).
- **El problema:** Su gran flexibilidad también trajo una enorme complejidad de configuración.

![[image 2.png]]

### 2. ¿Qué es Spring Boot? (La Evolución / El Atajo)

![[image 3.png]]

- No es un reemplazo, sino una **evolución de Spring Framework** que se basa en él.
- Llegó en 2014 para eliminar la complejidad de configuración.
- Su objetivo es permitir al desarrollador enfocarse en la **lógica de negocio** y no en la infraestructura.

![[image 4.png]]

### 🚀 Conceptos Clave de Spring Boot

Spring Boot logra esta simplificación gracias a dos conceptos principales:

### 1. Autoconfiguración

![[image 5.png]]

- **¿Qué es?** Spring Boot detecta qué dependencias hay en el proyecto y, basándose en ellas, configura automáticamente los componentes necesarios.
- **Ejemplo:** Si Spring Boot detecta el "starter web", automáticamente configura Tomcat, el `DispatcherServlet` y todo lo necesario para servir *endpoints* web, sin necesidad de configuración manual.

### 2. Starters

![[image 6.png]]

- **¿Qué son?** Son dependencias pre-armadas o "paquetes listos para usar".
- **¿Qué hacen?** No solo agrupan las librerías necesarias (ej. `spring-boot-starter-web`), sino que también **disparan la autoconfiguración** correspondiente.
- **Beneficio:** Ahorran horas de trabajo y aseguran que todas las librerías sean compatibles entre sí.
- **Ejemplos comunes:**
    - `spring-boot-starter-web`: Para crear APIs web.
    - `spring-boot-starter-data-jpa`: Para trabajar con bases de datos.
    - `spring-boot-starter-security`: Para añadir seguridad.

---

### ✅ Beneficios y Conclusión

![[image 7.png]]

El cambio radical de Spring Boot se resume en:

- **Desarrollo Rápido:** El setup pasa de días a minutos.
- **Configuración Mínima:** Provee valores por defecto inteligentes que funcionan "de caja".
- **Mayor Productividad:** El foco vuelve a la lógica de negocio.
- **Deploy Simple:** Gracias al servidor embebido (Tomcat, etc.), la aplicación se puede empaquetar y ejecutar en cualquier lugar.

**Conclusión del video:** Spring Framework es la base, y Spring Boot es la evolución que lo hace simple de usar.

![[image 8.png]]
