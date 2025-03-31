# Cuaderno1_Mario_LL
https://github.com/mllangon/Cuaderno1_Mario_LL.git
# Actividad: Ejercicios de Aplicación – Temas 1, 2 y 3

**Nombre del estudiante:** [Escribe tu nombre aquí]  
**Asignatura:** Sistemas de Comunicación  
**Fecha de entrega:** [Indicar fecha]

---

## Objetivo

El propósito de esta actividad es aplicar los conocimientos adquiridos en los temas 1, 2 y 3 mediante la resolución de problemas relacionados con sistemas de comunicación, modulación, protocolos y redes. Se busca fortalecer la comprensión de los fundamentos teóricos a través del análisis y resolución de casos prácticos.

---

## Ejercicio 1

### Enunciado
Para un sistema de comunicaciones con 17 niveles de señal, que funciona en banda base, calcular el máximo ancho de banda si el ruido es despreciable y la tasa de transmisión es de 10 Mbits/s. ¿Qué tipo de medio guiado se podría utilizar para el sistema?

### Resolución
Usamos la **fórmula de Nyquist**:

\[
C = 2B \cdot \log_{2}(M)
\]

Donde:
- \( C = 10 \times 10^6 \) bps  
- \( M = 17 \) niveles de señal  

Sustituyendo:

\[
\log_{2}(17) \approx 4.09
\]  
\[
10 \times 10^6 = 2B \cdot 4.09
\]  
Despejamos \(B\):

\[
B = \frac{10 \times 10^6}{2 \cdot 4.09} \approx 1.22 \text{ MHz}
\]

**Resultado:** El ancho de banda necesario es **1.22 MHz**.

**Tipo de medio guiado sugerido:**  
Cable coaxial, par trenzado apantallado (STP) o UTP categoría 5 (o superior).

---

## Ejercicio 2

### Enunciado
¿Cuál es la tasa de transmisión máxima en un canal óptico con fibra de ancho de banda de **1 THz** y conversores optoeléctricos de **100 Gbaudios**, si la relación SNR es de **15 dB** y la modulación utilizada en los conversores es de **4 símbolos en cuadratura**?

### Resolución

**Paso 1: Conversión de SNR a escala lineal**

\[
\text{SNR}_{\text{lineal}} = 10^{\frac{15}{10}} = 31.62
\]

---

**Paso 2: Aplicamos la fórmula de Shannon**

\[
C = B \cdot \log_2(1 + \text{SNR})
\]
\[
C = 1 \times 10^{12} \cdot \log_2(1 + 31.62)
\]
\[
\log_2(32.62) \approx 5.03
\]
\[
C = 1 \times 10^{12} \cdot 5.03 = 5.03 \times 10^{12} \, \text{bps} = 5.03 \, \text{Tbps}
\]

---

### Velocidad real con conversores

- **100 Gbaudios** con modulación de **4 símbolos** (QPSK).  
- Cada símbolo lleva \(\log_2(4) = 2\) bits.  
- Velocidad:

\[
100 \times 10^9 \times 2 = 200 \, \text{Gbps}
\]

---

### Resultado final

- **Tasa teórica máxima del canal**: 5.03 Tbps  
- **Tasa real** (limitada por conversores y modulación): 200 Gbps

---

## Ejercicio 3 – Resolución completa y explicada

### Enunciado
Si en el sistema anterior se introduce un conector de fibra con un **20% de pérdidas**, responder a las siguientes cuestiones:

a) ¿Se verá afectada la tasa de transmisión máxima?  
b) ¿Qué velocidad máxima se tendrá en la salida?

---

### a) ¿Se verá afectada la tasa de transmisión máxima?
**Sí.**  
La fórmula de Shannon depende directamente de la **SNR**. Al introducir una pérdida del 20 %, la **potencia de la señal disminuye**, lo que reduce la SNR y, por ende, **reduce la capacidad máxima teórica del canal**.

> **Conclusión:** Sí, la tasa máxima se verá afectada.

---

### b) ¿Qué velocidad máxima se tendrá en la salida?

**Paso 1: Reducción de la SNR**  
SNR original (lineal):  
\[
\text{SNR}_{\text{original}} = 31.62
\]  
Con pérdida del 20%:  
\[
\text{SNR}_{\text{nueva}} = 0.8 \times 31.62 = 25.296
\]

---

**Paso 2: Aplicamos la fórmula de Shannon**

