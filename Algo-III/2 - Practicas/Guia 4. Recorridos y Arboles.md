# Recorridos en profundidad


### 2) c.

Si el nivel de v en T es menor o igual al nivel de w en T, y v y w estan conectados entre si por vw, entonces:
- O v es ancestro de w
- O v y w estan ambos en el mismo nivel 
vw es puente <-> al eliminar vw del grafo tengo mas componentes conexas que antes de eliminarlo.

Ida (=>): Si vw es puente, entonces v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v) 

Vuelta (<-) Si v es el padre de w en T y ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), entonces vw es puente

Veamos la ida. Si vw es puente, implica que al eliminar vw del grafo tengo mas componentes conexas que antes de eliminarlo, tal que no hay otra forma de llegar de v a w que no sea pasando por esa arista. Si vw es una arista que conecta a v con w, puedo asumir que la salida (v) va a estar en un nivel menor que la llegada (w), tal que v es padre de w. Como T es un arbol generador de G, ambos pertenecen a T, tal que v es el padre de w en T. Luego, como vw es puente, ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), ya que esto significaria que existen otros caminos posibles para llegar de v a w, implicando que entonces vw no seria puente, debido a que logro unir ambos vertices mediante otras aristas. Mas aun, un descendiente de w es aquel vertice de mayor nivel que esta conectado a w mediante alguna arista, y un ancestro de (v) es un vértice en el camino desde la raíz hasta (v) en (T), justificando asi que si existiera algun camino que pudiera unir v con w y este no tuviera a vw de por medio, entonces vw no seria puente.

Ahora, la vuelta: Si v es el padre de w en T, entonces puedo decir que v esta en algun nivel menor que w y existe un camino que los une entre si. Mas aun, existe una arista vw que los une. Si ninguna arista de G\ {vw} une a un descendiente de w (o a w) con un ancestro de v (o con v), entonces no existe ningun otro camino que me permita llegar de v a w, ya que si lo hubiera, este deberia pasar por un descendiente de w y por un ancestro de v, donde ambos se unen a w y a v respectivamente, haciendo que exista un camino que no contiene a vw dentro de el, y generando que vw no sea puente. Luego, como esto no puede suceder, ya que no existen aristas que unan los vertices mencionados anteriormente, vw es puente


### 3) b.
_I => II) Si G admite una orientación que es fuertemente conexa, entonces G no tiene puentes._ 
Por contradiccion, digamos que G tiene algun puente 
(vw, v -> w) que lo orientamos en el grafo G; al desconectarlo de G obtenemos 2 componentes distintas, una que contiene a v y otra que contiene a w. En el digrafo orientado, para ir de w a v, debo usar alguna arista (wv) que conecte ambas componentes entre si, pero la unica arista que teniamos fue removida, e iba de v a w, no de w a v, y no hay forma de conectarlos nuevamente. Por lo tanto, **no hay camino dirigido de (w) a (v)**, así que el dígrafo **no es fuertemente conexo** (contradicción)

_II => I) Si G no tiene puentes, entonces G admite una orientación que es fuertemente conexa_
Tomo un arbol DFS (T) de G. Defino la orientacion D(T) tal que:
- v -> w si v es padre de w en T
- w -> v si w es un descendiente de v y hay una arista de retroceso de w a v
Como G no tiene puentes, toda arista de (vw) pertenece a algun ciclo => Hay alguna arista de retroceso que "cierra" el ciclo desde algun descendiente de w hacia v o algun ancestro de v. Esto me garantiza poder "subir y bajar" en el arbol usando las aristas de retroceso. Por lo tanto, desde cualquier vértice puedo llegar a cualquier otro 

# Recorridos en anchura

### 5
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
Recorriendo el grafo aplicando BFS desde (x1, y1, v1) obtengo todos los estados (x,y,w) donde (x,y) son cualquier posicion y w es mi valor objetivo.

