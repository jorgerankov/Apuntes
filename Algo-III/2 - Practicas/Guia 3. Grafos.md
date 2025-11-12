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
**a)** Si todos los vertices de un digrafo D tienen grado de salida > 0, entonces D tiene un ciclo.
Tomamos un vertice arbitrario v0 en D. Como d_out(v0) > 0, existe una arista v0 -> v1. Entonces, agrego v0 a la secuencia. Como d_out(v1), existe una arista v1 -> v2. Entonces, agrego v1 a la secuencia. Sigo este proceso para los n nodos de D. Como no existen n + 1 nodos, el nodo n debe apuntar a alguno de los n-1 nodos restantes de D, demostrando que existe un ciclo en D.


**b)** 
```
algoritmo ciclosD
in: Digrafo D con nodos con d_out > 0
out: booleano, True si hay ciclo, False si no

Tomo un nodo v <- cualquier nodo de D

// Hago un array de n nodos visitados de D 
Camino <- [v] 
Visitados <- {v}

Recorro los nodos vecinos de v:
	u <- ultimo vertice en camino (vecino de v)

	Elijo una arista u -> w cualquiera
	Si w esta en Visitados:
		retornar True
	Sino:
		Camino <- Camino + [w]
		Visitados <- Visitados U {w}

```

**c)** El algoritmo ciclosD es implementado corriendo BFS sobre todo el Digrafo. Como BFS recorre cada nodo y sus vecinos, y los marca dentro de una lista de booleanos si fueron visitados o no, se puede corroborar que, si un nodo aparece como visitado mientras que corre BFS, significa que ya fue visitado anteriormente. Esto, sumado a que en el enunciado se nos indica que cada nodo tiene grado de salida mayor a cero, denota que se llegó al mismo nodo de otra manera distinta a la primera, tal que existe un ciclo. Luego, el algoritmo me permite devolver True en caso de que exista un ciclo, o False si no. El algoritmo tiene complejidad O(n + m) en el peor caso. Si no tiene ciclos, BFS recorre todo el digrafo teniendo que pasar por todos los nodos (n) y aristas (m).  

**d)** Si D tiene un solo nodo, es trivial, ya que no tiene aristas salientes ni entrantes y, por ende, no tiene ciclos, tal que es aciclico. Ahora, tomemos D con un vertice con d_out{v} = 0 tal que D \ {v} es aciclico. Esto significa que v no tiene aristas salientes, tal que v no puede formar un ciclo de ninguna manera. Pero, mas aun, al removerlo de D, sigo sin ciclos, implicando que ningun nodo que quedó dentro de D tampoco forma ciclos

# 19
d(u) $\leq$ d(v) <- Grado de u es menor o igual que grado de v
N(u) <- Conjunto de vertices adyacentes a u <- N(u) **NO incluye a u**

Si G es un grafo threshold, sabemos que cada par de vertices u, v en V(G), con d(u) $\leq$ d(v), N(u) ⊆ N(v) o N[u] ⊆ N[v]. Es decir:

**a)** Gemelos: N(u) = N(v)
Mellizos: N[u] = N[v] == N(u) ∪ {u} = N(v) ∪ {v})

Sea u, v en V(G) tal que d(u) = d(v) = k
Queremos probar que u y v son mellizos o gemelos

Dado que d(u) = d(v), entonces d(u) $\leq$ d(v)
Por la propiedad de threshold:
N(u) ⊆ N(v) O N[u] ⊆ N[v]

Pero tambien, d(v) $\leq$ d(u), tal que:
N(v) ⊆ N(u) O N[v] ⊆ N[u]

Como N(u) ⊆ N(v) y N(v) ⊆ N(u), entonces N(u) = N(v)
--> u y v son gemelos

Y como N[u] ⊆ N[v] y N[v] ⊆ N[u], entonces N[u] = N[v]
--> u y v son mellizos

**b)** Si G es un grafo threshold, entonces exite un vertice de grado 0 o un vertice de grado n-1

Supongamos que G es un grafo threshold y que:
- Todo vertice tiene grado $\geq$ 1 (no hay grado 0)
- Todo vertice tiene grado $\leq$ n-2 (no hay grado n-1)
Es decir, todos los vertices tienen grado [1, n-2]

**c)** 


# 20
**a)** 
```
algoritmo aristasRepetidas
in: Conjunto C de aristas de un multigrafo G
out: Conjunto de aristas que no estan repetidas en G

// Guardo existencia de arista en un diccionario
// Para poder obtener acceso en O(1)
Para cada arista (v,w) en C: // O(n) recorrer C
	Diccionario[(v, w)] <- True

res = []

Para cada arista (v,w) en C: // O(n) recorrer C
	Si (w, v) not en diccionario: // O(1) busqueda
		res.append((v,w)) // O(1) agregar a res
		
Retornar res // Complejidad total: O(n) + O(n) = O(n)
```
**b)**
```
algoritmo repetidasDigrafo
in: Conjunto C de aristas de un digrafo D
out: Conjunto de aristas que no tienen su inversa en D

// Guardo existencia de arista en un diccionario
// Para poder obtener acceso en O(1)
Para cada arista (v,w) en D: // O(n) recorrer D
	Diccionario[(v, w)] <- True

res = []

Para cada arista (v,w) en D: // O(n) recorrer D
	Si (w, v) not en diccionario: // O(1) busqueda
		res.append((v,w)) // O(1) agregar a res
		
Retornar res // Complejidad total: O(n) + O(n) = O(n)

```