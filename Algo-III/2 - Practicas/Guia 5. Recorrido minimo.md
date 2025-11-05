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
			S
				
```