\[
C = B \cdot \log_2(1 + \text{SNR})
\]
\[
C = 1 \times 10^{12} \cdot \log_2(1 + 25.296)
\]
\[
\log_2(26.296) \approx 4.72
\]
\[
C = 1 \times 10^{12} \times 4.72 = 4.72 \times 10^{12} \, \text{bps} = 4.72 \, \text{Tbps}
\]

**Resultado:**  
- **Nueva capacidad máxima teórica**: 4.72 Tbps  
- **Velocidad real práctica (limitada por conversores)**: 200 Gbps  

(Conversores a 100 Gbaudios y modulación QPSK.)

---

### Conclusión final
Aunque la pérdida afecta la **capacidad máxima teórica** (de 5.03 Tbps a 4.72 Tbps), la **velocidad real de transmisión** sigue siendo **200 Gbps**, siempre que la nueva SNR sea suficiente para mantener la modulación sin errores.

---

## Ejercicio 4

### Enunciado
Indicar el tipo de modulación que se está utilizando y los problemas que plantea en los casos B y C.

### Análisis de los diagramas de constelación

- **Caso A**  
  La constelación muestra 4 puntos bien definidos, distribuidos simétricamente en los ejes In-Phase (I) y Quadrature (Q).  
  Esto corresponde a una modulación **QPSK** (Quadrature Phase Shift Keying).

- **Caso B**  
  El diagrama muestra 16 puntos agrupados alrededor de posiciones teóricas, pero con una dispersión notable.  
  Esto indica una modulación **16-QAM** (Quadrature Amplitude Modulation), pero con **ruido o interferencia** que provoca esa dispersión.  
  **Problema identificado**: la dispersión puede deberse a **ruido térmico**, **interferencia aditiva** o **atenuación**, lo que podría generar **errores en la demodulación**.

- **Caso C**  
  Se observan símbolos también de **16-QAM**, pero con una distribución menos clara y más concentrada hacia el centro.  
  **Problema identificado**: puede ser indicativo de **desfase de fase (rotación)** o **desalineación del plano IQ**, posiblemente provocado por **errores de sincronización de portadora** o **distorsión del canal**.

---

### Resumen de modulaciones y problemas
- **A**: QPSK – sin errores aparentes.  
- **B**: 16-QAM – afectada por **ruido aditivo**.  
- **C**: 16-QAM – afectada por **rotación de fase** o **distorsión de canal**.

---

## Ejercicio 5

### Enunciado
Sabiendo que se transmiten dos señales de forma simultánea y que se aplican dos modulaciones diferentes:

a) Indicar qué dos modulaciones se están aplicando.  
b) Recuperar la información de ambas señales.

---

### a) Identificación de modulaciones
Analizando la señal compuesta, se observan dos componentes distintas:

1. Una componente con **variación de amplitud y frecuencia constante**, lo que indica una **modulación en amplitud (AM)**.  
2. Otra componente que muestra **cambios en la frecuencia con envolvente constante**, indicando **modulación en frecuencia (FM)** o **FSK**.

**Resultado**:  
Las dos modulaciones que se están aplicando simultáneamente son:  
- **AM** (Amplitud Modulada)  
- **FM/FSK** (Frecuencia Modulada o Modulación por desplazamiento de frecuencia)

---

### b) Recuperación de la información de ambas señales
Para recuperar la información de cada señal es necesario aplicar un proceso de **demodulación selectiva**, generalmente en el dominio de la frecuencia:

1. **Filtrado en frecuencia**  
   Separar las dos señales moduladas aplicando un **filtro pasabanda** centrado en cada una de sus frecuencias portadoras.

2. **Demodulación individual**  
   - Para la señal **AM**: utilizar un **detector de envolvente** o **demodulador síncrono**.  
   - Para la señal **FM**: utilizar un **discriminador de frecuencia** o un **PLL (Phase Locked Loop)**.

Este proceso se realiza en sistemas de radio heterodinos o en radios definidas por software (SDR), permitiendo la separación y recuperación de múltiples señales transmitidas en paralelo.

---

## Ejercicio 6

### Enunciado
Indicar las longitudes de onda que se transmiten en cada uno de los puntos marcados en el esquema.

### Análisis del sistema
El esquema representa un sistema de transmisión óptica basado en **WDM (Wavelength Division Multiplexing)**, donde se combinan distintas longitudes de onda para ser transmitidas a través de una sola fibra y luego separadas nuevamente.

---

### Funcionamiento por bloques

