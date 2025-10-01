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
- δ(G) El minimo
