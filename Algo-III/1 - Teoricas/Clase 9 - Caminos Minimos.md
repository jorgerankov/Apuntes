Sea G = (V, X) un grafo, ℓ : X -> R una funcion de peso para las aristas de G
## Definiciones
#### Longitud de un recorrido R
- La **longitud** entre dos nodos v y u es la **suma de las longitudes de las aristas del camino R**
	- ℓ(R) = $\sum_{e \in R}$ ℓ(e)
#### Recorrido Minimo R$^0$
- Un recorrido minimo entre u y v **es un recorrido entre u y v tal que ℓ(R$^0$) = min$\{$ℓ(R)** | R un recorrido entre u y v$\}$ 
- **Si un recorrido minimo** entre un par de nodos **es un camino** entonces se lo llama como **camino minimo** entre ese par de nodos
- La _existencia de recorridos minimos_ es _equivalente a la existencia de caminos minimos_
- _Puede haber varios caminos minimos_
#### Distancia
- La distancia entre u y v, _dist(u, v)_ =
	- la longitud de un camino minimo entre u y v en caso de existir algun camino entre u y v
	- $\infty$ caso contrario  
# <u>Algoritmo de Dijkstra</u>
### Teorema
Dado un grafo orientado G con pesos no negativos en las aristas, el algoritmo de Dijkstra **determina el camino minimo entre el nodo v y el resto de los nodos de G**

- Utiliza conceptualmente una cola de prioridad para guardar los vertices que estan en V \ S, donde cada vertice v se guarda junto con su valor de clave prioridad π(v) que se puede ir disminuyendo con el tiempo
# <u>Algoritmo de Belmand-Ford</u>
### Teorema
Dado un grafo orientado G sin ciclos de longitud negativa alcanzables desde v, el algoritmo de Ford **determina un camino minimo entre el nodo v y cada nodo alcanzable desde v**
##### Dado un grafo orientado G con una funcion de longitud ℓ para sus aristas y un nodo origen v
- En **todo momento de la ejecucion** del algoritmo de Ford
	1. Si π(w) < ∞ para alg´un nodo w entonces existe un recorrido R que conecta v con w y π(w) = ℓ(R)
	2. Si existe un camino minimo entre v y w entonces π(w) $\geq$ dist(v,w)
- Si **C** es **un camino entre v y w con k aristas**
	- al finalizar la iteracion k del algoritmo de Ford, 
	  π(w) ≤ ℓ(C)
- Al finalizar la iteracion k del algoritmo de Ford determina un **camino minimo** entre v y w si existe un camino minimo de v a w con a lo sumo k aristas
- _Si hubo cambio de π hasta la iteracion n inclusive en la ejecucion_ entonces **existe un ciclo de longitud negativa (c.l.n.) alcanzable desde v**
- Si existe un c.l.n. alcanzable desde v entonces **hay cambio de π en toda iteracion de la ejecucion del algoritmo de Ford**

# <u>Algoritmo de Floyd</u>
## Teorema
Determina **los caminos minimos entre todos los pares de nodos de un grafo orientado sin ciclos de longitud negativa**
## Matriz de distancias
Genera una matriz de n * n que define en cada una de sus casillas el peso que tiene una arista que une un par de vertices. 
- La distancia que une a un nodo consigo mismo vale 0
- Si un vertice **no esta unido con otro**, la distancia es $\infty$
- Sino, ponemos el **valor/peso de la arista entre los vertices ij**
> Para cada valor que esta en M$_{ij}$, M$_{ji}$, 2 $\leq$ $i$ $\leq$ n, 2 $\leq$ $j$ $\leq$ n, si la suma de ambos es menor que el adyacente de ambos, entonces reemplazamos el valor actual del adyacente por la suma que obtuvimos

#### Ejemplo
$$ \begin{array}{cc}  &A \\  &A \end{array} $$

## Lema
Al finalizar la iteracion k del algoritmo, ℓ$_{ij}$ es la longitud de los caminos minimos desde v$_i$ a v$_j$ cuyos nodos intermedios son elementos de V$_k$ = {v$_1$, ..., v$_k$}, si no existe ciclo de longitud negativa con todos sus vertices en V$_k$.

![[Pasted image 20251027153402.png]]
# <u>Algoritmo de Dantzig</u>
## Teorema
Determina **los caminos minimos entre todos los pares de nodos de un grafo orientado sin ciclos de longitud negativa**
# Lema
Al finalizar la iteracion k − 1 del algoritmo, la matriz de k × k generada contiene la longitud de los caminos minimos en el subgrafo inducido por los vertices {v$_1$, ..., v$_k$ } sin ciclos de longitud negativa

![[Pasted image 20251027153518.png]]