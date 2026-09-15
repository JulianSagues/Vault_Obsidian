**1. La Regla de los Bits (El Árbol del Profesor)**

Toda dirección IPv4 tiene 32 bits divididos en dos zonas por la máscara de subred:
- **Parte de Red:** Se representa con **unos ($111...$)** en la máscara y queda **fija**.
- **Parte de Host ($H$):** Se representa con **ceros ($000...$)** en la máscara y es la que **varía**.
A partir de esta división se calculan los elementos clave:
- **Máscara ($Mas$):** Parte de red en $1$, parte de host en $0$.
- **IP de Red ($P_{red}$):** Parte de red fija, parte de host en **todos ceros ($000...0$)**.
- **Broadcast ($Br$):** Parte de red fija, parte de host en **todos unos ($111...1$)**.
- **Primer Host:** Parte de red fija, parte de host terminada en **$...0001$** ($P_{red} + 1$).
- **Último Host:** Parte de red fija, parte de host terminada en **$...1110$** ($Br - 1$).
**2. Caso A: Te piden armar o dimensionar una subred (VLSM)**
Se usa cuando el enunciado te da una cantidad de computadoras $N$ requeridas (ej: "se necesitan 22 hosts").
- **Paso 1: Calcular los bits de host ($H$) con la inecuación**$$2^H - 2 \ge N$$
    Buscás el menor exponente entero $H$ que cumpla la desigualdad.
    - _Ejemplo:_ Para $N = 22 \rightarrow 2^5 - 2 = 30 \ge 22$. Se necesitan **$H = 5$ bits de host**.
- **Paso 2: Calcular la nueva máscara y la barra**
    Restás los bits de host a los 32 bits totales:$$\text{Barra} = 32 - H$$
    - _Siguiendo el ejemplo:_ $32 - 5 = \mathbf{/27}$.
    - En binario: 27 unos y 5 ceros $\rightarrow$ `11111111.11111111.11111111.11100000` $\rightarrow$ **`255.255.255.224`**.
- **Paso 3: Obtener Red y Broadcast**
    Reservás los últimos $H$ bits del octeto en cuestión:
    - Para $P_{red}$: ponés esos $H$ bits en `0`.
    - Para $Br$: ponés esos $H$ bits en `1`.

**3. Caso B: Te dan una IP y una Máscara (o Barra) para analizar**
Se usa cuando te dan datos como `202.25.145.80` con máscara `255.255.255.192`.
- **Paso 1: Contar los bits de host ($H$)**
    - Si te dan la barra $/X$: $H = 32 - X$.
    - Si te dan la máscara en decimal: pasás a binario el octeto modificado y contás cuántos ceros hay al final.
    - _Ejemplo:_ `...192` es `11000000` $\rightarrow$ tiene **$H = 6$ bits de host** (y 26 unos $\rightarrow$ **/26**).
- **Paso 2: Calcular la cantidad máxima de hosts**$$\text{Hosts} = 2^H - 2$$
    - _Siguiendo el ejemplo:_ $2^6 - 2 = 64 - 2 = \mathbf{62\text{ hosts}}$.
- **Paso 3: Obtener la IP de Red ($P_{red}$)**
    Convertís el octeto de la IP a binario y ponés sus últimos $H$ bits en cero:
    - IP `80` en binario: `0 1 | 0 1 0 0 0 0`
    - Forzar los últimos 6 bits a cero: `0 1 | 0 0 0 0 0 0` $\rightarrow$ **64** en decimal.
    - $P_{red} =$ **`202.25.145.64`**.
- **Paso 4: Obtener el Broadcast ($Br$)**
    Tomás la misma parte de red y ponés los últimos $H$ bits en uno:
    - `0 1 | 1 1 1 1 1 1` $\rightarrow 64 + 63 =$ **127** en decimal.
    - $Br =$ **`202.25.145.127`**.
- **Paso 5: Armar el rango útil**
    - Primer host: $P_{red} + 1 \rightarrow$ **`202.25.145.65`**.
    - Último host: $Br - 1 \rightarrow$ **`202.25.145.126`**.