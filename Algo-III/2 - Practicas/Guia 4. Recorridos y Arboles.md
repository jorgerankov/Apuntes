# Recorridos en profundidad

| 2. _Una arista de un grafo G es puente si su remoción aumenta la cantidad de componentes conexas de G. Sea T un árbol DFS de un grafo conexo G_ |
| ----------------------------------------------------------------------------------------------------------------------------------------------- |

| c) Sea vw ∈ E(G) una arista tal que el nivel de v en T es menor o igual al nivel de w en T. Demostrar que vw es puente si y solo si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v) |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
Si el nivel de v en T es menor o igual al nivel de w en T, y v y w estan conectados entre si por vw, entonces:
- O v es ancestro de w
- O v y w estan ambos en el mismo nivel 
vw es puente <-> al eliminar vw del grafo tengo mas componentes conexas que antes de eliminarlo.

Ida (=>): Si vw es puente, entonces v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v) 

Vuelta (<-) Si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), entonces vw es puente

Veamos la ida. Si vw es puente, implica que al eliminar vw del grafo tengo mas componentes conexas que antes de eliminarlo, tal que no hay otra forma de llegar de v a w que no sea pasando por esa arista. Si vw es una arista que conecta a v con w, puedo asumir que la salida (v) va a estar en un nivel menor que la llegada (w), tal que v es padre de w. Como T es un arbol generador de G, ambos pertenecen a T, tal que v es el padre de w en T. Luego, como vw es puente, ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), ya que esto significaria que existen otros caminos posibles para llegar de v a w, implicando que entonces vw no seria puente, debido a que logro unir ambos vertices mediante otras aristas. Mas aun, un descendiente de w es aquel vertice de mayor nivel que esta conectado a w mediante alguna arista, y un ancestro de v es aquel vertice de menor nivel que esta conectado a v por una arista, justificando asi que si existiera algun camino que pudiera unir v con w y este no tuviera a vw de por medio, entonces vw no seria puente.

Ahora, la vuelta: Si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), entonces 



entonces vw es puente