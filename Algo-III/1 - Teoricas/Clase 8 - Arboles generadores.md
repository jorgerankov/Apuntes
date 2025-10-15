## Arbol generador minimo
- Defino una **funcion** X -> R **que asigna longitudes** (o pesos) **a las aristas** de T
- Se define la **longitud de T (l(T))** como _la sumatoria de todas las funciones aplicadas_
- Dado un grafo conexo G con dicha funcion definida, un **arbol generador minimo de G** es **un arbol generador de G de minima longitud**
	- Es decir, la _sumatoria_ de $\forall$ las _minimas longitudes asignadas que hacen que el arbol no deje de ser generador_, y que sea $\leq$ que l(T)

## Algoritmo de Prim
#### Lema
- Sea T = (V, X$_T$) un arbol generador de G = (V, X)
- Si e ∈ X y e $\notin$ X$_T$ y f ∈ X$_T$ una arista del ciclo de T + e
- Entonces **T'** = (V, X$_T$ ∪ {e} \ {f}) **es arbol generador de G**
#### Teorema
- El algoritmo de Prim es correcto
- Dado **un grafo G conexo determina un arbol generador minimo de G**
- El _algoritmo Prim_ es un algoritmo goloso
## Algoritmo de Kruskal
#### Proposicion
- Sea G un grafo conexo y B$_k$ = (V, X$_{T_k}$ ) el bosque generado por el algoritmo en algun momento con exactamente k aristas, 0 $\leq$ k $\leq$ n − 1, tal que **crea un subgrafo generador sin ciclos de un arbol generador minimo de G**
#### Teorema
- Dado **un grafo G conexo, determina un arbol generador minimo de G**
- Es un algoritmo goloso
