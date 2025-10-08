# Arboles
Son **grafos conexos sin circuitos simples**
### Dado un grafo G = (V, X):
1) **G es un arbol**
2) Existe exactamente **un camino** entre **todo par de nodos**
3) G **es conexo**, pero **si se quita cualquier arista a G** queda **un grafo no conexo**
	- _Toda arista es puente_
4) G es un grafo **sin circuitos simples** y _m = n − 1_
5) G es conexo y _m = n − 1_


***Una hoja es un nodo de grado 1***

### Lemas
- ##### Lema 0
	- _G = (V, X) un grafo, v,w ∈ V dos vertices diferentes_
	- Existen _2 caminos distintos entre estos dos veertices_ entonces **hay un ciclo en G**
- ##### Lema 1
	- _G = (V, X) un grafo conexo y e ∈ X_
	- G − e es **conexo** <=> **e pertenece** a un **circuito simple de G**
- ##### Lema 2
	- Todo _arbol no trivial_ tiene **al menos dos hojas**
- ##### Lema 3
	- Sea G = (V, X) arbol. Entonces m = n − 1


## Arboles enraizados
Arboles que **tienen un vertice distinguido** que llamamos ***raiz***
### Propiedades
- Explicitamente queda _definido_ un **arbol dirigido**
- ***Nivel*** de un vertice = La **distancia** de **la raiz a ese vertice**
- ***Altura h*** = el **maximo nivel** de sus **vertices**
- ***Vertices internos*** = Aquellos que no son ni hojas ni la raiz
- ***Arbol m-ario*** = Cuando $\forall$ sus **vertices internos** tienen **grado** a lo sumo **m+1** y su **raiz** a lo sumo **m**
- ***Arbol exactamente m-ario*** = Cuando $\forall$ sus **vertices internos** tienen grado **m+1** y su **raiz m**
- ***Arbol balanceado*** = Si $\forall$ sus hojas estan a nivel h o h − 1
- ***Arbol balanceado completo*** = si $\forall$ sus hojas estan a nivel h
- ***Relacion padre-hijo*** = dos _vertices adyacentes_, con el padre el **vertice de menor nivel**
### Teorema
- Un arbol **m-ario** de **altura h** tiene a lo sumo **m$^h$ hojas**
	- Alcanza esta cota si es un _arbol exactamente m-ario balanceado completo con h $\geq$ 1_
- Un arbol **m-ario con l hojas** tiene h $\geq$ \[log$_m$ l\] 
- Si T es un arbol **exactamente m-ario balanceado no trivial** entonces h = \[log$_m$ l\]

## Arboles generadores (AG)
Es un **subgrafo generador** (que _tiene el mismo conjunto de vertices_) de G **que es arbol**
### Teorema
- Todo **grafo conexo tiene** (al menos) un **arbol generador**
- G tiene un **unico arbol generador** <=> **G es arbol**

## Recorrido de arboles, grafos o digrafos
Para hacerlo de una forma ordenada y sistematica, se siguen dos ordenes:
- #### A lo ancho (Breadth-First Search - BFS)
	- **Comienza** por la **raiz** y se **visita cada vertice** en un nivel **antes de pasar al siguiente** nivel
- #### En profundidad (Depth-First Search - DFS)
	- **Comienza** por la **raiz** y se **explora cada rama lo mas profundo posible** antes de retroceder
- 