
---
![[1-Diagrama de Casos de Uso.drawio]]

[[Explicación Consultoría]]

---
### Actores:
- Socio Responsable: Profesional/persona de la consultoría con tareas referidas gestión de convenios
- Demonio de facturación: programa que se encarga de hacer facturación de convenios
- Profesional: persona que realiza los servicios del convenio
- Cliente: persona que solicita un convenio
- Administrador del sistema: "creador" del sistema que se encarga de tareas referidas al sistema
---
[[CU - Aceptar convenio (Maxi).docx|Aceptar Convenio]]
Para realizar este caso de uso el convenio debe estar registrado. El socio responsable deberá ingresar el numero de convenio. Una vez ingresado se verifica que el profesional tenga una disponibilidad horaria compatible con las pedidas por el tipo de servicio solicitado por el cliente, de ser así, se acepta el convenio y queda en estado aceptado. En caso contrario el convenio quedara rechazado. De ser aceptado se comienza con la primera iteración del servicio.

![[Aceptar Convenio.svg]]
[[Aceptar Convenio.svg]]

---
[[CU - Aprobar servicio.docx|Aprobar servicio]]
Para realizar este convenio el servicio debe estar terminado. El cliente comprobara que el servicio realizado tiene todo lo que el profesional dijo que realizado. De confirmarlo el servicio pasa a aprobado, en caso contrario vuelve a estar en proceso.

![[Aprobar servicio.svg]]
[[Aprobar servicio.svg]]

---
[[CU - Cancelar convenio (Maxi).docx|Cancelar convenio]]

un convenio podrá cancelarse si se encuentra aprobado, firmado o en progreso. En el caso de estar en progreso se deberán cancelar todos los servicios que se están realizando pasando de en progreso a terminados y los servicios asignados pasaran a estar cancelados.

---
[[CU - Configurar tarifas.docx|Configurar tarifas]]
el profesional podrá agregar y modificar las tarifas de un tipo de servicio. Si modifica podra elegir entre modificar el monto, las fechas o agregar una instancia de tipo servicio

---
[[CU - Entregar servicio (Maxi).docx|Entregar servicio]]
El profesional podra entregar aquellos servicios que esten en estado en progreso, de ahi se actualizaran las horas efectuadas totales teniendo en cuenta las tareas realizadas y agregara las observaciones pertinentes.

---
[[CU - Firmar convenio.docx|Firmar Convenio]]
El cliente  decide firmar para empezar a trabajar en el

---
[[CU - Gestionar convenios (Maxi).docx|Gestionar convenios]]
Se puede modificar y registrar un convenio que no este aceptado. Se puede modificar los servicios, cliente, proyecto y fechas del convenio. Un servicio se puede agregar o eliminar, ademas de modificar el servicio como tal. 

---
[[CU - Gestionar proceso de facturación.docx|Gestionar proceso de facturacion]]
Para poder facturar debe haberse iniciado el rpoceso de facturacion. Se puede visualizar, enviar, reenviar y anular. Para enviar se debe tener el resultado del CU iniciar proceso de facturacion. Este proceso puede fallar o no, en el caso de fallar se realizan 3 intentos y si no se logra comunicar con arca, el procesos queda como fallido, pero en el caso de funcionar se completan los datos faltantes de las clases correspondientes. El porceso fallido se puede intentar reenviar para realizar la facturacion.

---
[[Materias/Diseño de sistemas/Material/TP1/Flujos de sucesos/CU5 - Gestionar servicios/CU - Gestionar servicios.docx|Gestionar servicios]]
Segun el rol del usuario se mostraran y podra realizar cosas teniendo en cuenta lo determinado por el sistema. Por ejemplo un cliente podra aprobar un servicio

---
[[CU - Iniciar proceso de facturación.docx|Iniciar Proceso de facturacion]]
El demonio se encarga de buscar convenios firmados, terminados, en proceso o cancelados para cobrar aquellos servcios que esten en proceso o terminados, calculando los montos del convenio y sus servicios y tipo de servicios, ademas de generar la rimera instancia de la factura del cliente

---
[[CU - Iniciar sesión.docx|Iniciar sesion]]
se explica solo

---
[[Materias/Diseño de sistemas/Material/TP3/CU - Registrar tarea.docx|Registrar tarea]]
El profesional puede registrar la tarea de un servicio. En el caso de ser la primera tarea de un servicio, el mismo pasara a estar en progreso

---
[[CU - Solicitar servicio.docx|Solicitar servicio]]
El cliente solicita servicios, para ello determina el tipo de servicio que desea, las horas promedio que necesita. A partir de eso se verificara que haya disponibilidad horario, en el caso de haberla debera ingresar la descripcion de lo que desea.

---
## Dudas
Cuando se anula una facturacion
Porque se factura un convenio firmado
donde esta la nota de credito o en que parte se realiza

---