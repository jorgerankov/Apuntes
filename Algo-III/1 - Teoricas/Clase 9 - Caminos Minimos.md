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
# Algoritmo de Dijkstra
### Teorema
Dado un grafo orientado G con pesos no negativos en las aristas, el algoritmo de Dijkstra **determina el camino minimo entre el nodo v y el resto de los nodos de G**

- Utiliza conceptualmente una cola de prioridad para guardar los vertices que estan en V \ S, donde cada vertice v se guarda junto con su valor de clave prioridad π(v) que se puede ir disminuyendo con el tiempo
# Algoritmo de Ford
##### Dado un grafo orientado G con una funcion de longitud ℓ para sus aristas y un nodo origen v
- En **todo momento de la ejecucion** del algoritmo de Ford
	1. Si π(w) < ∞ para alg´un nodo w entonces existe un recorrido R que conecta v con w y π(w) = ℓ(R)
	2. Si existe un camino minimo entre v y w entonces π(w) $\geq$ dist(v,w)
- Si **C** es **un camino entre v y w con k aristas**
	- al finalizar la iteracion k del algoritmo de Ford, 
	  π(w) ≤ ℓ(C)
- Al finalizar la iteracion k del algoritmo de Ford determina un **camino minimo** entre v y w si existe un camino minimo de v a w con a lo sumo k aristas

