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

Veamos la ida. Si vw es puente, implica que al eliminar vw del grafo tengo mas componentes conexas que antes de eliminarlo, tal que no hay otra forma de llegar de v a w que no sea pasando por esa arista. Si vw es una arista que conecta a v con w, puedo asumir que la salida (v) va a estar en un nivel menor que la llegada (w), tal que v es padre de w. Como T es un arbol generador de G, ambos pertenecen a T, tal que v es el padre de w en T. Luego, como vw es puente, ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), ya que esto significaria que existen otros caminos posibles para llegar de v a w, implicando que entonces vw no seria puente, debido a que logro unir ambos vertices mediante otras aristas. Mas aun, un descendiente de w es aquel vertice de mayor nivel que esta conectado a w mediante alguna arista, y un ancestro de (v) es un vértice en el camino desde la raíz hasta (v) en (T), justificando asi que si existiera algun camino que pudiera unir v con w y este no tuviera a vw de por medio, entonces vw no seria puente.

Ahora, la vuelta: Si v es el padre de w en T, entonces puedo decir que v esta en algun nivel menor que w y existe un camino que los une entre si. Mas aun, existe una arista vw que los une. Si ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), entonces no existe ningun otro camino que me permita llegar de v a w, ya que si lo hubiera, este deberia pasar por un descendiente de w y por un ancestro de v, donde ambos se unen a w y a v respectivamente, haciendo que exista un camino que no contiene a vw dentro de el, y generando que vw no sea puente. Luego, como esto no puede suceder, ya que no existen aristas que unan los vertices mencionados anteriormente, vw es puente


| _Una orientación de un grafo G es un grafo orientado D cuyo grafo subyacente es G. (En otras palabras, D es una orientación de G cuando D se obtiene dando una orientación a cada arista de G). Para todo árbol DFS T de un grafo conexo G se define D(T) como la orientación de G tal que v → w es una arista de D(T) cuando: v es el padre de w en T o w es un ancestro no padre de v en T_<br><br>b) Demostrar que las siguientes afirmaciones son equivalentes<br>I) G admite una orientación que es fuertemente conexa. <br>II) G no tiene puentes. <br>III) para todo árbol DFS de T ocurre que D(T) es fuertemente conexo. <br>IV ) existe un árbol DFS de T tal que D(T) es fuertemente conexo |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
I => II) Si G admite una orientación que es fuertemente conexa, entonces G no tiene puentes. Por contradiccion, digamos que G tiene algun puente (vw), tal que 

II => I) Si G no tiene puentes, entonces G admite una orientación que es fuertemente conexa