---
Archivos Adjuntos: ""
Sub-item: []
Blocked by: []
Parent item:
  - "[[Notion/Materias/Desarrollo de software/Resumen Videos|Resumen Videos]]"
Blocking: []
Categoria: ""
---
![[image1 6.png]]

El entity manager. Como habíamos dicho, es como el control remoto que va a gestionar cuando una entidad está conectada, desconectada o marcada para borrar.

![[image2 6.png]]

En JPA, una entidad puede estar en cuatro estados diferentes.

Primero, nuevo, transient, que vendría a ser cuando un objeto en Java está recién creado y que JPA todavía no conoce.

Segundo sería gestionado persistent, que está bajo control del entity manager y que cualquier cambio se sincroniza con la base de datos.

Tercero sería desasociado, detached, donde tiene un ID, pero no está siendo gestionado activamente.

Y por último, eliminado, removed, que está marcado para borrarse en la base de datos.

Visualmente es como si tuviera vidas, nace, se conecta, se desconecta y finalmente se elimina.

![[image3 6.png]]

Cuando instancian un objeto con new, ese objeto solamente existe en la memoria, no tiene un id asignado por la base de datos y JPA no tiene la idea de que existe.

En este estado puedes modificarlo libremente, pero nada de eso se va a guardar en la base de datos hasta que lo incorporen en JPA.

![[image4 6.png]]

Una entidad está siendo gestionada cuando el entity manager la está controlando.

Esto significa que si hacemos algún cambio en la entidad, JPA se va a dar cuenta y lo va a guardar automáticamente al hacer el commit. Esto se llama dirty checking.

Podemos llegar a este estado de varias maneras, usando el persist sobre una entidad nueva, usando el find para buscar una entidad que ya exista, ejecutando consulta JPQL o criterio que devuelva entidades.

Además, en este estado, JPA usa la caché de primer nivel, lo que evita consultas innecesarias.

![[image5 7.png]]

Ahora hablemos del estado desasociado.

Una entidad pasa a este estado cuando ya no está más bajo control del entity manager, aunque todavía tiene un ID válido en la base de datos.

Podemos llegar a este estado si nosotros cerramos el entity manager o si llamamos al método detached sobre esa entidad o la serializamos.

El problema es que si la modificamos en este estado, JPA no se va a enterar y los cambios no se van a guardar en la base de datos.

![[image6 9.png]]

El siguiente estado del que voy a hablar es el estado eliminado, removed.

Este es el estado donde la entidad pasa a estar marcada para eliminarse de la base de datos.

Se llega a este estado desde el estado gestionado usando el método remove.

El borrado real no pasa al instante, sino que cuando se confirma la transacción con el comit.

![[image7 8.png]]

Ahora que ya vimos cada estado por separado, vamos a conectar los puntos.

En JPA las entidades no saltan entre estados al azar. Hay operaciones específicas que hacen que eso pase.

Es como un mapa de rutas que si queremos ir de nuevo gestionado, hay un camino concreto. Si queremos ir de gestionado a eliminado, hay otro distinto.

Aquí tenemos un ejemplo visual donde vemos que el nuevo pasa a gestionado con el persistent, pasa a desasociado cerrando el entity manager o usando el detached.

Desasociado pasa gestionado con el merge y gestionado pasa eliminado con el remove.

![[image8 7.png]]

![[image9 6.png]]

![[image10 5.png]]

![[image11 5.png]]

El ciclo nuevo que vendría a ser la entidad creada con new, sin ID y fuera del control de JPA.

Gestionada, que vendría a ser bajo el control del entity manager, donde los cambios son sincronizados automáticamente.

Después el estado desasociado con ID, pero sin gestión activa, es decir, que los cambios no se van a guardar en la base de datos.

Después tenemos el estado eliminado que está marcado para borrarse y se elimina físicamente en el commit.

Las operaciones claves son persist, merge, remove, close y detach. Y es importante recordar que el entity manager es el que va a decidir el estado de nuestra entidad.

**Ejemplo de código ciclo de vida de entidades**

![[image12 5.png]]

Primero creamos el EntityManagerFactory y el EntityManager

![[image13 5.png]]

Un producto con new. En este momento el producto está en ese estado nuevo o transient donde todavía no tiene un ID asignado, tampoco va a estar registrado en el contexto de JPA. Y si nosotros ahora mismo cerramos el programa, ese objeto va a desaparecer sin dejar rastro en la base de datos.

Esto es lo que habíamos dicho en la teoría, donde aquí solamente tenemos un simple objeto Java.

![[image14 5.png]]

Ahora, para pasar de ese estado nuevo donde era un simple objeto Java, para pasar al estado gestionado, lo que hice fue iniciar una transacción y persistir ese producto donde al persistirlo está siendo gestionado por JPA. Luego, obviamente, hice el comit.

En este punto es donde el producto pasa a estar gestionado. Eso significa que ya tiene un ID asignado y JPA lo está controlando.

Si nosotros llegamos a modificar un campo, JPA va a detectar ese cambio automáticamente gracias al dirty checking.

![[image15 2.png]]

Realicemos un cambio mientras el producto está siendo gestionado.

Ahora lo que hice fue realizar cambios en el producto mientras está en el estado gestionado. Para eso inicié la transacción, modifiqué el precio del producto, que JPA lo va a detectar automáticamente y realicé el commit.

Y como se puede ver, no hice ningún update manualmente y JPA se va a encargar de generar ese update en la base de datos.

Eso muestra la diferencia entre un objeto nuevo y uno gestionado, donde al estar gestionado y nosotros hacer un commit, cualquier modificación que hicimos se va a ver reflejada.

En cambio, si simplemente fuera un objeto nuevo, obviamente esos cambios no se verían en la base de datos y se perdería todo.

![[image16 2.png]]

Si vamos a la base de datos se puede ver el cambio que se le hizo al producto en estado gestionado. Donde paso del precio 1200 al 1100.

Y esto fue gracias a JPA, ya que nosotros no tuvimos que hacer ningún update manualmente.

![[image17 1.png]]

Para ver el siguiente estado, detach o desasociado, lo que hice fue cerrar el entity manager.

Una vez que nosotros cerramos el Entity Manager, el producto va a seguir existiendo en la memoria y también va a tener un ID, pero no va a estar siendo gestionado por JPA.

Y al no estar gestionado, si nosotros realizamos un cambio, no se va a ver reflejado en la base de datos.

![[image18 1.png]]

Por ejemplo, si nosotros modificamos el precio del producto y mostramos por pantalla, vamos a ver que el cambio sí se hizo, pero eso no se va a guardar en la base de datos, simplemente es un cambio de nuestro objeto en memoria.

Y claramente para nosotros ver reflejados estos cambios tenemos que pasar del estado desasociado a el estado gestionado.

![[image19 1.png]]

Para nosotros poder volver ese producto al estado gestionado, lo que hice fue crear otro entity manager y haciendo un merge de producto donde cualquier cambio que hagamos sobre producto ahora sí se va a ver reflejado nuevamente.

A lo mejor se preguntan por qué cree otro entity manager y la razón es que yo cerré el entity manager anterior.

![[image20 1.png]]

Ahora si corremos el programa y vamos a la aplicación si se ve reflejado el cambio.

![[image21 1.png]]

Por último, veamos el estado eliminado o removed, donde como siempre iniciamos la transacción.

En este caso vamos a remover justamente el producto para pasarlo a ese estado de removed y hacemos el commit en la base de datos.

Y recién cuando hacemos este commit se elimina físicamente el registro de la base de datos.

<u>7- Relaciones Unidireccionales en JPA</u>