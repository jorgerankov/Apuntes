## Notacion
- **n := | V |** := cantidad de nodos de G
- **m := | E |** := cantidad de aristas de G
- **N(v)** := vecindario del nodo v
- **d(v)** := | N(v) | = grado del nodo v
Vamos a asumir que **nuestros nodos son los numeros de 1 a n**
## Matriz de adyacencia
#### Definicion
Se representa el **grafo G = (V, E)** como **una matriz M de n × n**
Si i, j ∈ V, entonces:
- M[i][j] = M[j][i] = 0 si (i, j) $\notin$ E
- M[i][j] = M[j][i] = 1 si (i, j) ∈ E
**Complejidad espacial**: $\Theta$(n$^2$)
- La **matriz es simetrica** asi que **podriamos guardar solo una mitad**
## Lista de adyacencia
#### Definicion
Representamos el grafo **G = (V, E) como un vector** donde en la posicion correspondiente a cada nodo **vamos a almacenar un puntero a su conjunto de vecinos**
Si v,w ∈ V, entonces:
- w ∈ N[v] y v ∈ N[w] si (v,w) ∈ E
- w $\notin$ N[v] y v $\notin$ N[w] si (v,w) $\notin$ E

# Ejercicios
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

# 17
**a)** Tomemos el Digrafo D brindado. Sabemos que un Digrafo es aciclico cuando no tiene ciclos, es decir, cuando no existe mas de un camino simple para cada par de nodos. Teniendo esto en cuenta, si tomamos todos los vertices de D, vemos que tienen grado de salida mayor a 0. Esto implica que todos los nodos siempre van a estar conectados a otro nodo dentro de D mediante, como minimo, una arista, tal que, si existió una forma de llegar de un nodo a otro, al tener aristas salientes en este último, va a llegar un punto donde va a haber forma de "volver atrás" en D mediante una arista saliente (ya que va a haber un último nodo donde su arista saliente no conecta con nuevos nodos, sino que con los ya existentes). Finalmente, D tiene un ciclo, demostrado por lo mencionado.

**b)** 
```
algoritmo ciclosD
in: Digrafo D con nodos y aristas
out: booleano, True si hay ciclo, False si no

// Hago un array de n nodos visitados de D 
Visitados[n] <- False

Para cada arista (u -> v) en D:
	BFS(D, u) // Corre BFS a partir del nodo u
	// BFS encuentra ciclos automaticamente a partir de
	// su recorrido y guarda los visitados en Visitados
Si BFS encontró ciclos:
	Devolver True
Sino:
	Devolver False
```

**c)** El algoritmo ciclosD es implementado corriendo BFS 