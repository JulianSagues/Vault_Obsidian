---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
🔄 **Cascade Type y Orphan Removal en JPA**

🧠 **Introducción**

![[Assets/image1 3.png|image1 3.png]]

Hasta ahora, la persistencia de entidades relacionadas se hacía manualmente.

Esto generaba código repetitivo y propenso a errores.

Con **Cascade Type** y **Orphan Removal**, JPA puede encargarse automáticamente de estas operaciones.

![[Assets/image4 3.png|image4 3.png]]

![[Assets/image5 3.png|image5 3.png]]

![[Assets/image6 3.png|image6 3.png]]

![[Assets/image7 3.png|image7 3.png]]

![[Assets/image8 3.png|image8 3.png]]

![[Assets/image9 3.png|image9 3.png]]

![[Assets/image10 3.png|image10 3.png]]

![[Assets/image11 3.png|image11 3.png]]

🔁 **¿Qué es Cascade?**

Permite que las operaciones realizadas sobre una entidad principal se **propaguen** a sus

entidades relacionadas.

📌 **Ejemplo**

![[Assets/image2 3.png|image2 3.png]]

Si se persiste una Persona , también se persiste automáticamente su Domicilio

![[Assets/image3 3.png|image3 3.png]]

Ya no es necesario llamar a persist() para cada entidad relacionada

🧩 **Tipos de Cascade**

![[Assets/image12 3.png|image12 3.png]]

|**Tipo**|**Propagación de…**|**Uso común**|
|---|---|---|
|PERSIST|Guardado|✅|
|MERGE|Actualización|✅|
|REMOVE|Eliminación|⚠️|
|REFRESH|Sincronización desde BD|Opcional|
|DETACH|Desvinculación del contexto|Raro|
|ALL|Todos los anteriores|⚠️|

🔸 Es mejor **no usar** CascadeType.ALL **por defecto**.

🔸 Conviene elegir solo los tipos necesarios para cada relación.

🧪 **Ejemplo práctico: Persona y Domicilio**

![[Assets/image13 3.png|image13 3.png]]

![[Assets/image14 3.png|image14 3.png]]

Antes: se persistía primero el Domicilio , luego la Persona

![[Assets/image3 3.png|image3 3.png]]

Ahora: con CascadeType.PERSIST , basta con persistir la Persona

![[Assets/image14 3.png|image14 3.png]]

Resultado: el Domicilio se guarda automáticamente

📌 El cascade debe colocarse **del lado propietario** de la relación (no en el mappedBy )

🧪 **Ejemplo práctico: Persona y Cursos (ManyToMany Bidireccional)**

![[Assets/image17 2.png|image17 2.png]]

![[Assets/image18 2.png|image18 2.png]]

![[Assets/image19 2.png|image19 2.png]]

![[Assets/image20 2.png|image20 2.png]]

Persona es el lado propietario (tiene el @JoinTable )

![[Assets/image15 2.png|image15 2.png]]

Se configura cascade = CascadeType.PERSIST en Persona

![[Assets/image14 3.png|image14 3.png]]

Al persistir la Persona , también se persisten los Cursos

![[Assets/image16 2.png|image16 2.png]]

Ya no es necesario persistir cada curso manualmente

🧹 **¿Qué es Orphan Removal?**

![[Assets/image21 2.png|image21 2.png]]

Permite que una entidad relacionada se **elimine automáticamente** si pierde su vínculo con la entidad principal.

📌 **Ejemplo**

![[image22.png]]

Si se elimina el Domicilio de una Persona , se borra automáticamente de la base de datos

![[Assets/image15 2.png|image15 2.png]]

No hace falta llamar a delete() manualmente

🔸 Se activa con orphanRemoval = true

🔸 Úsalo solo si la entidad dependiente **no tiene sentido por sí sola**

🧪 **Ejemplo práctico: Orphan Removal en acción**

![[Assets/image14 3.png|image14 3.png]]

Se elimina el vínculo entre Persona y Domicilio ( persona.setDomicilio(null) )

![[Assets/image15 2.png|image15 2.png]]

Se actualiza la Persona con merge()

![[image22.png]]

Resultado: el Domicilio se elimina automáticamente de la base de datos

![[Assets/image16 2.png|image16 2.png]]

Esto mantiene la base de datos limpia y consistente

✅ **Buenas prácticas**

![[image24.png]]

![[image25.png]]

![[image26.png]]

![[image27.png]]

![[image28.png]]

![[image29.png]]

![[image30.png]]

![[image31.png]]

![[image32.png]]

![[image33.png]]

![[image34.png]]

![[image35.png]]

![[image36.png]]

![[image37.png]]

![[image38.png]]

![[image39.png]]

![[Assets/image16 2.png|image16 2.png]]

Usar cascade solo en el lado propietario

![[image23.png]]

Evitar CascadeType.ALL si no se necesita

![[Assets/image16 2.png|image16 2.png]]

Usar orphanRemoval solo cuando la entidad dependiente no debe existir sola

![[Assets/image15 2.png|image15 2.png]]

Encadenar tipos de cascada específicos:

cascade = {CascadeType.PERSIST, CascadeType.MERGE, CascadeType.REFRESH}

🧪 **Ejercicio propuesto**

![[image40.png]]

Modelar una relación entre Autor y Libro

![[image41.png]]

Probar distintas combinaciones de cascade y orphanRemoval

![[Assets/image16 2.png|image16 2.png]]

Preguntarse:

![[image41.png]]

¿Puede existir un libro sin autor?

![[image42.png]]

¿Puede existir un autor sin libros?

🧾 **Conclusión**

![[image45.png]]

![[image46.png]]

![[image43.png]]

Cascade simplifica la persistencia de entidades relacionadas Orphan Removal mantiene la base de datos limpia y coherente

![[image44.png]]

Estas herramientas permiten pasar de un código manual a uno más profesional y mantenible

10- FetchType LAZY vs EAGER