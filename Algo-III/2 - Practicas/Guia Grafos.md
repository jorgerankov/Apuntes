### 7 - Intersección Máxima
_Sea G un grafo conexo. Demostrar por el contrarrecíproco que todo par de caminos simples de longitud máxima de G tienen un vértice en común_
- Supongo que en G hay dos caminos X e Y disjuntos en vértices de igual longitud
- Defino un camino R que sea más largo que ellos 
	- R = el camino mas corto (minimo) de G + |P| + |Q| = longitud R + longitud P + longitud Q

Por el contrarreciproco, tengo que ver que $\neg$Q => $\neg$P, es decir, **si existen dos caminos simples de longitud máxima que son disjuntos en vértices, entonces G no es conexo**.
Si G fuera conexo y existieran los caminos mencionados, significa que _puedo construir un camino mas largo que conecte todo entre si_ (por propiedades del grafo conexo), en este caso, mediante R. **Esto contradice que X e Y sean un par de longitud maxima del grafo G**.

Entonces, no puede existir **ningun camino que conecte un vértice de (P) con uno de (Q)** (de lo contrario, podría construir un camino más largo). Por lo tanto, (P) y (Q) están en **componentes (conexas?) diferentes** => significa que **G no es conexo** ($\neg$P)