- **Entradas al combiner (multiplexor)**  
  Cada una de las fibras de entrada transporta una señal óptica con una **longitud de onda diferente**:  
  - Entrada 1: \(\lambda_2\)  
  - Entrada 2: \(\lambda_3\)  
  - Entrada 3: \(\lambda_4\)  
  - Entrada 4: \(\lambda_1\)

- **Fibra compartida**  
  El **combiner** junta todas estas señales en una sola fibra. Por tanto, en esta sección viajan simultáneamente:  
  \(\lambda_1 + \lambda_2 + \lambda_3 + \lambda_4\)

- **Splitter (demultiplexor)**  
  El **splitter** divide las señales de nuevo para que lleguen a distintos receptores. En cada salida, se puede:  
  - Enviar todas las longitudes de onda (si no hay filtrado), o  
  - Separar selectivamente cada longitud de onda usando filtros.

---

### ¿Qué representan las partes grises en las salidas del splitter?
Las piezas grises en el esquema, ubicadas antes del extremo de cada salida, representan probablemente:

1. **Filtros ópticos sintonizados por longitud de onda**  
   Permiten que cada salida deje pasar únicamente **una longitud de onda específica (\(\lambda_i\))**.  
2. **Receptores ópticos integrados**  
   Pueden incluir **fotodetectores** (conversión óptico-eléctrica).  
3. **Conectores ópticos con filtrado**  
   En algunos sistemas, los conectores pueden incluir funciones de filtrado o atenuación selectiva.

---

### Conclusión
- En las **entradas**, cada fibra lleva una longitud de onda diferente (\(\lambda_1\) a \(\lambda_4\)).  
- En la **fibra compartida**, se transmiten todas las longitudes de onda simultáneamente.  
- En las **salidas del splitter**, cada puerto puede recibir todas las longitudes de onda o una filtrada, dependiendo del uso de filtros ópticos o receptores específicos.

Las partes grises indican componentes que **seleccionan o reciben** una longitud de onda específica, asegurando que cada señal llegue al destino correcto.

---

## Ejercicio 7

### Enunciado
Se considera una pila de protocolos de 4 capas. La capa 4 envía un bloque de 1 Kbyte.  
La capa 3 añade cabeceras de 256 bits y cada paquete es de 512 bytes.  
La capa 2 añade cabeceras de 512 bits y el campo de datos de las tramas son de 128 bytes.  
La capa 1 añade a cada 30 bytes de datos: 32 bits de comienzo, un byte de parada, y 16 bits de CRC.  

Dibujar el proceso de encapsulamiento y calcular la eficiencia del sistema.

