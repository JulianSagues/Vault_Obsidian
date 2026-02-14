---
notion-id: 28fac26b-dee7-8092-a451-e808f2e93e35
base: "[[Sistemas Operativos.base]]"
Sub-item: []
Blocked by: []
Parent item:
  - 265ac26b-dee7-8009-adbd-fdf5d10c1b59
Blocking: []
Categoria: []
---

Tipos de dispositos e/s


![[60db197f-e369-4a51-90eb-2f088cf0be55.png]]

Para saber si grabe algo bien el disco tengo que devolver y ver si la info esta completa. Para solucionarlo habría que cambiar el bloque y inhabilitar el bloque que no funciona.

Para saber que bloques están ocupados o no uso mapa de bits o lista enlazada.

Nunca cambiar la geometría del disco en un formateo de bajo nivel porque la controladora se confunde y no sabe manejar el disco.

## Acceso Directo a Memoria (DMA) → lo toma

El problema es que hay que prestarle atención a las interrupciones cada vez que suceden.

Las interrupciones son muy molestas como un nene chico que insiste en que le compres algo, las interrupciones molestan a la CPU. Las interrupciones evitan que se ejecuten los procesos.

Las interrupciones son procesos también, los procesos se suspenden para que se ejecuten las interrupciones

DMA→ Acceso Directo a Memoria → me deja ir directo a memoria.

Que es lo que hago con DMA? que hace?

La cpu programa el contralador DMA.

Sirve para grandes transferencias de datos osea el DMA.

El problema de esto es que se comparte el mismo bus con memoria. El DMA ocupa el BUS a memoria y jode si me quiero comunicar con la memoria.

🚀 Método de ráfaga (Burst Mode)

- **Definición:** El controlador DMA toma el control del bus del sistema y transfiere *una ráfaga de múltiples bytes consecutivos* sin liberar el bus entre cada byte.

🚀 Robo de ciclos

El **robo de ciclos** (cycle stealing) es un modo de operación del controlador **DMA** (Acceso Directo a Memoria) en el que se transfiere **un dato por vez**, interrumpiendo brevemente a la CPU para acceder al bus del sistema.

¿Qué solución se por usar DMA pero que no me afecte la comunicación entre memoria y CPU?

La solución es usar otra CPU para que el DMA no interfiera. Los otros disp se veran afectados.

Windows no me da libertad para como llamar a mis dispositivos, en cambio en linux podes tener más libertad. Se busca independencia del path windows no me deja.

Los errores los maneja la controladora.

Si se llena el disco y quiero guardar algo el que me tira el error es el S.O. El error primero lo detecta la controladora.

## Capas de software de E/S

![[image 81.png]]


![[image 82.png]]

mknot es comando para dispositivos en linux.

Si los dispositivos los trato como archivos, osea les doy permisos.

Estudiar la parte de software y hardware de los dispositivos.

![[image 83.png]]

LEER EL PDF DE RAID!!!

[[5.3 - Niveles de RAID.pdf]]

[[5.2 - Mapa conceptual ES 2023.docx]]

El mapa conceptual también.

### Raid

raid 0→ Busco velocidad intercambio datos entre discos, se rompe un disco y perdes todo

raid 1 → La controladora 

raid 5→  Tengo la controladora y voy a tener al menos 3 discos, uno va a ser el disco A, B y C cada uno de un tera.

los driver pueden estar en modo usuario o modo kernel

modo usuario:

- desventaja: es mas complicado hacer algo, tengo que hacer llamadas

modo kernel:

- desventajas: puede arruinar el kernel de SO
