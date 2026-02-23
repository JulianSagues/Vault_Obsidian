- [[1-Diagrama de Clases.drawio]]
- [[1-Diagrama de Casos de Uso.drawio]]

---
[[CU - Aceptar convenio.docx]]

**Estado Inicial:**
- El convenio tiene que estar registrado
- El profesional tiene que saber sobre el tipo servicio
- Debe existir el estado aceptado (si hay disponibilidad horaria), registrado, en progreso, registrado y rechazado(si no hay disponibilidad horaria)
**Estado Final:**
- El convenio queda aceptado o rechazado
**Parámetros de Entrada:**
- numeroConvenio
**Precondición:**
- profesional instanciado con socioResponsable verdadero
**Flujo:**
1. Inicia caso de uso
2. Se verifica que el profesional sea socio responsable y se le pide que ingrese el numeroConvenio
3. Ingresa numeroConvenio
4. Se verifica que el numero sea correcto, se buscan los estados registrado, aceptado, firmado, en progreso y rechazado y se verifica que el convenio este registrado
5. Leemos el inicio de