![image](https://github.com/user-attachments/assets/64eab142-1901-4e01-b33a-3bea240abd23)

---

## Ejercicio 8

### Enunciado
Un sistema satélite divide la información de la capa 3 en bloques de **1904 bits**, a los que añade una cabecera de **64 bits**.  
Si cada trama tarda en transmitirse **20 ms** y la latencia del satélite es de **85 ms**, ¿cuánto tiempo tardará en realizar la transmisión de **5 Mbytes** de información?

### Resolución

1. **Tamaño total por trama**  
\[
1904 + 64 = 1968 \text{ bits}
\]

2. **Total de bits a transmitir**  
\[
5 \text{ MB} = 5 \times 1024 \times 1024 \times 8 = 41{,}943{,}040 \text{ bits}
\]

3. **Número de tramas necesarias**  
\[
\frac{41{,}943{,}040}{1968} \approx 21{,}309.3 \Rightarrow 21{,}310 \text{ tramas}
\]

4. **Tiempo total de transmisión**  
   - **Transmisión**: \(21{,}310 \times 20 \text{ ms} = 426{,}200 \text{ ms} = 426.2 \text{ s}\)  
   - **Latencia** (asumiendo ida + vuelta): \(2 \times 85 = 170 \text{ ms} = 0.17 \text{ s}\)

**Resultado final**  
\[
\text{Tiempo total} = 426.2 + 0.17 = 426.37 \text{ segundos}
\]

---

## Ejercicio 9

### Enunciado
Calcular el resultado de un paquete de datos “1111011101010101” en un sistema de enlace de datos con las siguientes especificaciones:

- Secuencia de inicio de trama: “010101010”  
- Protección frente a errores: Hamming (7,4)  
- Tamaño máximo por trama: 4 bytes

### Resolución

**Datos**  
- Tamaño total: 16 bits = 2 bytes → **entra en una única trama**.

---

**Paso 1: Codificación Hamming (7,4)**  
Se divide en bloques de 4 bits:

1. 1111  
2. 0111  
3. 0101  
4. 0101

Cada bloque de 4 bits se codifica en 7 bits (tabla de Hamming):

- 1111 → 1111011  
- 0111 → 0111011  
- 0101 → 0101001  
- 0101 → 0101001  

Total bits codificados:  
4 bloques \(\times\) 7 bits = **28 bits**

---

**Paso 2: Añadir secuencia de inicio**  
- Secuencia de inicio: 9 bits → “010101010”  
- Trama total: \(9 + 28 = 37\) bits

---

**Resultado final**  
Trama de salida = **Inicio (9 bits) + Datos codificados (28 bits) = 37 bits**

---

## Ejercicio 10

### Enunciado
Un fabricante indica que su sistema integra un **CRC-8** con el siguiente polinomio generador:

\[
G(x) = x^8 + x^7 + x^2 + 1
\]

Plantear los pasos que se deben realizar para calcular la trama resultante, considerando que el CRC se aplica al final de la **trama 2** del ejercicio anterior.

### Resolución

**Polinomio generador en binario**: 110000101

1. Obtener la secuencia de bits de la trama 2 (0111).  
2. Codificar con H(7,4) → Resultado: 0111011.  
3. Multiplicar por \(x^8\): añadir 8 ceros al final:  
   `0111011 00000000`  
4. Dividir esta cadena por el generador binario (110000101).  
5. El **residuo** de esa división es el CRC de 8 bits.  
6. Concatenar la secuencia original codificada con el CRC calculado.

**Resultado final**  
La trama estará formada por la **codificación Hamming + 8 bits de CRC**.

---

## Ejercicio 11

### Enunciado
¿Cuántos errores pueden llegar a corregir la codificación **H(15,11)** y el **CRC-32**?

### Resolución

**Codificación H(15,11)**  
- Es un código Hamming extendido, con 11 bits de datos y 15 bits totales.  
- Puede **detectar** hasta 2 errores y **corregir** 1 error.

**Resultado**  
- **H(15,11)** corrige 1 error y detecta 2.

**CRC-32**  
- No está diseñado para corregir errores, sino para **detectarlos**.  
- Utiliza un polinomio generador de 32 bits.  
- Detecta todos los errores de 1 bit, todos los errores de ráfaga hasta 32 bits y la mayoría de errores múltiples con alta probabilidad.

**Resultado**  
- **CRC-32** no corrige errores, solo los detecta con alta fiabilidad.

---

## Ejercicio 12

### Enunciado
Se recibe la trama “1111111101011010101011” y se conoce que el protocolo está constituido por una cabecera “11111111” y que los datos están codificados con **H(14,10)**. ¿Cuáles son los datos útiles que se han transmitido?

### Resolución

**Paso 1: Identificar la cabecera**  
- La cabecera es: “11111111” (8 bits)  
- Resto de la trama: “01011010101011” (14 bits)

**Paso 2: Decodificar el bloque H(14,10)**  
- H(14,10): 14 bits totales, de los cuales 10 son datos útiles y 4 son de control.  
- Suponiendo que no hay error y que los bits están correctos, los **10 primeros bits de este bloque** tras la cabecera son los datos útiles.

**Resultado**  
Datos útiles transmitidos: `0101101010`

---

## Ejercicio 13

### Enunciado
¿A qué protocolo de la capa de enlace de datos corresponde el siguiente esquema temporal?

### Análisis del diagrama
- Se observa que cada trama enviada debe ser reconocida (**ACK**) antes de enviar la siguiente.  
- No hay transmisión simultánea de varias tramas.  
- El emisor espera la confirmación antes de enviar una nueva.

### Resultado
El protocolo es **Stop-and-Wait**.  
Se caracteriza por transmitir un solo marco a la vez y esperar el **ACK** para cada trama. También usa bits de secuencia (0 y 1) para evitar duplicados.

---

## Ejercicio 14

### Enunciado
¿Se puede aplicar el protocolo del ejercicio anterior en el siguiente escenario?

### Análisis del diagrama
- Se observa que se **pierde un ACK**.  
- El emisor retransmite la trama anterior.  
- El receptor vuelve a recibir el mismo número de secuencia.

### Conclusión
El protocolo **Stop-and-Wait** puede funcionar, pero tiene limitaciones en escenarios con pérdida de ACK:

- Retransmisiones de la misma trama.  
- Posibles duplicados si no se distingue bien el número de secuencia.

**Respuesta final**  
Sí, se puede aplicar, pero **no** es eficiente. Protocolos más robustos (Go-Back-N, Selective Repeat) son recomendados en entornos con mayor probabilidad de error.

---

## Ejercicio 15

### Enunciado
Dibujar un diagrama de ventana deslizante con un receptor con buffer para tres tramas y un transmisor que dispone de 5 tramas **desordenadas** que llegan en el orden: **0, 3, 2, 4, 1**.

### Resolución

**Supuestos**  
- Ventana del receptor: tamaño 3  
- Tramas esperadas inicialmente: 0, 1, 2  
- Orden de llegada: 0, 3, 2, 4, 1  

**Comportamiento del receptor**  
1. Llega trama 0  
   - Esperada. Se acepta.  
   - Ventana se desliza a [1, 2, 3].  
2. Llega trama 3  
   - Dentro de la ventana. Se almacena en buffer.  
   - No se entrega aún (falta 1 y 2).  
3. Llega trama 2  
   - Dentro de la ventana. Se almacena.  
   - Aún no se entrega (falta 1).  
4. Llega trama 4  
   - Fuera de la ventana actual ([1, 2, 3]). Se **descarta**.  
5. Llega trama 1  
   - Esperada. Se acepta.  
   - Se puede entregar en orden: 1 → 2 → 3.  
   - La ventana se desliza a [4, 5, 6].

**Diagrama esquemático (simplificado)**

| Tiempo | Trama recibida | Estado del buffer | Entrega al receptor | Ventana actual |
|-------:|:--------------:|:-----------------:|:-------------------:|:--------------:|
| T1     | 0             | []               | 0                  | [1,2,3]        |
| T2     | 3             | [3]              | -                  | [1,2,3]        |
| T3     | 2             | [2,3]            | -                  | [1,2,3]        |
| T4     | 4             | [2,3]            | -                  | [1,2,3]        |
| T5     | 1             | [] (se entregan 1,2,3) | 1→2→3         | [4,5,6]        |

---

## Ejercicio 16

### Enunciado
Un canal coaxial con FDM, con una tasa de transmisión de **500 Mbits/s**, una longitud media de trama de \(\frac{1}{\mu} = 12584\) bits y una tasa de llegada \(\lambda = 20000\) tramas/s:

a) ¿Qué retardo tendrá?  
b) ¿Cuántas portadoras serán necesarias si se comparte entre 256 usuarios?  
c) ¿Cuánto tiempo tarda un nodo en detectar una colisión?

