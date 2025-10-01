### Notacion
- **n := | V |** := cantidad de nodos de G
- **m := | E |** := cantidad de aristas de G
- **N(v)** := vecindario del nodo v
- **d(v) := | N(v) |** = grado del nodo v
### Definicion
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