```
Algoritmo grillaBFS
in: grilla[n][m], 
	posicion_inicial (x1,y1), 
	valor inicial v1,
	objetivo w
out: minima cantidad de movimientos para obtener w

	Inicializacion BFS
		Cola <- {}
		visitado <- {}
		distancia <- {}
		
		estado_inicial <- (x1,y1,v1)
		encolar(cola, estado_inicial)
		visitado.agregar(estado_inicial)
		distancia[estado_inicial] <- 0
	BFS
		resultado_minimo <- inf+

		mientras cola no este vacia:
			(x, y, v) <- desencolar(cola)
			dist_actual <- distancia[(x,y,v)]
			
		distancia_actual <- distancia[(x,y,v)]
		
		si v == w:
			resultado_minimo <- min(resultado_minimo,
			dist_actual)
			continuar
		
		Para c/vecino (x', y') adyacente a (x, y):
			valor_destino <- grilla[x'][y']
			v_nuevo <- (v + valor_destino) mod k
			estado_nuevo <- (x', y', v_nuevo)
			
			Si estado_nuevo not in visitado:
				visitado.agregar(estado_nuevo)
				distancia[estado_nuevo] <- dist_actual 
				+ 1
				encolar(cola, estado_nuevo)
	
	Retornar resultado_minimo	
```

# AGM, Camino minimax y maximin
### 12) a.
Trabajo mi algoritmo en base a recorrer el grafo con el algoritmo de Prim, modificando los valores de las aristas del grafo original. Multiplico por -1 todos los valores de las aristas, tal que Prim obtenga el mínimo valor posible en cada pasada. Prim me asegura obtener un grafo conexo, tal que, al final de su recorrido, voy a obtener un grafo conexo con valores de aristas mínimos. Luego, vuelvo a multiplicar por -1, para obtener los valores originales de las aristas, teniendo así un árbol generador con pesos máximos en sus aristas (el peso mínimo de un valor negado es el máximo de un valor positivo). Recorro cada arista del AGM para obtener el menor peso posible, que será el ancho de banda. Finalmente, devuelvo el ancho de banda obtenido.
```
Algoritmo redPrim
in: Grafo G =(V, E) con pesos positivos
out: Ancho de banda (k maximo tal que Gk es conexo)

	Para cada arista e en G:
		peso[e] <- peso[e] * (-1) // invierto valor
	
	AGM <- Prim(G) // Encuentro AGM minimo de pesos-
	Para cada arista e en AGM:
		peso[e] <- peso[e] * (-1) // restauro valor
	
	ancho_banda <- inf+
	Para cada arista e en AGM:
		Si peso[e] < peso_minimo:
		peso_minimo <- peso[e]
	retornar ancho_banda
```
### 14) a.
Sea T un AGM cualquiera de G, definimos qT(e) = 0 si e en T, y 1 si e no en T.
Sea T' el arbol obtenido por Kruskal con orden de selección usando q_T
Quiero ver que T' = T mostrando que toda arista de T es elegida por Kruskal, y que ninguna arista de T es elegida por Kruskal 

En cada iteracion de Kruskal se elige una arista de peso minimo que no crea un ciclo.

