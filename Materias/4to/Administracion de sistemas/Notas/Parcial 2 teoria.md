
# Expo1: Arquitecturas Centralizadas, Descentralizadas y Distribuidas

## Idea central
Una arquitectura informática define **dónde se almacenan los datos, quién procesa, cómo se comunican los equipos y cómo se administra la red**.

## 1. Centralizada
Todo (datos, procesamiento, administración) está en **un único servidor**. Los clientes solo piden y reciben resultados.

- **Ventajas:** fácil de administrar, buen control y seguridad, backups simples.
- **Desventajas:** si el servidor cae, cae todo el sistema; cuello de botella; servidor caro.
- **Ejemplos:** bancos tradicionales, universidades con servidor central.

## 2. Descentralizada
Existen **varios centros de procesamiento independientes** (cada sede/departamento tiene su propio servidor y base de datos), que se comunican entre sí pero mantienen autonomía.

- **Ventajas:** autonomía por área, una falla solo afecta a esa sede, menor carga por equipo.
- **Desventajas:** administración más compleja, riesgo de duplicar información, difícil mantener todo sincronizado.
- **Ejemplos:** empresas con sucursales, organismos de gobierno, universidades con sedes propias.

## 3. Distribuida
El procesamiento y los datos están **repartidos entre múltiples equipos (nodos)** que colaboran como si fueran un solo sistema. El usuario no sabe en qué nodo se ejecuta algo.

- **Ventajas:** alta disponibilidad, escalabilidad, tolerancia a fallos, mejor aprovechamiento del hardware, más velocidad con muchos usuarios.
- **Desventajas:** administración compleja, difícil sincronizar datos, necesita redes confiables.
- **Ejemplos:** Google, Netflix, AWS, Big Data, bases de datos distribuidas.

## Comparación rápida

| Característica       | Centralizada | Descentralizada | Distribuida |
|-----------------------|--------------|------------------|-------------|
| Procesamiento         | 1 servidor   | Varios independientes | Muchos equipos juntos |
| Administración        | Simple       | Media            | Compleja    |
| Escalabilidad         | Baja         | Media            | Alta        |
| Tolerancia a fallos   | Baja         | Media            | Alta        |
| Costo inicial         | Alto         | Medio            | Variable    |

## Conclusión
Hoy la mayoría de las organizaciones usa arquitecturas **distribuidas** por la nube e Internet, pero las tres siguen siendo válidas según el contexto: centralizada = control y simpleza; descentralizada = autonomía; distribuida = disponibilidad y escalabilidad.

# Expo2: Medios de Interconexión Cableados

## Idea central
Son elementos físicos que transportan datos entre dispositivos, convirtiendo la información en señales **eléctricas** (cobre) u **ópticas** (fibra). Los principales son: par trenzado, coaxial y fibra óptica.

## 1. Cable de Par Trenzado
Pares de cobre trenzados entre sí para **reducir interferencias electromagnéticas**. Usado en redes LAN, con conectores **RJ-45** (8 posiciones).

- **UTP** (Unshielded Twisted Pair): sin blindaje, bajo costo, fácil instalación. El más usado en Ethernet.
- **STP** (Shielded Twisted Pair): con blindaje extra, mejor contra interferencias, útil en ambientes con mucha electricidad.

**Normas T568A y T568B:** esquemas de conexión de los cables en el conector RJ-45; difieren en la posición de los pares verde y naranja. **Regla clave:** no mezclar normas en la misma instalación (salvo cable cruzado), o falla la conectividad.

- **Ventajas:** bajo costo, fácil instalación y mantenimiento, buena flexibilidad.
- **Desventajas:** más sensible a interferencias, distancia limitada, rendimiento depende de la categoría del cable.

## 2. Cable Coaxial
Conductor de cobre central rodeado de aislante, malla metálica y cubierta exterior. Señal eléctrica. Fue clave en Ethernet antiguo, hoy usado sobre todo en **TV, cámaras y servicios de acceso por cable**.

**Estructura:** conductor central → dieléctrico/aislante → blindaje metálico → cubierta exterior.

- **Ventajas:** buena protección contra interferencias, resistente, cubre distancias considerables, apto para radiofrecuencia/video.
- **Desventajas:** menos flexible que el par trenzado, instalación más difícil, reemplazado en LAN modernas por UTP/fibra.

## 3. Fibra Óptica
Transmite información mediante **pulsos de luz** por un núcleo de vidrio (no usa corriente eléctrica). Permite grandes velocidades y distancias, con **alta resistencia a interferencias electromagnéticas**.

**Estructura:** cubierta del cable → capas aislantes → buffer → unidades de fibra → miembro de fuerza (FRP, resistencia mecánica).

- **Fibra monomodo (SMF):** núcleo pequeño, un solo modo de propagación → ideal para **larga distancia** y telecomunicaciones.
- **Fibra multimodo (MMF):** núcleo más grande, múltiples modos → ideal para **distancias cortas** (edificios, campus, data centers).

- **Ventajas:** muy alta capacidad, grandes distancias, altísima resistencia a interferencias, baja atenuación.
- **Desventajas:** mayor costo inicial, instalación especializada, fibras físicamente delicadas, empalmes complejos.

## Comparación rápida

| Característica | Par trenzado | Coaxial | Fibra óptica |
|---|---|---|---|
| Señal | Eléctrica | Eléctrica | Óptica |
| Flexibilidad | Alta | Media/baja | Variable |
| Resistencia a interferencias | Media | Buena | Muy alta |
| Distancias largas | Limitadas | Buenas según uso | Excelente |
| Instalación | Sencilla | Moderada | Especializada |
| Uso actual | LAN | TV/RF/HFC | Backbone y telecom |

## Aplicaciones actuales
- **Par trenzado:** hogares, oficinas, redes LAN, empresas, centros de datos.
- **Coaxial:** TV por cable, internet por cable, antenas, radiofrecuencias.
- **Fibra óptica:** proveedores de internet, redes troncales, centros de datos, redes metropolitanas, enlaces entre edificios.

## Conclusión
No hay un medio "mejor" en todos los casos: **par trenzado** = bajo costo y fácil instalación (LAN); **coaxial** = perdió protagonismo en LAN pero sigue en TV/RF; **fibra óptica** = máxima capacidad y distancia, clave en redes troncales y data centers. La elección depende de distancia, velocidad, presupuesto y ambiente.