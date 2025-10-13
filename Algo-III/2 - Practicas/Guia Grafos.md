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

N(v) = [vecino1, vecino2, ..., vecino_n] de cada v

Puedo acceder a cada N(v) en O(1) = L de adyacencias
```
1) _Inicializar la estructura a partir de un conjunto de aristas de G_:
2) _Determinar si dos vértices v y w son adyacentes_: Acceder en O(1) a N(v) + ver si w existe en la lista (recorrer n veces la lista) = O(1) + O(|V|) (en el peor caso) = O(n) temporal
3) _Recorrer y/o procesar el vecindario N(v) de un vértice v dado_: acceder a N(v) en O(1), si v tiene n vecinos, recorrer el vecindario N(v) cuesta O(d(v)) = O(d(v)) temporal
4) _Insertar un vértice v con su conjunto de vecinos N(v)_: 
	- Si N es tamaño fijo |V| = redimensionar todo N + agregar el nuevo v con su conjunto = O(|V|)
	- Si N es una LE, agregar v cuesta O(1) + agregar todo su conjunto de vecinos N(v) con d(v) elems = O(d(v))
	- Ademas, agregar v a todos los vecinos = O(d(v))
5) _Insertar una arista vw_ (asumo que v y w existen en G):
	- Acceder a N(v) en O(1) + agregar w a N(v): O(d(v)) si es un vector fijo, O(1) si es una Lista Enlazada o vector dinamico
	- Mismos casos para N(w)
	- Complejidad total: O(1) si tengo una estructura dinamica, O(d(v) + d(w)) si tengo vectores fijos
6) _Remover un vértice v con todas sus adyacencias_: 
	   - Acceder a todos los N(v) existentes (n) para remover a v de todos los N(v) = O(n)
	   - Eliminar un N(v) completo es acceder en O(1) a N(v), recorrer y eliminar cada elemento 1 por 1 = O(n)
	   - Remover el v del grafo es desconectar al v de G, al haberlo eliminado de todos los N(v) y eliminar el N(v) de v ya lo hicimos = O(1)
	   - Complejidad total temporal = O(n) 
7) _Remover una arista vw:_
8) _Mantener un orden de N(v) de acuerdo a algún invariante que permita recorrer cada vecindario en un orden dado_