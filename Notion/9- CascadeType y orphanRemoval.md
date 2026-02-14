---
notion-id: 29bac26b-dee7-8193-b3f1-d9cbd9269a0a
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - 29bac26b-dee7-80d2-9ccf-cc05773f4eeb
Blocking: []
Categoria: ""
---
🔄 **Cascade Type y Orphan Removal en JPA**

🧠 **Introducción**

![[image1 9.png]]

Hasta ahora, la persistencia de entidades relacionadas se hacía manualmente.

Esto generaba código repetitivo y propenso a errores.

Con **Cascade Type** y **Orphan Removal**, JPA puede encargarse automáticamente de estas operaciones.

![[image4 15.png]]

![[image5 11.png]]

![[image6 13.png]]

![[image7 12.png]]

![[image8 14.png]]

![[image9 9.png]]

![[image10 8.png]]

![[image11 8.png]]

🔁 **¿Qué es Cascade?**

Permite que las operaciones realizadas sobre una entidad principal se **propaguen** a sus

entidades relacionadas.

📌 **Ejemplo**

![[image2 9.png]]

Si se persiste una Persona , también se persiste automáticamente su Domicilio

![[image3 14.png]]

Ya no es necesario llamar a persist() para cada entidad relacionada

🧩 **Tipos de Cascade**

![[image12 8.png]]

| **Tipo** | **Propagación de…** | **Uso común** |
| --- | --- | --- |
| PERSIST | Guardado | ✅ |
| MERGE | Actualización | ✅ |
| REMOVE | Eliminación | ⚠️ |
| REFRESH | Sincronización desde BD | Opcional |
| DETACH | Desvinculación del contexto | Raro |
| ALL | Todos los anteriores | ⚠️ |

🔸 Es mejor **no usar** CascadeType.ALL **por defecto**.

🔸 Conviene elegir solo los tipos necesarios para cada relación.

🧪 **Ejemplo práctico: Persona y Domicilio**

![[image13 8.png]]

![[image14 8.png]]

Antes: se persistía primero el Domicilio , luego la Persona

![[image3 15.png]]

Ahora: con CascadeType.PERSIST , basta con persistir la Persona

![[image14 9.png]]

Resultado: el Domicilio se guarda automáticamente

📌 El cascade debe colocarse **del lado propietario** de la relación (no en el mappedBy )

🧪 **Ejemplo práctico: Persona y Cursos (ManyToMany Bidireccional)**

![[image17 4.png]]

![[image18 4.png]]

![[image19 13.png]]

![[image20 11.png]]

Persona es el lado propietario (tiene el @JoinTable )

![[image15 5.png]]

Se configura cascade = CascadeType.PERSIST en Persona

![[image14 10.png]]

Al persistir la Persona , también se persisten los Cursos

![[image16 5.png]]

Ya no es necesario persistir cada curso manualmente

🧹 **¿Qué es Orphan Removal?**

![[image21 16.png]]

Permite que una entidad relacionada se **elimine automáticamente** si pierde su vínculo con la entidad principal.

📌 **Ejemplo**

![[image22 5.png]]

Si se elimina el Domicilio de una Persona , se borra automáticamente de la base de datos

![[image15 6.png]]

No hace falta llamar a delete() manualmente

🔸 Se activa con orphanRemoval = true

🔸 Úsalo solo si la entidad dependiente **no tiene sentido por sí sola**

🧪 **Ejemplo práctico: Orphan Removal en acción**

![[image14 11.png]]

Se elimina el vínculo entre Persona y Domicilio ( persona.setDomicilio(null) )

![[image15 7.png]]

Se actualiza la Persona con merge()

![[image22 6.png]]

Resultado: el Domicilio se elimina automáticamente de la base de datos

![[image16 6.png]]

Esto mantiene la base de datos limpia y consistente

✅ **Buenas prácticas**

![[image24 10.png]]

![[image25 3.png]]

![[image26 4.png]]

![[image27 3.png]]

![[image28 3.png]]

![[image29 3.png]]

![[image30 3.png]]

![[image31 3.png]]

![[image32 2.png]]

![[image33 2.png]]

![[image34 2.png]]

![[image35 2.png]]

![[image36 2.png]]

![[image37 2.png]]

![[image38 2.png]]

![[image39 2.png]]

![[image16 7.png]]

Usar cascade solo en el lado propietario

![[image23 3.png]]

Evitar CascadeType.ALL si no se necesita

![[image16 8.png]]

Usar orphanRemoval solo cuando la entidad dependiente no debe existir sola

![[image15 8.png]]

Encadenar tipos de cascada específicos:

cascade = {CascadeType.PERSIST, CascadeType.MERGE, CascadeType.REFRESH}

🧪 **Ejercicio propuesto**

![[image40 2.png]]

Modelar una relación entre Autor y Libro

![[image41 2.png]]

Probar distintas combinaciones de cascade y orphanRemoval

![[image16 9.png]]

Preguntarse:

![[image41 3.png]]

¿Puede existir un libro sin autor?

![[image42 2.png]]

¿Puede existir un autor sin libros?

🧾 **Conclusión**

![[image45 2.png]]

![[image46 2.png]]

![[image43 2.png]]

Cascade simplifica la persistencia de entidades relacionadas Orphan Removal mantiene la base de datos limpia y coherente

![[image44 2.png]]

Estas herramientas permiten pasar de un código manual a uno más profesional y mantenible

<u>10- FetchType LAZY vs EAGER</u>