Sea e $\in$ T una arista que aun no fue elegida. Si e puede ser agregada sin crear un ciclo en T', entonces es considerada. Kruskal busca la arista de peso minimo. Como T es un AGM, e tiene peso minimo o igual entre las aristas no procesadas que no crean ciclo. Si hay empate con otra arista e $\notin$ T del mismo peso:
- q$_T$(e) = 0
- q$_T$(e') = 1
- Kruskal elige la de minima prioridad: e (con prioridad 0)
Por lo tanto, Kruskal selecciona e.

Sea e $\notin$ T una arista cualquiera. Como T es un arbol generador, agregar e a T crea un ciclo C. Sea f $\in$ T una arista en ese ciclo C.
Como e $\notin$ T, p(e) $\geq$ p(f):
- Si p(e) > p(f), Kruskal procesa f antes que e. Cuando f es procesada, se agrega a T'. Cuando e es considerada, crea el ciclo con f, tal que Kruskal descarta e.
- Si p(e) = p(f), ambas tienen el mismo peso, pero q$_T$(f) = 0 y q$_T$(e) = 1, ya que una pertenece a T' y otra no. Cuando Kruskal debe elegir entre ellas (si llega la opción de elegir entre ambas), elige f (prioridad 0) sobre e (prioridad 1). Luego, Kruskal no selecciona e.

Finalmente, T' contiene exactamente las aristas de T.
Como ambos son arboles generadores con las mismas |V-1| aristas, T' = T.
Por lo tanto, Kruskal con orden de selección obtiene T como resultado.

# 14) b.
Si los pesos de G son todos distintos, entonces G tiene un único árbol generador mínimo.

Sea T un AGM generado por Kruskal a partir de G, con G teniendo n aristas de pesos distintos entre si {1, ..., n}. Sabemos que Kruskal siempre elige los minimos pesos entre todas las aristas existentes dentro de un grafo, tal que siempre va a obtener el AGM de minimo peso posible. Como todos los pesos son distintos entre si, Kruskal siempre va a elegir una arista con peso minimo que no tiene comparacion de peso con otra arista. Ademas, tampoco habrá que decidir una elección por prioridad, ya que no hay que buscar comparación entre 2 aristas del mismo peso.

Ahora, observemos por contradicción que, dado un Grafo con n aristas, y siendo v, w, 2 aristas con mismo peso, y son las de minimo peso de todo el grafo, podemos obtener un único AGM. 

Corriendo Kruskal en el grafo, asignemos primero qT(v)=0 y qT(w)=1, tal que, al momento de tener que elegir entre ambas aristas para generar el AGM, elijamos v, ya que tiene minima prioridad en comparacion a w. Esto nos devolverá un AGM, que lo denominaremos T, de peso mínimo posible con todas las aristas con pesos distintos.
Ahora, corramos nuevamente Kruskal, pero asignando qT(w)=0 y qT(v)=1, tal que Kruskal seleccione a w al momento de armar el AGM, ya que w tiene minima prioridad en comparacion a v. Tambien obtenemos un AGM, que lo denominaremos T', de peso minimo posible con todas sus aristas con pesos distintos, y a su vez distinta a T. Luego, ambas tienen todas aristas de peso mínimo y peso distinto entre sí. Pero T != T', ya que un AGM contiene a v y otro a w, demostrando que G, al no tener todos pesos distintos, puedo obtener mas de un AGM. Luego, queda demostrado que para obtener un unico AGM, todos los pesos de G deben ser distintos entre si.

# 18
v <- Un vertice que alcanza todos los otros vertices de D
T <- Un AG que se obtiene al correr DFS desde v
Los vertices hermanos de T estan ordenados tal que u aparece antes que su hermano w <- u fue descubierto antes que w por DFS
(El vecindario de u fue procesado antes que el de w)
S <- Secuencia que se obtiene al revisar T en sentido postorder

# 19
**a)** Para determinar si existe un unico camino entre v y w, primero chequeo si el grafo G es un arbol directamente. En caso que lo sea, ya me aseguro que existe un unico camino entre v y w. Caso contrario, recorro G ejecutando DFS desde v, tal que me devuelva un arbol con un unico camino arbitrario entre v y w, pero ademas me devuelva los back edges detectados en G. Luego, verifico si algun back edge (u, x) cumple que: u es descendiente de w y x es antepasado de w en el arbol DFS. Si encuentro uno, entonces hay multiples caminos de v a w. Sino, hay un unico camino de v a w.

**b)** El algoritmo me permite procesar el grafo G con costo O(n + m). A medida que lo proceso, creo un diccionario de pares de nodos, donde la construccion del mismo es O(n + m), y guardo cada par de nodos dentro. Recorro cada arista una sola vez, y la consulta (if (u, v) in dict: ...) tiene costo O(1) tiempo.

# 20
F <- Bosque generador de un grafo G pesado
c <- Funcion E(G) -> Reales, que le da peso a c/ arista de G
vw es segura <- v y w pertenecen a arboles $\neq$ de F
vw es candidata p/ un árbol T de F que contiene a v <- vw es segura y c(vw) $\leq$ c(xy) $\forall$ arista segura xy tq x $\in$ T