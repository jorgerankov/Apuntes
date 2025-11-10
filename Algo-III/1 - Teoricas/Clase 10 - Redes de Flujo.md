# Red de Flujo
- Digrafo G = (V, E) donde
	- Cada arista e tiene una **capacidad c(e) $\geq$ 0**
	- Hay un nodo fuente **s** y un nodo final **t**
	- El flujo no puede exceder la capacidad de cada arista
	- El flujo debe conservarse en cada nodo (excepto s y t)
## Flujo
Es una función f: E -> $\mathbb{R}$ que asigna un valor a cara arista
- Hay restricción de capacidad: 0 $\leq$ f(e) $\leq$ c(e) 