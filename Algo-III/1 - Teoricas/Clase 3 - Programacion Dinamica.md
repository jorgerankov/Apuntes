## _<u>Superposición de estados/subproblemas</u>_
Busca **evitar repeticiones** de un arbol de llamadas recursivas **que resuelve el mismo problema varias veces**
- Permite **descomponer** un problema en **subproblemas más pequeños**
- Esos subproblemas **se repiten muchas veces** al resolver el problema principal
- **La programación dinámica** aprovecha la superposición de subproblemas **almacenando los resultados** (memoization) **para no recalcularlos**
<br>
### <u>Enfoques</u>
- **top-down**:
	- Implementacion recursiva
	- Guarda el resultado de cada llamada recursiva en una _estructura de datos_ -> **memoization**
	- Si una llamada recursiva se repite, _retorna lo guardado en la estructura_
- **bottom-up**:
	- Resuelve primero los **subproblemas mas pequenos** y _guarda todos los resultados_
	- Solo necesita _almacenar la fila anterior_ de la que estamos calculando -> **No es posible con top-down**
<br>
## **<u>Soluciones por PD</u>**
- Se basa en la idea de Memoization
- Construye iterativamente soluciones a los subproblemas hasta llegar a la solucion del problema original
- Usa **logica inductiva**: Si puedo asumir que ya tengo calculadas todas las soluciones anteriores -> Como puedo usarlas para construir lo que necesito? 
#### n$_p$ completo
Recursividad de conjunto de problemas que se pueden subdividir en otro conjunto de problemas
