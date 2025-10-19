# <u>Arboles</u>
### Definicion
- **Son grafos que son conexos y no tienen ciclos ni circuitos simples**
- Es decir, **grafos que pueden ir de cualquier vertice a cualquier otro mediante algun conjunto de aristas** y ademas sus vertices **no pueden tener un mismo punto de partida y de llegada** (no se puede ir y volver al mismo vertice mediante un conjunto de aristas)
- Entre **todo par de vertices existe un unico camino simple**
- Todo **arbol tiene como cantidad de aristas** = la cantidad de vertices - 1
### Propiedades
- Si **agrego una arista** entre dos vertices de un arbol, **deja de ser un arbol** (Deja de tener el camino simple, pasa a tener un ciclo)
- **Todas las aristas de un arbol son puentes** (Si desconecto alguna, deja de ser un grafo conexo)
- En todo arbol: | V | = | A | + 1 => La cantidad de vertices es igual a la cantidad de aristas + 1
## <u>Bosque</u>
- Es un **grafo no conexo** en el cual **cada una de las componentes es un arbol**
- **Ejemplo**: Un grafo que no tiene todos sus vertices conectados entre si pero todos cumplen la propiedad de arbol por su cuenta
## <u>Arboles dirigidos</u>
- Arboles que **tienen un vertice distinguido** que llamamos ***raiz***
- Un digrafo simple **es un arbol dirigido** si **su grafo asociado** (es decir, el "grafo sin flechitas") **es un arbol dirigido**
### <u>Arbol dirigido con raiz (enraizado)</u>
- Es un arbol dirigido en el cual **el grado entrante** (positivo) **de cada vertice es igual a 1** (les llega por lo menos una arista), **excepto** por un **unico vertice con grado positivo igual a 0**, que sera _**la raiz**_ (es decir, que no le deben llegar aristas)
### <u>Otras definiciones sobre arboles</u>
- Queda _definido_ un **arbol dirigido**
#### Hoja
- Un **vertice v** de un arbol se dice **hoja cuando g(v) = 1** (el grado total de ese vertice va a ser el entrante (solo recibe una arista de otro vertice pero no le sale ninguna))
#### Vertices internos
- Son aquellos que **no son ni la raiz ni las hojas**
#### Rama
- Una **rama** es **todo camino que va desde la raiz a alguna hoja**
#### Antecesor
- v es **antecesor** de w <=> $\exists$ un **unico camino simple de v a w**
#### Sucesor
- Asimismo, w es **sucesor** de v **en el caso anterior**
#### Padre
- v es **padre** de w <=> $\exists$ **una arista de v a w**
#### Hijo
- w es **hijo** de v **en el caso anterior**
#### Hermanos
- v y w son **hermanos** <=> **tienen el mismo padre** (una misma arista tiene vertices apuntando hacia ambos)
#### Nivel de un vertice
- La **distancia** de **la raiz a ese vertice**
- El _nivel de la raiz es 0_: n(r) = 0
- _Cada vertice tiene un nivel mas que su padre_: Si p es padre de v --> n(v) = n(p) + 1
- La **altura** de un arbol es el mayor nivel posible (el ultimo)
### Lemas
- ##### Lema 0
	- Sea _G = (V, X) un grafo, v,w ∈ V dos vertices diferentes_
	- Existen _2 caminos distintos entre estos dos veertices_ entonces **hay un ciclo en G**
- ##### Lema 1
	- Sea _G = (V, X) un grafo conexo y e ∈ X_
	- G − e es **conexo** <=> **e pertenece** a un **circuito simple de G**
- ##### Lema 2
	- Todo _arbol no trivial_ tiene **al menos dos hojas**
- ##### Lema 3
	- Sea G = (V, X) arbol. Entonces m = n − 1
- ##### Corolario 1
	- Sea _G = (V, X) sin circuitos simples_ y _c componentes conexas_. Entonces _m = n − c_
- ##### Corolario 2
	- Sea _G = (V, X) con c componentes conexas_. Entonces _m ≥ n − c_
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

# <u>Recorrido de arboles</u>
### Subarbol
- Sea G = (A, V, \) un arbol con raiz r
- Sea v $\in$ V, se llama **subarbol con raiz v**
- Y se indica **T(v)** al **arbol que consta de v, todos sus descendientes y las aristas entre ellos**
### Recorridos
- Significa **nombrar a todos los vertices del arbol siguiendo un determinado orden**
### Definiciones recursivas
#### Orden previo (preorder)
- Lo primero que se nombra es la raiz
- Recorre el subarbol izquierdo en este mismo orden
- Finalmente, hace lo mismo con el subarbol derecho
- En cada subarbol, paso la raiz -> sub. izq -> sub. der
#### Orden simetrico (inorder)
- Recorre el subarbol izquierdo en este mismo orden
- Nombra la raiz
- Recorre el subarbol derecho en este mismo orden
- En cada subarbol, paso el sub. izq -> raiz -> sub. der
#### Orden posterior (postorder)
- Recorre el subarbol izquierdo en este mismo orden
- Recorre el subarbol derecho en este mismo orden
- Nombra la raiz
- En cada subarbol, paso el sub. izq -> sub. der -> raiz 

### Ordenes de recorrido:
- #### En profundidad (DFS)
	- Es un **algoritmo recursivo** que sigue la **idea de backtracking** para poder recorrer todos los nodos
	- **Comienza** por la **raiz** y **se explora cada rama lo mas profundo posible antes de retroceder**
	- Recorro todos los nodos una sola vez y reviso las aristas tambien una sola vez => O(m + n)
	- **LISTA** implementada como **pila**
- #### A lo ancho (BFS)
	- Tambien vamos a recorrer todos los nodos pero en lugar de recorrer en profundidad **va recorriendo a lo ancho**
	- La idea del algoritmo es arrancar en algun nodo y recorrer todos sus vecinos, luego los vecinos de sus vecinos...
	- **Comienza** por la **raiz** (nivel 0) y **se visita cada vertice en un nivel antes de pasar al siguiente**
	- **LISTA** implementada como **cola**
#### DFS p/ enumerar $\forall$ los vertices de un digrafo
- **tree edges**: arcos que forman el bosque DFS
- **backward edges**: van hacia un ancestro. 
- **forward edges**: van hacia un descendiente. 
- **cross-edges**: van hacia a otro arbol (anterior) del bosque o a otra rama (anterior) del arbol

##### Para grafos, solamente existen aristas _tree edges_ y _back edges_



## <u>Arbol n-ario</u>
- Arbol donde **cada vertice puede tener a lo sumo n hijos**
	- Ejemplo: n = 2 => arbol binario
### Arbol n-ario regular
- **Todos los vertices tienen la misma cantidad de hijos**, salvo las hojas que no tienen hijos
### Arbol n-ario regular pleno/completo
- Si **ademas de ser n-ario regular**, **todas las hojas se hallan en el mismo nivel**
