# Dijkstra
### 1) a.
Observemos que, bajo la definicion de d(., .), sabemos que d(s, v) nos indica el peso del camino minimo entre s y v, y d(w, t) el peso del camino minimo entre w y t, y no existe un peso menor a los obtenidos, ya que, por definición, d(.,.) es el camino más corto de un nodo a otro. 
Luego, el peso de ellos tambien será mínimo. Sea e = (v, w) una arista que conecta a v con w con un peso c. Sabemos que, al ser una arista dirigida, v conecta con w. 

Uniendo todo lo obtenido, d(s,v) + c(v -> w) + d(w, t) es el resultado de sumar los pesos del camino minimo de s a v, el peso de la arista v -> w y el peso del camino minimo de w a t. Si combinamos un camino mínimo de s a v, la arista v -> w, y un camino mínimo de w a t, se obtiene un camino de s a t con los minimos pesos posibles que podemos obtener de esos caminos minimos, d(s,v) + c(v -> w) + d(w, t) nos devuelve como resultado el peso que obtenemos encontrando el camino minimo que comienza en s, pasa por la arista v -> w y finaliza en t, tal que  forma el camino minimo entre s y t y no existe un camino mínimo menor al obtenido, tal que encontramos d(s, t), y demostrando que v -> w es st-eficiente, como queríamos probar.

### 2)
```
algoritmo pesoDeSaT
in: digrafo G, vertices s y t, cota c
out: Arista de peso maximo entre todos los caminos 
	de s a t en G con peso <= c
	 
	dist_desde_s <- Dijkstra(G, s)
	// Dijkstra obtiene todos los pesos d(s, v), en G
	
	G_transp <- Invertir todas las aristas de G
	dist_hacia_t <- Dijkstra(G_transp, t)
	// Dijkstra obtiene todos los pesos d(v, t), en G
	
	arista_max = 0
	peso_max <- inf-
	
	Para cada arista u -> v con peso w en G:
		Si dist_desde_s[u] + w + dist_hacia_t[v] <= c: 
			Si w > peso_max:
				peso_max <- w
				arista_max <- (u, v)
	
	Retornar arista_max
```
### 3)
Ejecuto el algoritmo con una versión modificada de Bellman-Ford, que cuenta las aristas negativas usadas.
Busco guardar en cada estado la # aristas negativas usadas, tal que lo actualizo si:
- La distancia es menor,
- La distancia es igual pero usa menos aristas negativas, o
- Usa exactamente una arista negativa
```
Algoritmo caminoMinUnaNegativa
in: Digrafo G, Vertices s y t
out: Peso del camino minimo de s a t con <= 1 arista neg

	dist[s] <- 0
	negativas[s] <- 0 // #aristas negativas en el camino
	Para cada vertice v != s:
		dist[v] <- inf+
		negativas[v] <- inf+
		
	Para i = 1 hasta |V| - 1:
		Para cada arista u -> v con peso w en G:
			es_negativa <- (w < 0 ? 1 : 0)
			nuevas_neg <- negativas[u] + es_negativa
			
			Si dist[u] + w < dist[v] Y  nuevas_neg <= 1:
				dist[v] <- dist[u] + w
				negativas[v] <- nuevas_neg
			
			Si dist[u] + w == dist[v] Y nuevas_neg < 
										negativas[v]:
				negativas[v] <- nuevas_neg
	
	Si dist[t] == inf+:
		Retornar "No hay camino"
	Sino:
		Retornar dist[t]
```

### 4.
Mi planteo para este algoritmo, al tener un Grafo G con pesos positivos, y un conjunto de aristas E $\notin$ E(G) que tambien tienen peso positivo, es correr Dijkstra 2 veces, una en un grafo G sin las aristas de E $\notin$ E(G), y otra con dichas aristas. 
Luego, guardo en dos variables los pesos obtenidos, y comparo ambos pesos. Se que Dijkstra siempre me va a devolver el camino de menor peso de s a t, tal que, si al comparar los caminos obtenidos el de menor peso entre ambos es el que tiene las aristas E $\notin$ E(G), busco cuales son las aristas de ese camino que pertenecen a E $\notin$ E(G)

```
algoritmo AristasMejoranCamino
in:  Digrafo G con pesos+,
	 Vertices s y t, 
	 conjunto de aristas E not en G
out: Aristas de E que mejoran d_G(s, t)

	// Calcular distancias en G
	dist_desde_s <- Dijkstra(G, s)
	// Obtengo todos los pesos (s, v) en G
	G_transp <- Invertir todas las aristas de G
	dist_hacia_t <- Dijkstra(G_transp, t)
	// Obtengo todos los pesos (v, t) en G
	
	dist_original <- dist_desde_s[t]
	
	Si dist_original == inf+:
		Retornar E
	
	aristas_mejoran <- {}
	
	Para cada arista e = (u -> v) con peso w en E:
		camino_con_e <- dist_desde_s[u] + w + 
		dist_hacia_t[v]
		
	// Mejora?
	Si camino_con_e < dist_original:
		aristas_mejoran <- aristas_mejoran U {e} 
	
	Retornar aristas_mejoran	
```
# Algoritmo de Bellman-Ford y SRDs
### 8)
Dado un DAG (Grafo dirigido aciclico), sabemos que el digrafo contiene todos nodos que tienen, como minimo, una arista saliente y que, ademas tienen, como mucho, una sola arista incidente (es decir, una arista de entrada), ya que no tiene ciclos, por propiedades del DAG.

Esto me proporciona 3 observaciones:
- Tengo x caminos distintos en mi digrafo, de x a y, usando n nodos y m aristas,
- No existe viceversa (ya que sino habrian ciclos),
- Cada camino es unico y nada me asegura que pueda llegar a cualquier nodo desde cualquier otro
En base a esto, 
## 11) a.
Sabiendo que siempre comenzamos desde la posición i y tenemos que llegar a j, y sabiendo que pueden haber hasta n caminos distintos, donde cada camino tiene un puntaje p(i->j), y que hay mención de niveles en el enunciado (haciendo referencia a que podríamos estar trabajando con un DAG), podría, primero, realizar ordenamiento topológico del grafo para asegurarme de obtener todos los caminos de i a j de manera ordenada, para luego, con DP, guardar cada puntaje total a medidca que recorro cada uno de los caminos obtenidos en el ordenamiento topológico. Luego, retorno el puntaje n (el máximo puntaje obtenido).

```
Algoritmo puntajesConBonificaciones
in: DAG G, vertices i, j
out: Puntaje maximo de los caminos de i a j

	// Busco los caminos alcanzables desde i, descarto los q no
	alcanzan_i <- BFS/DFS desde i
	
	// Busco los caminos alcanzables desde j, descarto los q no
	G_transp <- Transponer/invertir G
	alcanzan_j <- BFS/DFS desde j
	
	// Subgrafo con los caminos de i a j
	vertices_iguales <- alcanzan_i interseccion alcanzan_j 
	
	// Conjunto de caminos de i a j
	orden_topo <- OrdenTopologico(subgrafo con vertices_iguales)
	
	// Aplico DP
	puntaje[i] <- 0
	Para cada vertice u en orden_topo:
		Para cada arista u -> v:
			puntaje[v] <- max(puntaje[v], puntaje[u] + 
			peso(u->v))
	
	Retornar puntaje[j]
```
