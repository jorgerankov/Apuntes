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

### <u>Multigrafos</u>
Grafos en el que **puede haber varias aristas** entre **el mismo par de vertices distintos**
### <u>Pseudografo</u>
Grafos en el que **puede haber varias aristas entre cada par de vertices** y tambien **puede haber aristas** _(loops)_ que **unan a un vertice con si mismo**

### <u>Grado de un vertice v en el grafo G</u>
- **d$_G$ (v)**: es la cantidad de _aristas incidentes a v en G_
- **∆(G)**: El **maximo grado de los vertices** de G
- **δ(G)**: El **minimo grado de los vertices** de G

La **suma de los grados** de los vertices de un grafo = _2 veces el numero de aristas_: $\sum^{n}_{i = 1}$d(v$_i$) = 2m
- Para todo grafo, la cantidad de vertices que tienen grado impar es par
### <u>Grafo Completo</u>
- Todos los vertices son **adyacentes entre si**
- K$_n$ es el **grafo completo** de n vertices
### <u>Complemento de un Grafo G$^c$ = (V, X)</u>
- Tiene el **mismo conjunto de vertices** que G
- Tiene todos los vertices que **no son adyacentes en G**
### <u>Recorridos, caminos, circuitos y ciclos</u>
- ***Recorrido***: 
- ***Camino***: Un recorrido que **no pasa dos veces por el mismo vertice**
- ***Seccion***: 
- ***Circuito***: Un recorrido que **empieza y termina en el mismo vertice**
- ***Ciclo***: Un circuito de **3 o mas vertices que no pasa dos veces por el mismo vertice**
### <u>Longitud: l(P)</u>
Es la **cantidad de aristas que tiene** un _recorrido P_
### <u>Distancia d(v,w)</u>
- Es la **longitud del recorrido mas corto** entre _dos vertices v y w_
- **d(v,w) = ∞** si _no existe recorrido entre v y w_
- $\forall$ vertice v, **d(v, v) = 0**
- Si un _recorrido P entre v y w_ tiene **longitud d(v,w), P debe ser un camino**
- #### Propiedades ($\forall$ u, v, w pertenecientes a V)
	- d(u, v) $\geq$ 0 y d(u, v) = 0 si y solo si u = v
	- d(u, v) = d(v, u)
	- d(u,w) $\leq$ d(u, v) + d(v,w)
### <u>Subgrafos</u>
- H es un **subgrafo generador de G** si H ⊆ G y V$_G$ = V$_H$
- **Subgrafo inducido**: 