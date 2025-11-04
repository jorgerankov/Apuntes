# Recorridos en profundidad


2 _Una arista de un grafo G es puente si su remoción aumenta la cantidad de componentes conexas de G. Sea T un árbol DFS de un grafo conexo G_
1) Sea vw ∈ E(G) una arista tal que el nivel de v en T es menor o igual al nivel de w en T. Demostrar que vw es puente si y solo si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v)

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
_I => II) Si G admite una orientación que es fuertemente conexa, entonces G no tiene puentes._ 
Por contradiccion, digamos que G tiene algun puente 
(vw, v -> w) que lo orientamos en el grafo G; al desconectarlo de G obtenemos 2 componentes distintas, una que contiene a v y otra que contiene a w. En el digrafo orientado, para ir de w a v, debo usar alguna arista (wv) que conecte ambas componentes entre si, pero la unica arista que teniamos fue removida, e iba de v a w, no de w a v, y no hay forma de conectarlos nuevamente. Por lo tanto, **no hay camino dirigido de (w) a (v)**, así que el dígrafo **no es fuertemente conexo** (contradicción)

_II => I) Si G no tiene puentes, entonces G admite una orientación que es fuertemente conexa_
Tomo un arbol DFS (T) de G. Defino la orientacion D(T) tal que:
- v -> w si v es padre de w en T
- w -> v si w es un descendiente de v y hay una arista de retroceso de w a v
Como G no tiene puentes, toda arista de (vw) pertenece a algun ciclo => Hay alguna arista de retroceso que "cierra" el ciclo desde algun descendiente de w hacia v o algun ancestro de v. Esto me garantiza poder "subir y bajar" en el arbol usando las aristas de retroceso. Por lo tanto, desde cualquier vértice puedo llegar a cualquier otro 

# Recorridos en anchura

| 5. ⋆Un árbol generador T de un grafo G es v-geodésico si la distancia entre v y w en T es igual a la distancia entre v y w en G para todo w ∈ V (G). Demostrar que todo árbol BFS de G enraizado en v es v-geodésico. Dar un contraejemplo para la vuelta, i.e., mostrar un árbol generador vgeodésico de un grafo G que no pueda ser obtenido cuando BFS se ejecuta en G desde v. |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
->) La ida se cumple demostrando que todo vertice w esta a la misma distancia de v tanto en G como en T
Tomemos a v como la raiz del grafo enraizado G, y ejecutemos BFS desde alli, tal que se nos devuelva un árbol BFS que, a su vez, es un árbol generador T, ya que el mismo comienza a recorrer desde la raiz hasta la ultima hoja siguiendo un recorrido determinado, y dandole una direccion a cada arista entre 2 nodos.
Si un nodo w era hijo de v en el grafo G (es decir, estaba en un nivel mayor que v, ya que v es raiz y esta en el nivel 0), al correr BFS en el Grafo logramos observar que, siguiendo el camino que conecta v con w, la cantidad de aristas + 1 coincide con la diferencia de nivel entre ambos, dando a entender que se cumple la distancia entre ambos vertices tanto en el grafo G enraizado como en el arbol BFS

->) Ejecuto BFS en (G) **desde el vértice (v)**. Esto produce un **árbol BFS (T) enraizado en (v)**.
BFS construye un árbol generador (T) de (G) que incluye todos los vértices de (G). (T) es un **subgrafo** de (G) (las aristas de (T) son aristas de (G)).
Después de ejecutar BFS desde (v), cada vértice (w) tiene un **nivel** en (T), que es la distancia desde (v) en (T).

Todo árbol BFS de (G) enraizado en (v) es (v)-geodésico.
- Sea (d_G(v, w)) la **distancia entre (v) y (w) en (G)** (longitud del camino más corto).
- Sea (d_T(v, w)) la **distancia entre (v) y (w) en (T)** (longitud del único camino en el árbol).

qvq (d_T(v, w) = d_G(v, w)) para todo (w $\in$ V(G))
Como (T) es un **subgrafo** de (G) (las aristas de (T) son aristas de (G)), cualquier camino en (T) también es un camino en (G) => la distancia en (T) no puede ser **menor** que la distancia en (G).

BFS explora los vértices en orden creciente de distancia desde (v)
Cuando BFS visita (w) por primera vez, lo hace desde un vértice (u) tal que (d_G(v, u) = d_G(v, w) - 1); BFS agrega la arista (uw) al árbol (T), por lo que d_T(v, w) = d_T(v, u) + 1
Por la propiedad de BFS, sabemos que (d_T(v, u) = d_G(v, u)), tal que d_T(v, w) = d_G(v, u) + 1 = d_G(v, w)

Por lo tanto, (T) es (v)-geodésico.

### 8)
Comienzo en la posicion 1 como indica el enunciado, tal que pueda obtener w. Como debo obtener un w arbitrario, recorrer todos los resultados mod k posibles que me permitan obtener dicho w me costará O(k). 
Recorriendo el grafo aplicando BFS, me encuentro con que visito los nodos una unica vez y los marco como visitados, quitandome posibles soluciones en caso de querer recorrerlo nuevamente para buscar otras soluciones. 
Esto me indica que, para poder obtener todas las w soluciones posibles, debo recorrer el grafo nm (vertices * aristas) veces, tal de poder encontrar todas las soluciones posibles. 
Luego, si encontré un resultado igual a w, guardo la cantidad de movimientos que hice para llegar hasta ahi. Comparando cada solucion obtenida con el mod k tal que me de w, y quedandome con la minima cantidad de movimientos realizada en cada uno obtengo la complejidad O(n) + O(knm) = O(knm)

```
Algoritmo grillaBFS
	
	pi <- posicion[x1][y1]
	objetivo = w
	res_actual = BFS(Grafo)
```