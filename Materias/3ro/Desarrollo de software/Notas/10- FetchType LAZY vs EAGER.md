---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
Gracias por compartir el texto completo, Julián. Acá tenés la explicación ordenada y profesional para Obsidian, sobre el concepto de **Fetch Type** en JPA, con jerarquía clara, estilo técnico y lista para copiar:

⚡️ **Fetch Type en JPA: EAGER vs LAZY**

🧠 **¿Qué es Fetch Type?**

Define **cuándo** y **cómo** se cargan las relaciones entre entidades desde la base de datos. No afecta la persistencia, sino la **carga de datos al consultar**.

🔁 **Tipos de Fetch**

![[Assets/image1 4.png|image1 4.png]]

|**Tipo**|**Comportamiento**|**Ventajas**|**Riesgos**|
|---|---|---|---|
|EAGER|Carga inmediata en la misma consulta|Simple, sin sorpresas|Puede traer datos innecesarios y afectar el rendimiento|
|LAZY|Carga bajo demanda cuando se accede|Eficiente,  <br>  <br>evita  <br>  <br>sobrecarga|Puede fallar fuera del contexto de persistencia  <br>  <br>(LazyInitializationException)|

![[Assets/image2 4.png|image2 4.png]]

![[Assets/image3 4.png|image3 4.png]]

🧪 **Ejemplo: Persona y Domicilio (OneToOne)**

![[Assets/image10 4.png|image10 4.png]]

![[Assets/image11 4.png|image11 4.png]]

![[Assets/image4 4.png|image4 4.png]]

![[Assets/image5 4.png|image5 4.png]]

Por defecto, JPA usa EAGER en relaciones @OneToOne

![[Assets/image6 4.png|image6 4.png]]

Si se consulta una Persona , también se carga su Domicilio en la misma consulta

![[Assets/image7 4.png|image7 4.png]]

Si se cambia a LAZY , se hace una segunda consulta solo cuando se accede al domicilio

📌 Esto se puede observar en el SQL generado por JPA:

EAGER : un solo SELECT con JOIN

LAZY : dos SELECT , uno para Persona , otro para Domicilio

🧪 **Ejemplo: Persona y Cursos (ManyToMany)**

![[Assets/image6 4.png|image6 4.png]]

Por defecto, JPA usa LAZY en relaciones @ManyToMany

![[Assets/image8 4.png|image8 4.png]]

Al consultar una Persona , no se cargan los cursos hasta que se accede a la lista

![[Assets/image6 4.png|image6 4.png]]

Si se fuerza EAGER , se puede caer en el problema clásico de

**N+1 consultas**

:

![[Assets/image9 4.png|image9 4.png]]

Una consulta para todas las personas

![[Assets/image6 4.png|image6 4.png]]

Una consulta adicional por cada persona para traer sus cursos

📌 Esto puede afectar gravemente el rendimiento en colecciones grandes

![[Assets/image12 4.png|image12 4.png]]

![[Assets/image13 4.png|image13 4.png]]

![[Assets/image14 4.png|image14 4.png]]

![[Assets/image15 3.png|image15 3.png]]

![[Assets/image16 3.png|image16 3.png]]

![[Assets/image17 3.png|image17 3.png]]

![[Assets/image18 3.png|image18 3.png]]

![[Assets/image19 3.png|image19 3.png]]

![[Assets/image20 3.png|image20 3.png]]

![[Assets/image21 3.png|image21 3.png]]

![[Assets/image22 2.png|image22 2.png]]

![[Assets/image23 2.png|image23 2.png]]

![[Assets/image24 2.png|image24 2.png]]

![[Assets/image25 2.png|image25 2.png]]

![[Assets/image26 2.png|image26 2.png]]

![[Assets/image27 2.png|image27 2.png]]

![[Assets/image28 2.png|image28 2.png]]

![[Assets/image29 2.png|image29 2.png]]

![[Assets/image30 2.png|image30 2.png]]

![[Assets/image31 2.png|image31 2.png]]

✅ **Buenas prácticas**

![[Assets/image7 4.png|image7 4.png]]

Usar LAZY por defecto en colecciones ( @OneToMany , @ManyToMany )

![[Assets/image9 4.png|image9 4.png]]

Usar EAGER solo en relaciones pequeñas ( @OneToOne ) y cuando

**siempre**

se necesiten los datos

![[Assets/image7 4.png|image7 4.png]]

Para casos puntuales, usar

**consultas con**

JOIN FETCH en lugar de cambiar el fetch global

![[Assets/image5 4.png|image5 4.png]]

Revisar el SQL generado por JPA para entender el comportamiento real

🧾 **Conclusión**

![[Assets/image33 2.png|image33 2.png]]

![[Assets/image34 2.png|image34 2.png]]

![[Assets/image35 2.png|image35 2.png]]

![[Assets/image36 2.png|image36 2.png]]

![[Assets/image37 2.png|image37 2.png]]

![[Assets/image38 2.png|image38 2.png]]

![[Assets/image39 2.png|image39 2.png]]

![[Assets/image40 2.png|image40 2.png]]

![[Assets/image41 2.png|image41 2.png]]

![[Assets/image42 2.png|image42 2.png]]

![[Assets/image43 2.png|image43 2.png]]

![[Assets/image44 2.png|image44 2.png]]

![[Assets/image45 2.png|image45 2.png]]

![[Assets/image46 2.png|image46 2.png]]

![[image47.png]]

![[image48.png]]

![[image49.png]]

![[image50.png]]

![[image51.png]]

![[image52.png]]

![[image53.png]]

![[image54.png]]

EAGER es cómodo pero puede ser costoso

LAZY es eficiente pero requiere contexto abierto

![[Assets/image8 4.png|image8 4.png]]

La elección depende del caso de uso y del diseño de la aplicación

![[Assets/image32 2.png|image32 2.png]]

Entender fetch type permite escribir código más profesional y optimizado