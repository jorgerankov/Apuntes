# Problemas de optimizacion
**Consiste en encontrar la mejor solucion dentro de un conjunto**:

- _z*_ = max f(x), o
- _z*_ = min f(x), con x ∈ S
<br>
- La funcion _f : S → R_ es la **funcion objetivo** del problema
- El conjunto _S_ es la **region factible**
- los elementos _x ∈ S_ son las **soluciones factibles**
- El valor z* ∈ R es el **valor optimo** del problema
- Cualquier solucion factible x* ∈ S tq f(x*) = z* es un **optimo** del problema

### Problemas de optimizacion combinatoria
**Su _region factible_ es un conjunto definido por consideraciones combinatorias**

# Algoritmos de fuerza bruta
**Consiste en generar todas las soluciones factibles y quedarse con la mejor**
- Suele ser facil de implementar, y es un **algoritmo exacto**: _si hay solucion, siempre la encuentra_
- El principal problema es su complejidad.
  Habitualmente, tiene una **complejidad exponencial**

# Backtracking
**Recorre todas las posibles configuraciones del espacio de soluciones de un problema computacional**
- Elimina las **configuraciones parciales** que no puedan completarse a una solucion
- Permite **descartar configuraciones antes de explorarlas**
- Analiza todas las posibles “configuraciones”, lo cual habitualmente **implica una complejidad exponencial**
<br>
### Podas
- #### Por factibilidad
	- 
- #### Por optimalidad
- Usa un vector a = (a$_1$, a$_2$, . . . , a$_n$) para _representar una solucion candidata_
- Cada a$_i$ pertenece un conjunto ordenado y finito A$_i$
- En cada paso se _extienden las soluciones parciales agregando un elemento mas_
- Las nuevas soluciones parciales son _sucesoras de la anterior_ 
```
algoritmo BT(a,k) 
	si a es solucion entonces
		procesar(a)
		retornar 
	sino
		para cada a' ∈ Sucesores(a, k)
			BT(a 0 , k + 1)
		fin para
	fin si
	retornar
```