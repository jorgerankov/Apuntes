## <u>Notacion</u>
- **n := | V |** := cantidad de nodos de G
- **m := | E |** := cantidad de aristas de G
- **N(v)** := vecindario del nodo v
- **d(v) := | N(v) |** = grado del nodo v
## <u>Matriz de adyacencia</u>
#### Definicion
Grafo G = (V, E) definido como una **matriz M de n × n**
Si **i, j ∈ V**, entonces:
- M$[i][j]$ = M$[j][i]$ = $0$ si (i, j) $\notin$ E
- M$[i][j]$ = M$[j][i]$ = $1$ si (i, j) $\in$ E
### Inicializar un Grafo
```
init(cantidad de nodos, lista de aristas):
	M ← matriz de n × n con 0
	for cada arista (v,w) do
		M[v][w] ← 1
		M[w][v] ← 1
	end for
	return M
```
**Complejidad: Θ(n$^2$)**

### Chequear/agregar/eliminar arista
```
tieneArista(G, (v,w)):
	return G[v][w] == 1

agregarArista(G, (v,w)):
	G[v][w] ← 1
	G[w][v] ← 1
	return G
	
eliminarArista(G, (v,w))
	G[v][w] ← 0
	G[w][v] ← 0
	return G
```
**Complejidad: Θ(1)**
### Vecindario
El **vecindario de un vértice v** es el conjunto de todos los vértices _u_ tales que _existe una arista entre v y u_
```
vecindario(G, v):
	res ← {}
	for u ∈ V do
		if G[v][u] = 1 then
			res ← res ∪ {u}
		end if
	end for
	return res
```
**Complejidad: Θ(n)**
## <u>Lista de adyacencia</u>
#### Definicion
Grafo **G = (V, E)** definido como un vector donde en la posicion correspondiente a cada nodo **va a almacenar un puntero a su conjunto de vecinos**

Si v,w ∈ V, entonces:
- w ∈ N$[v]$ y v ∈ N$[w]$ si (v,w) ∈ E
- w $\notin$ N$[v]$ y v $\notin$ N$[w]$ si (v,w) $\notin$ E
### Inicializar una Lista de adyacencia
```
init(cantidad de nodos, lista de aristas):
	N ← arreglo de largo n
	for v ∈ 1 ... n do
	
```