---
notion-id: 29cac26b-dee7-80e0-a377-fa031013e759
base: "[[Diseño de sistemas.base]]"
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29cac26b-dee7-80ba-91e6-d4b53855a0ec
Blocking: []
Categoria: ""
---
GOF = Gang Of Four

# Singleton

![[image 124.png]]

# DTO (Data Transfer Object)

![[image 125.png]]

# Estrategia

![[image 126.png]]

# Adaptador

![[image 127.png]]

# Factoria

![[image 128.png]]

Adaptador (Adapter)

El patrón Adaptador (GoF) se utiliza para **convertir la interfaz original de un componente en otra interfaz** mediante un objeto adaptador intermedio, resolviendo interfaces incompatibles o proporcionando una interfaz estable para componentes similares.

Patrones y Principios Relacionados:

- **Polimorfismo:** La aplicación del Adaptador es una especialización de componentes GRASP básicos y utiliza Polimorfismo. Adaptador es uno de los patrones de diseño GoF que depende del Polimorfismo.
- **Indirección:** El adaptador actúa como un nivel de indirección para desacoplar el sistema de las APIs externas, lo que soporta el Bajo Acoplamiento.
- **Variaciones Protegidas:** El uso de Adaptadores proporciona **Variaciones Protegidas** frente a cambios en las interfaces externas o paquetes de terceros.
- **Fabricación Pura (Pure Fabrication):** El Adaptador es un ejemplo de Fabricación Pura, una clase artificial creada para soportar alta cohesión y bajo acoplamiento, ya que no representa un concepto del dominio del problema.
- **Fachada (Facade):** Un adaptador de recursos que oculta un sistema externo también puede considerarse un objeto Fachada, aunque el nombre "adaptador" se enfatiza cuando facilita la adaptación a diversas interfaces externas.
- **Bajo Acoplamiento (Low Coupling):** La Indirección proporcionada por el Adaptador ayuda a disminuir el acoplamiento entre componentes.

Factoría (Factory)

El patrón Factoría (GoF) es una **Fabricación Pura** que se utiliza para manejar la creación de objetos, especialmente cuando existe lógica de creación compleja o se desea **separar las responsabilidades de creación** para mejorar la cohesión.

Patrones y Principios Relacionados:

- **Fabricación Pura (Pure Fabrication):** Una Factoría es explícitamente definida como un objeto **Fabricación Pura**.
- **Creador (Creator) (GRASP):** La Factoría es una **solución alternativa frecuente** al patrón Creador, especialmente cuando la creación requiere una complejidad significativa o consideraciones especiales como instancias recicladas.
- **Singleton:** Las Factorías se acceden a menudo con el patrón **Singleton** para asegurar un punto de acceso único y global a la factoría.
- **Variaciones Protegidas (Protected Variations):** Las factorías pueden diseñarse para conseguir Variaciones Protegidas, por ejemplo, leyendo la clase de implementación a crear desde una fuente externa (diseño dirigido por datos).
- **Estrategia (Strategy):** Las Factorías se utilizan para crear instancias de objetos Estrategia (ej., `FactoriaDeEstrategiasFijarPrecios`), especialmente porque las políticas de fijación de precios pueden cambiar dinámicamente.
- **Factoría Abstracta (Abstract Factory) (GoF):** Es una variación de Factoría utilizada para crear familias de clases relacionadas que implementan una interfaz común, como los controladores de dispositivos JavaPOS.

Singleton

El patrón Singleton (GoF) asegura que **exista exactamente una instancia de una clase** y proporciona un único punto de acceso global a ella.

Patrones y Principios Relacionados:

- **Factoría (Factory):** El patrón Singleton se utiliza a menudo para acceder a objetos **Factoría**.
- **Fachada (Facade):** Singleton también se utiliza comúnmente para acceder a objetos **Fachada**. Por ejemplo, se accede a la `FachadaMotorReglasPDV` normalmente mediante el Singleton.
- **Registro Centralizado de Errores:** Se propone utilizar un objeto central de registro de errores con acceso mediante el patrón Singleton.

Estrategia (Strategy)

El patrón Estrategia (GoF) se utiliza para diseñar **diversos algoritmos o políticas relacionadas** al definir cada una en una clase independiente con una interfaz común, permitiendo que estos algoritmos puedan cambiar.

Patrones y Principios Relacionados:

- **Polimorfismo:** Estrategia se fundamenta en el **Polimorfismo** y las interfaces para permitir algoritmos conectables. Puesto que el comportamiento varía según la estrategia, se utilizan operaciones polimórficas (como `getTotal`).
- **Variaciones Protegidas (Protected Variations):** Estrategia proporciona Variaciones Protegidas con respecto a algoritmos que cambian.
- **Fabricación Pura (Pure Fabrication):** El patrón Estrategia es un ejemplo de Fabricación Pura.
- **Factoría (Factory):** Las Estrategias son creadas normalmente mediante una **Factoría** (ej., `FactoriaDeEstrategiasFijarPrecios`).
- **Composite (GoF):** El patrón Composite se utiliza a menudo junto con Estrategia para tratar una estructura de múltiples estrategias de la misma manera que una sola estrategia (polimórficamente), como cuando se aplican múltiples descuentos a una venta.
- **Estilo de diseño:** Singleton se clasifica como un patrón de **Estilo** que resuelve soluciones de diseño de bajo nivel orientadas a la implementación o al lenguaje.