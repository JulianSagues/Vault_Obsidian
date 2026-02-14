---
Parent item:
  - "[[Materias/Desarrollo de software/Resumen Videos\\|Resumen Videos]]"
---
🔄 **Cascade Type y Orphan Removal en JPA**

🧠 **Introducción**

![[Assets/image1 12.png|image1 12.png]]

Hasta ahora, la persistencia de entidades relacionadas se hacía manualmente.

Esto generaba código repetitivo y propenso a errores.

Con **Cascade Type** y **Orphan Removal**, JPA puede encargarse automáticamente de estas operaciones.

![[Assets/image4 18.png|image4 18.png]]

![[Assets/image5 14.png|image5 14.png]]

![[Assets/image6 16.png|image6 16.png]]

![[Assets/image7 15.png|image7 15.png]]

![[Assets/image8 17.png|image8 17.png]]

![[Assets/image9 12.png|image9 12.png]]

![[Assets/image10 11.png|image10 11.png]]

![[Assets/image11 11.png|image11 11.png]]

🔁 **¿Qué es Cascade?**

Permite que las operaciones realizadas sobre una entidad principal se **propaguen** a sus

entidades relacionadas.

📌 **Ejemplo**

![[Assets/image2 12.png|image2 12.png]]

Si se persiste una Persona , también se persiste automáticamente su Domicilio

![[Assets/image3 18.png|image3 18.png]]

Ya no es necesario llamar a persist() para cada entidad relacionada

🧩 **Tipos de Cascade**

![[Assets/image12 11.png|image12 11.png]]

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

![[Assets/image13 11.png|image13 11.png]]

![[Assets/image14 14.png|image14 14.png]]

Antes: se persistía primero el Domicilio , luego la Persona

![[Assets/image3 18.png|image3 18.png]]

Ahora: con CascadeType.PERSIST , basta con persistir la Persona

![[Assets/image14 14.png|image14 14.png]]

Resultado: el Domicilio se guarda automáticamente

📌 El cascade debe colocarse **del lado propietario** de la relación (no en el mappedBy )

🧪 **Ejemplo práctico: Persona y Cursos (ManyToMany Bidireccional)**

![[Assets/image17 6.png|image17 6.png]]

![[Assets/image18 6.png|image18 6.png]]

![[Assets/image19 15.png|image19 15.png]]

![[Assets/image20 13.png|image20 13.png]]

Persona es el lado propietario (tiene el @JoinTable )

![[Assets/image15 10.png|image15 10.png]]

Se configura cascade = CascadeType.PERSIST en Persona

![[Assets/image14 14.png|image14 14.png]]

Al persistir la Persona , también se persisten los Cursos

![[Assets/image16 11.png|image16 11.png]]

Ya no es necesario persistir cada curso manualmente

🧹 **¿Qué es Orphan Removal?**

![[Assets/image21 18.png|image21 18.png]]

Permite que una entidad relacionada se **elimine automáticamente** si pierde su vínculo con la entidad principal.

📌 **Ejemplo**

![[Assets/image22 7.png|image22 7.png]]

Si se elimina el Domicilio de una Persona , se borra automáticamente de la base de datos

![[Assets/image15 10.png|image15 10.png]]

No hace falta llamar a delete() manualmente

🔸 Se activa con orphanRemoval = true

🔸 Úsalo solo si la entidad dependiente **no tiene sentido por sí sola**

🧪 **Ejemplo práctico: Orphan Removal en acción**

![[Assets/image14 14.png|image14 14.png]]

Se elimina el vínculo entre Persona y Domicilio ( persona.setDomicilio(null) )

![[Assets/image15 10.png|image15 10.png]]

Se actualiza la Persona con merge()

![[Assets/image22 7.png|image22 7.png]]

Resultado: el Domicilio se elimina automáticamente de la base de datos

![[Assets/image16 11.png|image16 11.png]]

Esto mantiene la base de datos limpia y consistente

✅ **Buenas prácticas**

![[Assets/image24 11.png|image24 11.png]]

![[Assets/image25 4.png|image25 4.png]]

![[Assets/image26 5.png|image26 5.png]]

![[Assets/image27 4.png|image27 4.png]]

![[Assets/image28 4.png|image28 4.png]]

![[Assets/image29 4.png|image29 4.png]]

![[Assets/image30 4.png|image30 4.png]]

![[Assets/image31 4.png|image31 4.png]]

![[Assets/image32 3.png|image32 3.png]]

![[Assets/image33 3.png|image33 3.png]]

![[Assets/image34 3.png|image34 3.png]]

![[Assets/image35 3.png|image35 3.png]]

![[Assets/image36 3.png|image36 3.png]]

![[Assets/image37 3.png|image37 3.png]]

![[Assets/image38 3.png|image38 3.png]]

![[Assets/image39 3.png|image39 3.png]]

![[Assets/image16 11.png|image16 11.png]]

Usar cascade solo en el lado propietario

![[Assets/image23 4.png|image23 4.png]]

Evitar CascadeType.ALL si no se necesita

![[Assets/image16 11.png|image16 11.png]]

Usar orphanRemoval solo cuando la entidad dependiente no debe existir sola

![[Assets/image15 10.png|image15 10.png]]

Encadenar tipos de cascada específicos:

cascade = {CascadeType.PERSIST, CascadeType.MERGE, CascadeType.REFRESH}

🧪 **Ejercicio propuesto**

![[Assets/image40 3.png|image40 3.png]]

Modelar una relación entre Autor y Libro

![[Assets/image41 4.png|image41 4.png]]

Probar distintas combinaciones de cascade y orphanRemoval

![[Assets/image16 11.png|image16 11.png]]

Preguntarse:

![[Assets/image41 4.png|image41 4.png]]

¿Puede existir un libro sin autor?

![[Assets/image42 3.png|image42 3.png]]

¿Puede existir un autor sin libros?

🧾 **Conclusión**

![[Assets/image45 3.png|image45 3.png]]

![[Assets/image46 3.png|image46 3.png]]

![[Assets/image43 3.png|image43 3.png]]

Cascade simplifica la persistencia de entidades relacionadas Orphan Removal mantiene la base de datos limpia y coherente

![[Assets/image44 3.png|image44 3.png]]

Estas herramientas permiten pasar de un código manual a uno más profesional y mantenible

10- FetchType LAZY vs EAGER