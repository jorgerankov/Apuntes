# Recorridos en profundidad

| 2. _Una arista de un grafo G es puente si su remoción aumenta la cantidad de componentes conexas de G. Sea T un árbol DFS de un grafo conexo G_ |
| ----------------------------------------------------------------------------------------------------------------------------------------------- |

| c) Sea vw ∈ E(G) una arista tal que el nivel de v en T es menor o igual al nivel de w en T. Demostrar que vw es puente si y solo si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v) |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
Si el nivel de v en T es menor o igual al nivel de w en T, y v y w estan conectados entre si por vw, entonces:
- O v es ancestro de w
- O v y w estan ambos en el mismo nivel 
vw es puente <-> 