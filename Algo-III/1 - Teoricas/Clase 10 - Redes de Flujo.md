# Red de Flujo
- Digrafo G = (V, E) donde
	- Cada arista e tiene una **capacidad c(e) $\geq$ 0**
	- Hay un nodo fuente **s** y un nodo final **t**
	- El flujo no puede exceder la capacidad de cada arista
	- El flujo debe conservarse en cada nodo (excepto s y t)
# Flujo
Es una función f: E -> $\mathbb{R}$ que asigna un valor a cara arista
- **Restricción de capacidad**: 0 $\leq$ f(e) $\leq$ c(e) $\forall$ arista e
- **Conservación de flujo**: $\forall$ v $\neq$ s, t:
	- $\sum$(flujo entrante) = $\sum$(flujo saliente)
- **Valor del flujo**: |f| = $\sum$(flujo saliente de s)

# Grafo residual
Es el grafo G$_f$ = (V, E$_f$) que representa las capacidades disponibles en el flujo actual
#### Construcción
Para cada arista (u, v) en el grafo original:
- Si _c_f(u, v) > 0_, incluir arista (u, v) en E$_f$ 
- Si _c_f(v, u) > 0_, incluir arista (v, u) en E$_f$ 
  (arista inversa o de retroceso)
Permite **encontrar caminos aumentantes** y deshacer decisiones previas
# Camino aumentante
Es un **camino dirigido desde s hasta t** en el **grafo residual** donde todas las aristas tienen **capacidad residual > 0**
##### c_f(u,v) = c(u, v) - f(u, v) + f(v, u)
_c(u, v) - f(u, v)_ es la capacidad disponible hacia adelante
_f(v, u)_ es el flujo que podemos "deshacer" en sentido inverso

# Corte
Es una partición de los vértices V en dos conjuntos disjuntos S y T:
- s $\in$ S (la fuente está en S)
- t $\in$ T (la llegada está en T)
- S $\cup$ T = V y S $\cap$ T = $\emptyset$ 

**Capacidad del corte**: c(S, T) = $\sum$ c(u, v) $\forall$ (u, v) con u $\in$ S, v $\in$ T
**Flujo a través del corte**: f(S, T) = $\sum$ f(u, v) $\forall$ (u, v) con u $\in$ S, v $\in$ T

**Ejemplo**:
```
Red: s --> u --> v --> t

Corte 1: S = {s}, T = {u,v,t}
	Capacidad: c(s,u) + c(s,v)
	
Corte 2: S = {s,u,v}, T = {t}
	Capacidad: 

```
# Cuello de botella
Es la **capacidad residual mínima** a lo largo de un camino aumentante

**Ejemplo:**
```
Camino: s -> u -> v -> t
Capacidades residuales: 5, 2, 8
Cuello de botella = min(5, 2, 8) = 2
```

Es el **máximo flujo** que podemos enviar por ese camino **sin violar capacidades**
