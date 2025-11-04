# Dijkstra
### 1) a.
Observemos que, bajo la definicion de d(., .), sabemos que d(s, v) nos indica el peso del camino minimo entre s y v, y d(w, t) el peso del camino minimo entre w y t, y no existe un peso menor a los obtenidos, ya que, por definición, d(.,.) es el camino más corto de un nodo a otro. 
Luego, el peso de ellos tambien será mínimo. Sea e = (v, w) una arista que conecta a v con w con un peso c. Sabemos que, al ser una arista dirigida, v conecta con w. 

Uniendo todo lo obtenido, d(s,v) + c(v -> w) + d(w, t) es el resultado de sumar los pesos del camino minimo de s a v, el peso de la arista v -> w y el peso del camino minimo de w a t. Si combinamos un camino mínimo de s a v, la arista v -> w, y un camino mínimo de w a t, se obtiene un camino de s a t con los minimos pesos posibles que podemos obtener de esos caminos minimos, d(s,v) + c(v -> w) + d(w, t) nos devuelve como resultado el peso que obtenemos encontrando el camino minimo que comienza en s, pasa por la arista v -> w y finaliza en t, tal que  forma el camino minimo entre s y t y no existe un camino mínimo menor al obtenido, tal que encontramos d(s, t), y demostrando que v -> w es st-eficiente, como queríamos probar.

### 2)
```
algoritmo pesoSaT
in: digrafo G con pesos >= 0
	vertices s y t
	cota c
out: el mayor peso entre las aristas que pertenecen a un
	 camino de s a t cuyo peso del camino es <= c
	 
	 
```