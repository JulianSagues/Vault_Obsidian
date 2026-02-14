---
Parent item:
  - "[[Materias/Desarrollo de software/JPA\\|JPA]]"
---
Claro. Este es un concepto fundamental en JPA (Java Persistence API) para resolver el problema de cómo almacenar jerarquías de herencia de la Programación Orientada a Objetos (POO) en bases de datos relacionales (que no tienen un concepto nativo de herencia).

JPA ofrece principalmente tres estrategias para manejar esto, que se configuran usando la anotación `@Inheritance` en la clase base (o superclase) de la jerarquía.

Aquí tienes un desglose de cada una:

---

### 1. 🗺️ Tabla Única (Single Table)

Esta es la **estrategia por defecto** en JPA si no especificas ninguna.

- **Anotación:** `@Inheritance(strategy = InheritanceType.SINGLE_TABLE)`

- **Cómo funciona:** Se crea **una sola tabla** en la base de datos para _todas_ las clases de la jerarquía (la clase base y todas sus subclases).

- **Columna Discriminadora:** Para saber a qué clase pertenece cada fila, JPA añade automáticamente una columna especial llamada **"columna discriminadora"** (por defecto `DTYPE`). Esta columna almacena un valor (como el nombre de la clase) que identifica el tipo de objeto.

- **Ejemplo:**
    
    - Clases: `Vehiculo` (base), `Coche` (subclase), `Moto` (subclase).
    
    - Tabla: `VEHICULO` (Columnas: `ID`, `DTYPE`, `color`, `matricula_coche`, `cilindrada_moto`).
    

- **Ventajas:**
    
    - **Rendimiento:** Es la estrategia más rápida. Las consultas polimórficas (buscar todos los "Vehiculos") son muy eficientes porque solo consultan una tabla. No se necesitan `JOINs`.
    

- **Desventajas:**
    
    - **Desperdicio de espacio y Nulos:** La tabla tendrá columnas para _todas_ las propiedades de _todas_ las subclases. Esto significa que las filas de `Coche` tendrán `NULL` en la columna `cilindrada_moto`, y las filas de `Moto` tendrán `NULL` en `matricula_coche`.
    
    - **Integridad de datos:** No puedes usar restricciones a nivel de base de datos (como `NOT NULL`) en campos que solo pertenecen a una subclase (porque necesitarían ser `NULL` para las otras).
    

---

### 2. 🔗 Unión de Tablas (Joined)

Esta estrategia es a menudo considerada la más "limpia" desde la perspectiva de la base de datos relacional.

- **Anotación:** `@Inheritance(strategy = InheritanceType.JOINED)`

- **Cómo funciona:**
    
    1. Se crea una tabla para la **clase base** con sus campos comunes.
    
    1. Se crea una **tabla separada para cada subclase** que contiene _solo_ los campos específicos de esa subclase.
    
    1. La clave primaria (PK) de la tabla de la clase base se usa también como clave primaria (y clave foránea - FK) en las tablas de las subclases, relacionándolas.
    

- **Ejemplo:**
    
    - Tabla `VEHICULO`: `ID` (PK), `color`.
    
    - Tabla `COCHE`: `ID` (PK, FK a VEHICULO), `matricula_coche`.
    
    - Tabla `MOTO`: `ID` (PK, FK a VEHICULO), `cilindrada_moto`.
    

- **Ventajas:**
    
    - **Modelo de datos normalizado:** Es el modelo de base de datos más limpio. No hay `NULL`s innecesarios.
    
    - **Integridad de datos:** Puedes usar restricciones `NOT NULL` en los campos de las subclases sin problema.
    

- **Desventajas:**
    
    - **Rendimiento:** Es la estrategia que puede ser más lenta. Para obtener un objeto completo de una subclase (ej. un `Coche`), JPA _siempre_ debe hacer un `JOIN` entre la tabla `VEHICULO` y la tabla `COCHE`. Las consultas polimórficas pueden requerir `JOIN`s complejos.
    

---

### 3. 📑 Tabla por Clase (Table Per Class)

Esta estrategia es la menos común y, a menudo, la menos recomendada.

- **Anotación:** `@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)`

- **Cómo funciona:** Se crea una tabla separada para **cada clase concreta** (no abstracta) de la jerarquía. Cada una de estas tablas contiene _todas_ las columnas de esa clase, incluyendo las heredadas.

- **Ejemplo:**
    
    - Tabla `COCHE`: `ID`, `color` (heredado), `matricula_coche`.
    
    - Tabla `MOTO`: `ID`, `color` (heredado), `cilindrada_moto`.
    
    - (Si `Vehiculo` es abstracta, no tendrá tabla. Si es concreta, tendrá su propia tabla solo con `ID` y `color`).
    

- **Ventajas:**
    
    - Consultar una clase concreta (ej. "todos los Coches") es simple y rápido (consulta a una sola tabla).
    

- **Desventajas:**
    
    - **Pésimo rendimiento polimórfico:** Una consulta polimórfica (buscar todos los "Vehiculos") es **muy costosa**. JPA debe ejecutar una consulta `UNION` a través de _todas_ las tablas de las subclases (`SELECT ... FROM COCHE UNION SELECT ... FROM MOTO`).
    
    - **Mantenimiento:** Si añades o cambias un campo en la clase base (`Vehiculo`), debes actualizar la estructura de _todas_ las tablas de las subclases.
    
    - **Relaciones:** Es complicado establecer relaciones de clave foránea (FK) con la clase base `Vehiculo`, ya que los datos están repartidos en múltiples tablas.
    

---

### Resumen Comparativo

|   |   |   |   |   |
|---|---|---|---|---|
|Estrategia|Tablas Creadas|Consultas Polimórficas|Manejo de Nulos|Integridad de Datos|
|**Single Table**|1 tabla total|Muy Rápido (1 tabla)|Malo (muchos `NULL`s)|Débil|
|**Joined**|1 por clase (relacionadas)|Lento (`JOIN`s)|Excelente (sin `NULL`s)|Fuerte|
|**Table Per Class**|1 por clase concreta (separadas)|Muy Lento (`UNION`s)|Excelente (sin `NULL`s)|Débil (en la superclase)|

Generalmente, la elección se reduce a:

- Usa **Single Table** (la defecto) si tu jerarquía es simple y el rendimiento es tu prioridad principal.

- Usa **Joined** si necesitas un modelo de datos normalizado, la integridad de los datos (`NOT NULL`) es crucial y puedes aceptar el coste de los `JOIN`s.