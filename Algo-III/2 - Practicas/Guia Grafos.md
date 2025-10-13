### 7 - Intersección Máxima
_Sea G un grafo conexo. Demostrar por el contrarrecíproco que todo par de caminos simples de longitud máxima de G tienen un vértice en común_
- Supongo que en G hay dos caminos X e Y disjuntos en vértices de igual longitud
- Defino un camino R que sea más largo que ellos 
	- R = el camino mas corto (minimo) de G + |P| + |Q| = longitud R + longitud P + longitud Q

Por el contrarreciproco, tengo que ver que $\neg$Q => $\neg$P, es decir, **si existen dos caminos simples de longitud máxima que son disjuntos en vértices, entonces G no es conexo**.
Si G fuera conexo y existieran los caminos mencionados, significa que _puedo construir un camino mas largo que conecte todo entre si_ (por propiedades del grafo conexo), en este caso, mediante R. **Esto contradice que X e Y sean un par de longitud maxima del grafo G**.

Entonces, no puede existir **ningun camino que conecte un vértice de (P) con uno de (Q)** (de lo contrario, podría construir un camino más largo). Por lo tanto, (P) y (Q) están en **componentes (conexas?) diferentes** => significa que **G no es conexo** ($\neg$P)

## Representación de grafos y digrafos
#### Representación por Conjunto de Aristas
- **Notación:** G = (V, E)
    - V = V(G): conjunto de **vértices**
    - E = E(G): conjunto de **aristas**
- **Características**
	- Representación explícita de todas las conexiones
	- No consume espacio adicional más allá del tamaño del grafo
	- No asume propiedades estructurales especiales
#### Representación por Conjunto de Vecindarios
- **Notación:** G = (V, N)
    - V: conjunto de vértices
    - N: **función** que asigna a cada vértice (v $\in$ V) su conjunto de vecinos (N(v))
- **Para dígrafos:**
    - Se distingue entre:
        - **Vecindario de entrada:** vértices desde donde llegan aristas
        - **Vecindario de salida:** vértices hacia donde salen aristas
#### Convención de Numeración
- Los vértices se **enumeran desde 0 hasta (|V(G)| - 1)**
- **Ventaja:** Simplifica la indexación y el acceso a datos (útil en implementaciones computacionales)
#### Elección de Representación según el Contexto
**Grafos Generalizados (sin estructura específica):**
- **Representación preferida:** Conjunto de aristas ((V, E))
- **Razones:**
    1. No requiere espacio adicional
    2. No asume propiedades especiales del grafo

**Grafos con Estructura Específica (ej: árboles):**
- **Representación puede variar** según la estructura
- **Ejemplo para árboles:**
    - Función que asigna a cada vértice (excepto la raíz) su **único predecesor**
    - Aprovecha la propiedad de que cada nodo (salvo la raíz) tiene exactamente un padre
### 14 - RepresentaGrafos
a) _N se representa con una secuencia (vector o lista) que en cada posición v tiene el conjunto N(v) implementado sobre una secuencia (lista o vector). Cada vértice es una estructura que tiene un índice para acceder en O(1) a N(v). Esta representación se conoce comúnmente como lista de adyacencias._
```
N = [N(v), N(v), ..., N(v)]

N(v) asigna a cada vértice (v en V) su conjunto de vecinos
N(v) = [vecino1, vecino2, ..., vecino_n]

```