### Resolución

Usamos el **modelo M/M/1** para cálculo de retardo promedio:

\[
T = \frac{1}{\mu - \lambda}
\]

Donde:  
\[
\mu = \frac{500 \times 10^6}{12584} \approx 39722.5 \quad (\text{tramas/s})
\]  
\[
\lambda = 20000 \quad (\text{tramas/s})
\]  

\[
T = \frac{1}{39722.5 - 20000} = \frac{1}{19722.5} \approx 5.07 \times 10^{-5} \text{ s} = 50.7 \,\mu \text{s}
\]

---

**(a) Retardo**  
\(\approx 50.7\) μs

**(b) Número de portadoras**  
Para FDM y 256 usuarios, cada usuario necesita una portadora.  
\[
\text{Portadoras necesarias} = 256
\]

**(c) Tiempo de detección de colisión**  
En coaxial (CSMA/CD), se basa en el tiempo de propagación. Sin datos físicos de la longitud del medio, no se puede dar un valor exacto. Aproximadamente sería:

\[
t_{\text{colisión}} \approx 2 \times t_{\text{propagación}}
\]

---

## Ejercicio 17

### Enunciado
Representar la trama “1111111101011010101011” con **codificación Manchester** y **Manchester diferencial**. Indicar las unidades y magnitudes en los ejes.

### Explicación

- **Codificación Manchester**  
  Cada bit se codifica con una transición en la mitad del intervalo de bit:
  - Un `1` se representa típicamente con una transición de nivel **bajo** a **alto** a la mitad del bit.
  - Un `0` se representa con una transición de nivel **alto** a **bajo** a la mitad del bit.

- **Codificación Manchester diferencial**  
  En la versión diferencial, lo que determina si es `1` o `0` es la **presencia o ausencia de transición** al inicio del período de bit:
  - Un `1` se indica con un cambio de nivel al comienzo del bit.
  - Un `0` se indica sin cambio de nivel al comienzo del bit.
  - La transición en la mitad del bit sirve para mantener el ritmo.

