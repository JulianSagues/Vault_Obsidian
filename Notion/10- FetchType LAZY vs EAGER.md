---
notion-id: 29bac26b-dee7-8195-b9bd-e05944b95fd9
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
Gracias por compartir el texto completo, Julián. Acá tenés la explicación ordenada y profesional para Obsidian, sobre el concepto de **Fetch Type** en JPA, con jerarquía clara, estilo técnico y lista para copiar:

⚡️ **Fetch Type en JPA: EAGER vs LAZY**

🧠 **¿Qué es Fetch Type?**

Define **cuándo** y **cómo** se cargan las relaciones entre entidades desde la base de datos. No afecta la persistencia, sino la **carga de datos al consultar**.

🔁 **Tipos de Fetch**

![[image1 1.png]]

| **Tipo** | **Comportamiento** | **Ventajas** | **Riesgos** |
| --- | --- | --- | --- |
| EAGER | Carga inmediata en la misma consulta | Simple, sin sorpresas | Puede traer datos innecesarios y afectar el rendimiento |
| LAZY | Carga bajo demanda cuando se accede | Eficiente,<br><br>evita<br><br>sobrecarga | Puede fallar fuera del contexto de persistencia<br><br>(LazyInitializationException) |

![[image2 1.png]]

![[image3 1.png]]

🧪 **Ejemplo: Persona y Domicilio (OneToOne)**

![[image10 1.png]]

![[image11 1.png]]

![[image4 1.png]]

![[image5 1.png]]

Por defecto, JPA usa EAGER en relaciones @OneToOne

![[image6 1.png]]

Si se consulta una Persona , también se carga su Domicilio en la misma consulta

![[image7 1.png]]

Si se cambia a LAZY , se hace una segunda consulta solo cuando se accede al domicilio

📌 Esto se puede observar en el SQL generado por JPA:

EAGER : un solo SELECT con JOIN

LAZY : dos SELECT , uno para Persona , otro para Domicilio

🧪 **Ejemplo: Persona y Cursos (ManyToMany)**

![[image6 2.png]]

Por defecto, JPA usa LAZY en relaciones @ManyToMany

![[image8 1.png]]

Al consultar una Persona , no se cargan los cursos hasta que se accede a la lista

![[image6 3.png]]

Si se fuerza EAGER , se puede caer en el problema clásico de

**N+1 consultas**

:

![[image9 1.png]]

Una consulta para todas las personas

![[image6 4.png]]

Una consulta adicional por cada persona para traer sus cursos

📌 Esto puede afectar gravemente el rendimiento en colecciones grandes

![[image12 1.png]]

![[image13 1.png]]

![[image14 1.png]]

![[image15.png]]

![[image16.png]]

![[image17.png]]

![[image18.png]]

![[image19.png]]

![[image20.png]]

![[image21.png]]

![[image22.png]]

![[image23.png]]

![[image24.png]]

![[image25.png]]

![[image26.png]]

![[image27.png]]

![[image28.png]]

![[image29.png]]

![[image30.png]]

![[image31.png]]

✅ **Buenas prácticas**

![[image7 2.png]]

Usar LAZY por defecto en colecciones ( @OneToMany , @ManyToMany )

![[image9 2.png]]

Usar EAGER solo en relaciones pequeñas ( @OneToOne ) y cuando

**siempre**

se necesiten los datos

![[image7 3.png]]

Para casos puntuales, usar

**consultas con**

JOIN FETCH en lugar de cambiar el fetch global

![[image5 2.png]]

Revisar el SQL generado por JPA para entender el comportamiento real

🧾 **Conclusión**

![[image33.png]]

![[image34.png]]

![[image35.png]]

![[image36.png]]

![[image37.png]]

![[image38.png]]

![[image39.png]]

![[image40.png]]

![[image41.png]]

![[image42.png]]

![[image43.png]]

![[image44.png]]

![[image45.png]]

![[image46.png]]

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

![[image8 2.png]]

La elección depende del caso de uso y del diseño de la aplicación

![[image32.png]]

Entender fetch type permite escribir código más profesional y optimizado