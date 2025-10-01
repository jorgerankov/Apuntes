 - Modelan **relaciones entre vertices**
 - Representa **problemas de la vida real** que consideran una red como _estructura subyacente_
### <u>Que es un Grafo G = (V, X)</u>
 Es un **par de conjuntos**,
 - **V** _es un conjunto de puntos/nodos/vertices_ 
 - **X** es un _subconjunto del conjunto de pares no ordenados_ de elementos distintos de V
 - Los **elementos de X** se llaman **aristas/ejes**
 - Dados v,w ∈ V, si e = (v,w) ∈ X:
	 - _v y w_ son **adyacentes** (comparten un mismo par)
	 - _e_ es **incidente** a v y w
- La **vecindad** de un vertice v, **N(v)**:
	- Es el _conjunto de los vertices adyacentes a v_
	- **N(v)** = {w ∈ V : (v,w) ∈ X}
- #### Notacion
	- n$_G$ = |V|
	- m$_G$ = |X|

### Multigrafos
Grafos en el que **puede haber varias aristas** entre **el mismo par de vertices distintos**
### Pseudografo
Grafos en el que **puede haber varias aristas entre cada par de vertices** y tambien **puede haber aristas** _(loops)_ que **unan a un vertice con si mismo**

### Grado de un vertice v en el grafo G
- **d$_G$ (v)**: es la cantidad de _aristas incidentes a v en G_
- **∆(G)**: El **maximo grado de los vertices** de G
- **δ(G)**: El **minimo grado de los vertices** de G

La **suma de los grados** de los vertices de un grafo = _2 veces el numero de aristas_: $\sum^{n}_{i = 1}$d(v$_i$) = 2m
- Para todo grafo, la cantidad de vertices que tienen grado impar es par

### Grafo Completo
- Todos los vertices son **adyacentes entre si**
- K$_n$ es el **grafo completo** de n vertices

