
# Heuristicas
- Procedimiento para obtener soluciones de **buena calidad** para un problema
- Con comportamiento **lo mas preciso posible**
- **Decisiones locales** que se trabajan a **largo plazo** a medida que vamos _usando informacion_
- Buscar una **regla sencilla** que nos permita _acercarnos a la solucion mas optima_

**A es un algoritmo $\epsilon$-aproximado** para un problema si:
$X_A − X_{OPT} \le \epsilon$ 
Donde $X$ es la condicion por la que estoy evaluando (_ej: tiempo de ejecucion de un algoritmo_)
#### Algoritmos Golosos
- Busca **construir una solucion** seleccionando en cada paso _la mejor alternativa_
- Se dan heuristicas sencillas para problemas de optimizacion
- En general permiten construir soluciones razonables

#### Problema de la mochila (BT):
```
def mochila(pesos, beneficios, capacidad):
	if len(pesos) == 0 or capacidad == 0:
		return 0;

	if pesos[0]	> capacidad[0]:
		return mochila(pesos[1:], beneficios[1:], capacidad)
	
	lo_pongo = beneficios[0] + mochila(pesos[1:], beneficios[1:], capacidad - pesos[0])
	
	no_lo_pongo = mochila(pesos[1:], beneficios[1:], capacidad)
	
	lo_mejor = max(lo_pongo, no_lo_pongo)
	
	return lo_mejor
		
pesos = [5, 3, 2, 5, 3, 1, 10]
beneficios = [15, 5, 6, 2, 5, 2, 12]
		
mochila(pesos, beneficios, 20)
```

### Problema de la mochila (Greedy):
```
import numpy as np
pesos = np.array(pesos)
beneficios = np.array(beneficios)
	
def mochila_greedy(pesos, beneficios, capacidad)
	orden = np.argsort(pesos)
	beneficio_acumulado = 0
	
	for i in range(0, len(pesos)):
		if pesos[orden[i]] > capacidad:
			return int(beneficio_acumulado)
		else:
		capacidad = capacidad - pesos[orden[ind]]
		beneficio_acumulado += beneficios[orden[i]]
	
	return int(beneficio_acumulado)
```