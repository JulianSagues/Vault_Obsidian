---
Parent item:
  - "[[Materias/Desarrollo de software/Notas/Resumen Videos\\|Resumen Videos]]"
---
Gracias por compartir el texto completo, Julián. Acá tenés la explicación ordenada y profesional para Obsidian, sobre el concepto de **Fetch Type** en JPA, con jerarquía clara, estilo técnico y lista para copiar:

⚡️ **Fetch Type en JPA: EAGER vs LAZY**

🧠 **¿Qué es Fetch Type?**

Define **cuándo** y **cómo** se cargan las relaciones entre entidades desde la base de datos. No afecta la persistencia, sino la **carga de datos al consultar**.

🔁 **Tipos de Fetch**

![[Assets/image1 13.png|image1 13.png]]

|**Tipo**|**Comportamiento**|**Ventajas**|**Riesgos**|
|---|---|---|---|
|EAGER|Carga inmediata en la misma consulta|Simple, sin sorpresas|Puede traer datos innecesarios y afectar el rendimiento|
|LAZY|Carga bajo demanda cuando se accede|Eficiente,  <br>  <br>evita  <br>  <br>sobrecarga|Puede fallar fuera del contexto de persistencia  <br>  <br>(LazyInitializationException)|

![[Assets/image2 13.png|image2 13.png]]

![[Assets/image3 19.png|image3 19.png]]

🧪 **Ejemplo: Persona y Domicilio (OneToOne)**

![[Assets/image10 12.png|image10 12.png]]

![[Assets/image11 12.png|image11 12.png]]

![[Assets/image4 19.png|image4 19.png]]

![[Assets/image5 15.png|image5 15.png]]

Por defecto, JPA usa EAGER en relaciones @OneToOne

![[Assets/image6 17.png|image6 17.png]]

Si se consulta una Persona , también se carga su Domicilio en la misma consulta

![[Assets/image7 16.png|image7 16.png]]

Si se cambia a LAZY , se hace una segunda consulta solo cuando se accede al domicilio

📌 Esto se puede observar en el SQL generado por JPA:

EAGER : un solo SELECT con JOIN

LAZY : dos SELECT , uno para Persona , otro para Domicilio

🧪 **Ejemplo: Persona y Cursos (ManyToMany)**

![[Assets/image6 17.png|image6 17.png]]

Por defecto, JPA usa LAZY en relaciones @ManyToMany

![[Assets/image8 18.png|image8 18.png]]

Al consultar una Persona , no se cargan los cursos hasta que se accede a la lista

![[Assets/image6 17.png|image6 17.png]]

Si se fuerza EAGER , se puede caer en el problema clásico de

**N+1 consultas**

:

![[Assets/image9 13.png|image9 13.png]]

Una consulta para todas las personas

![[Assets/image6 17.png|image6 17.png]]

Una consulta adicional por cada persona para traer sus cursos

📌 Esto puede afectar gravemente el rendimiento en colecciones grandes

![[Assets/image12 12.png|image12 12.png]]

![[Assets/image13 12.png|image13 12.png]]

![[Assets/image14 15.png|image14 15.png]]

![[Assets/image15 11.png|image15 11.png]]

![[Assets/image16 12.png|image16 12.png]]

![[Assets/image17 7.png|image17 7.png]]

![[Assets/image18 7.png|image18 7.png]]

![[Assets/image19 16.png|image19 16.png]]

![[Assets/image20 14.png|image20 14.png]]

![[Assets/image21 19.png|image21 19.png]]

![[Assets/image22 8.png|image22 8.png]]

![[Assets/image23 5.png|image23 5.png]]

![[Assets/image24 12.png|image24 12.png]]

![[Assets/image25 5.png|image25 5.png]]

![[Assets/image26 6.png|image26 6.png]]

![[Assets/image27 5.png|image27 5.png]]

![[Assets/image28 5.png|image28 5.png]]

![[Assets/image29 5.png|image29 5.png]]

![[Assets/image30 5.png|image30 5.png]]

![[Assets/image31 5.png|image31 5.png]]

✅ **Buenas prácticas**

![[Assets/image7 16.png|image7 16.png]]

Usar LAZY por defecto en colecciones ( @OneToMany , @ManyToMany )

![[Assets/image9 13.png|image9 13.png]]

Usar EAGER solo en relaciones pequeñas ( @OneToOne ) y cuando

**siempre**

se necesiten los datos

![[Assets/image7 16.png|image7 16.png]]

Para casos puntuales, usar

**consultas con**

JOIN FETCH en lugar de cambiar el fetch global

![[Assets/image5 15.png|image5 15.png]]

Revisar el SQL generado por JPA para entender el comportamiento real

🧾 **Conclusión**

![[Assets/image33 4.png|image33 4.png]]

![[Assets/image34 4.png|image34 4.png]]

![[Assets/image35 4.png|image35 4.png]]

![[Assets/image36 4.png|image36 4.png]]

![[Assets/image37 4.png|image37 4.png]]

![[Assets/image38 4.png|image38 4.png]]

![[Assets/image39 4.png|image39 4.png]]

![[Assets/image40 4.png|image40 4.png]]

![[Assets/image41 5.png|image41 5.png]]

![[Assets/image42 4.png|image42 4.png]]

![[Assets/image43 4.png|image43 4.png]]

![[Assets/image44 4.png|image44 4.png]]

![[Assets/image45 4.png|image45 4.png]]

![[Assets/image46 4.png|image46 4.png]]

![[Assets/image47 2.png|image47 2.png]]

![[Assets/image48 2.png|image48 2.png]]

![[Assets/image49 2.png|image49 2.png]]

![[Assets/image50 2.png|image50 2.png]]

![[Assets/image51 2.png|image51 2.png]]

![[Assets/image52 2.png|image52 2.png]]

![[Assets/image53 2.png|image53 2.png]]

![[Assets/image54 2.png|image54 2.png]]

EAGER es cómodo pero puede ser costoso

LAZY es eficiente pero requiere contexto abierto

![[Assets/image8 18.png|image8 18.png]]

La elección depende del caso de uso y del diseño de la aplicación

![[Assets/image32 4.png|image32 4.png]]

Entender fetch type permite escribir código más profesional y optimizado