## Arbol generador minimo
- Defino una **funcion** X -> R **que asigna longitudes** (o pesos) **a las aristas** de T
- Se define la **longitud de T (l(T))** como _la sumatoria de todas las funciones aplicadas_
- Dado un grafo conexo G con dicha funcion definida, un **arbol generador minimo de G** es **un arbol generador de G de minima longitud**
	- Es decir, la _sumatoria_ de $\forall$ las _minimas longitudes asignadas que hacen que el arbol no deje de ser generador_, y que sea $\leq$ que l(T)
#### Algoritmo de Kruskal
- Genera un bosque en algun momento con exactamente k aristas0 ≤ k ≤ n − 1, tal que **crea un subgrafo generador sin ciclos de un arbol generador minimo de G**
- Dado un grafo G conexo determina un arbol generador minimo de G
- Es un algoritmo goloso
