
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

#### Problema de la mochila:
```
def mochila(pesos, beneficios, capacidad):
	if len(pesos) == 0 or capacidad == 0:
		return 0;

	
pesos = [5, 3, 2, 5, 3, 1, 10]
beneficios = []		
			
```