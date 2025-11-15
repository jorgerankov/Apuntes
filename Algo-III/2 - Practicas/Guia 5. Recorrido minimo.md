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


# 6
**Peso multiplicativo en un camino** <- multiplicatoria de los pesos de sus aristas
- Se buscan cuando se quiere encontrar una sucesion de eventos con probabilidad max/min
Modelar como un problema de camino minimo

Comienzo partiendo desde el vertice v_1 y, mediante la ejecución del algoritmo de Dijkstra sobre el digrafo G, elijo como inicio del camino a v_1 e intento llegar a v_k, siendo este último el objetivo que quiero alcanzar. Como el algoritmo de Dijkstra me asegura que siempre va a encontrar el camino de peso mínimo en cada iteración, la suma de pesos de este camino tambien va a ser la minima que se pueda encontrar. 
Pero el peso multiplicativo es mas complejo que encontrar la suma de pesos del camino minimo. 

Por ende, procedo a transformar todos los pesos originales del grafo G en sus respectivos logaritmos, tal que si una arista del grafo G tiene peso X, ahora pasa a tener peso log(X), permitiendome realizar, por propiedad de logaritmos, cuentas del estilo: log(a) + log(b) = log(a * b), y generando asi la eleccion del minimo coste logaritmico que hay dentro de cada arista de G y, ademas, formando el camino de minimo coste logaritmico posible entre v_1 y v_k, asegurandome que la multiplicacion total de los valores va a ser log(c(e_1) * c(e_2) * ... * c(e_k)) y no existe menor valor multiplicativo que este, ya que es asegurado por la ejecucion del algoritmo de Dijkstra

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
# b.
Se puede obtener puntaje infinito si y solo si:
1. Existe un ciclo alcanzable desde el nivel 1 (i)
2. Ese ciclo tiene puntaje total positivo
3. Desde ese ciclo se puede llegar al nivel n (j)
```
Algoritmo DetectarPuntajeInf
in: Grafo G con pesos, vertice inicial i y final j
out: True si es posible puntaje inf+, False sino

	alcanzables_i <- BFS/DFS(G,i)
	
	G_transp <- Invierte aristas de G
	alcanzables_j <- BFS/DFS(G_transp, j)
	
	vertices_i_j <- alcanzables_i interseccion alcanzables_j
	
	G_i_j <- Subgrafo inducido por vertices_i_j
	

	// Detectar ciclo positivo usando Bellman-Ford
	dist[v] <- 0 para todo v en G_i_j
	
	// Vemos si hay mejora en las iteraciones
	Para k = 1 hasta |v| - 1:
		Para cada arista u -> v con peso w en G_i_j:
			Si dist[u] + w > dist[v]:
				dist[v] <- dist[u] + w

	// Si aún hay mejora, existe ciclo positivo
	Para cada arista u -> v con peso w en G_i_j:
		Si dist[u] + w > dist[v]:
			Retornar True // Hay ciclo positivo
	
	Retornar False // No hay ciclo positivo
```
# 12) a.
```
Algoritmo DetectarCicloNegativo
in: Grafo G con pesos
out: True si existe ciclo negativo, False si no

	// Correr Bellman-Ford desde cualquier nodo
	v_inicial <- cualquier nodo de G
	
	// Inicializo las distancias
	dist[v_inicial] <- 0
	dist[v] <- inf+ para todo v != v_inicial
	
	// Chequeo si se reducen los pesos entre aristas
	Para i = 1 hasta |V| -1:
		Para cada arista u -> v con peso w en G:
			si dist[u] + w < dist[v]:
				dist[v] = dist[u] + w
	
	// Si vuelve a reducirse, hay ciclo
	Para cada arista u -> v con peso w en G:
		si dist[u] + w < dist[v]:
			Retonar True // Hay ciclo negativo
			
	Retornar False
```
# b.
```
Algoritmo DetectarCicloSaT
in: Grafo G con pesos, nodos s, t
out: True si existe ciclo negativo, False si no

	// Obtengo con BFS o DFS todos los caminos de s  
	caminos_de_s <- BFS/DFS(G, s)
	// Invierto el grafo para obtener caminos desde t
	G_invertida <- Transponer G
	// Obtengo con BFS o DFS todos los caminos de t  
	caminos_hacia_t <- BFS/DFS(G, t)
	
	// Me quedo solo con los vertices en el camino de s a t
	Caminos_s_t <- caminos_de_s interseccion caminos_hacia_t
	
	Grafo_s_t <- Grafo inducido por Caminos_s_t 
	
	// Correr Bellman-Ford desde s
	v_inicial <- s
	
	// Inicializo las distancias
	dist[v_inicial] <- 0
	dist[v] <- inf+ para todo v != v_inicial
	
	// Chequeo si se reducen los pesos entre aristas de s a t
	Para i = 1 hasta |V| -1:
		Para cada arista u -> v con peso w en Grafo_s_t:
			si dist[u] + w < dist[v]:
				dist[v] = dist[u] + w
	
	// Si vuelve a reducirse, hay ciclo
	Para cada arista u -> v con peso w en Grafo_s_t:
		si dist[u] + w < dist[v]:
			Retonar True // Hay ciclo negativo en el camino s a t
			
	Retornar False
	// No hay ciclos negativos en el camino de s a t
```
# 13) a.
Veamos que, dado un grafo G y un vertice origen s, podemos llegar mediante un camino minimo de s a n (siendo n cualquier nodo de G) pasando por a lo sumo k aristas (con peso w).
->) Si después de k iteraciones del algoritmo se ha calculado correctamente la distancia mínima desde s a todo vértice alcanzable, entonces fue realizado mediante un camino de a lo sumo k aristas.