### Representación gráfica

- **Eje X**: tiempo (dividido en intervalos de bit: 1 bit, 2 bits, etc.).  
- **Eje Y**: voltaje (podría ser -V y +V, o 0 V y +V, según se defina).

Para cada bit de la secuencia `1111111101011010101011`, debes:
1. Dividir el tiempo de bit en dos mitades.
2. Determinar la forma de onda según la regla de la codificación elegida.

Por ejemplo, si tomamos la primera parte de la trama `11111111`:
- **Manchester**:
  - Para un `1`, en la primera mitad de tiempo el voltaje es bajo, y en la segunda mitad sube (transición baja→alta).
  - Se repite para cada bit `1`.

- **Manchester diferencial**:
  - Se observa si hay transición al **inicio** del bit respecto al nivel final del bit anterior.
  - Un `1` implica una transición al empezar.
  - Un `0` implica no haber transición al empezar.
  - Siempre habrá una transición en el medio de cada bit para mantener el *timing*.

El resultado final será una señal en la que cada bit está representado por dos niveles de voltaje por intervalo de bit (codificación Manchester) o por la presencia/ausencia de transición al inicio y una transición en medio (codificación Manchester diferencial).

---

## Ejercicio 18

### Enunciado
Diseñar una red Bluetooth que pueda mantener 15 nodos esclavos activos de manera simultánea.

### Resolución

En Bluetooth clásico, la **topología** principal es la **piconet**, con:
- 1 maestro
- Hasta 7 esclavos activos al mismo tiempo

Para tener **15 esclavos** activos simultáneamente, se requiere una **scatternet**, que conecta varias piconets a través de nodos puente:
- Un dispositivo puede actuar como **maestro** en una piconet y como **esclavo** en otra.

**Diseño propuesto**:
- **Piconet A**:  
  - 1 maestro + 7 esclavos  
- **Piconet B**:  
  - 1 maestro (que podría ser esclavo en la piconet A) + 8 esclavos  

Así, entre la piconet A y B, se dispondría de 15 esclavos activos, enlazados mediante al menos un **nodo puente** (que figura como esclavo en la piconet del otro maestro). De esta manera, se cumplen las limitaciones de Bluetooth y se mantiene la comunicación simultánea de todos los nodos en una scatternet.

---

**Ejercicio 19 – Enunciado:**  
¿Cuál será el rutado entre los siguientes switches si utilizan para su conexión un árbol de expansión con raíz B5?

**Explicación:**  
Un árbol de expansión (Spanning Tree) es una estructura lógica utilizada en redes de switches para evitar bucles de capa 2. Se construye a partir de un switch raíz y conecta todos los demás switches con la menor cantidad de enlaces posible, sin formar ciclos.

En este caso:

- El switch raíz es B5.
- Todos los enlaces se suponen de igual coste.
- Se eligen los caminos más cortos (menor número de saltos).
- En caso de empate, se prioriza por identificador (por ejemplo, B1 antes que B2).

**Topología del árbol con raíz B5:**
     B5
    /  \
  B3    B4
 /  \

**Razonamiento:**  
- B3 y B4 se conectan directamente a B5.
- B1 y B2 se conectan a través de B3, ya que es el primer nodo conectado a B5 y equidistante a ambos.
- El resultado es una topología libre de bucles y con conectividad completa desde la raíz.

---

**Ejercicio 20 – Enunciado:**  
Conociendo el rutado del ejercicio anterior, realizar de nuevo el árbol de expansión que se produciría si el switch B3 dejara de estar activo.

**Explicación:**  
Si el switch B3 deja de estar activo, el árbol debe reorganizarse automáticamente para mantener la conectividad entre todos los switches sin formar bucles.

**Nueva topología del árbol sin B3:**
     B5
      |
     B4
    /  \
  B1    B2

**Razonamiento:**  
- B3 ya no está disponible.
- B1 y B2, que antes dependían de B3, ahora deben conectarse mediante B4.
- B4 se mantiene como intermediario directo de B5.
- La red sigue conectada sin bucles, cumpliendo con los principios del Spanning Tree.

**Conclusión general:**  
- En el Ejercicio 19, la raíz B5 conecta directamente a B3 y B4; B1 y B2 dependen de B3.
- En el Ejercicio 20, al fallar B3, B1 y B2 se reencaminan por B4, manteniendo la estructura libre de bucles.



