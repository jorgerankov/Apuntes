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
Arboles que tienen un vertice distinguido que llamamos ra´ız