El algoritmo de Bellman-Ford obtiene siempre la arista de menor peso posible en cada una de esas iteraciones, comenzando desde el nodo origen s y llegando a cada uno de los nodos alcanzables por el mismo. Teniendo esto en cuenta, y sabiendo (por nuestra hipotesis inicial) que llegamos a calcular la distancia minima desde s a todo nodo en k iteraciones del algoritmo, significa que tuvimos que hacer, en k movimientos, k elecciones de aristas para llegar a todos los nodos que queríamos. Luego, si cada elección de una arista cuesta 1 movimiento, llegar a hacer k movimientos implicará hacer un camino de a lo sumo k aristas (en el peor caso), como queríamos probar.

<-) Si tenemos un camino de a lo sumo k aristas, entonces se ha calculado correctamente la distancia mínima desde s a todo vértice alcanzable después de k iteraciones

El algoritomo de Bellman-Ford recorrió k aristas para obtener los caminos posibles. Por cada arista que recorrió tuvo que hacer 1 movimiento, tal que para un camino con k aristas hizo k movimientos. Como Bellman-Ford siempre obtiene el camino minimo partiendo de un nodo origen, sabemos que al recorrer k aristas también obtuvo el camino k-mínimo para ese nodo origen a todos los demás nodos, dando a saber que, en k iteraciones, tuvo que obtener el camino mínimo desde s a cualquier nodo.

# b.
Si no hay ciclos negativos, con n−1 iteraciones es suficiente (donde n es la cantidad de vértices) ya que, si no hay ciclos negativos, el camino minimo de s a cualquier nodo es un camino simple (sin repetir vertices), donde ese camino minimo simple tiene a lo sumo n-1 aristas.
Si el ciclo tiene peso negativo, hay contradiccion con el enunciado. Si hay un ciclo con peso positivo, implica que existe un camino que puede eliminar ese ciclo y tener un camino mas corto y con menor peso, significando que el camino encontrado no era el minimo posible. 
Luego, en el peor caso, s pasa por todos los n nodos para llegar a alguno de sus caminos minimos y, en ese caso, conectar n nodos cuesta n-1 aristas

# 14) a.
```
Algoritmo caminoMinimoLim
in: Digrafo G, nodos s,v, int i (#aristas requeridas)
out: Camino de peso minimo de s a t que usa exact. k aristas si
existe, Null si no
	
	nodos_desde_s <- BFS(G, s)
	G_transp <- Transponer G
	nodos_hasta_v <- BFS(G_transp, v)

	nodos_deSaV <- nodos_desde_s inserseccion nodos_hasta_v
	
	G_SaV <- Grafo inducido por nodos_deSaV
	
	// Genero todos los caminos minimos con 
	// inicio en s e inicio en v
	total_cam_min_s: BellmanFord(G_SaV, s)
	total_cam_min_v: BellmanFord(G_SaV, v)
	
	// Me quedo con todos los caminos minimos que coincidan
	total_caminos_SaV <- total_cam_min_s inter total_cam_min_v
	
	max_peso = 0
	para cada j entre total_caminos_SaV:
		si |total_caminos_SaV[j]| == i:
			para cada k entre total_caminos_SaV[j] con peso c:
				total_peso_k <- total_peso_k + c
			max_peso <- max(max_peso, total_peso_k)
			
	Retornar max_peso
	
```
