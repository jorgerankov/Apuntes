**Divide el problema en subproblemas de tamanos menores que se resuelven recursivamente**

Busca **evitar repeticiones** de un arbol de llamadas recursivas **que resuelve el mismo problema varias veces** con alguno de estos _dos esquemas_:
- Enfoque **top-down**:
	- Implementacion recursiva
	- Guarda el resultado de cada llamada recursiva en una _estructura de datos_ -> **memorizacion**
- Enfoque **bottom-up**:
	- Resuelve primero los **subproblemas mas pequenos** y _guarda todos los resultados_
