## 1 - _Mergesort_
1. 
	* **Divide**: medio = len ( arr ) // 2 (calcula el punto medio)
	* **Conquer**:  
		* mitad_izq = merge_sort ( arr [: medio ])
		* mitad_der = merge_sort ( arr [ medio :])
	* **Combine**: 
		* return merge(mitad_izq, mitad_der)
		* toda la funcion merge
2. **2 subproblemas**,  mitad_izq y mitad_der
3. **Tamano n/2**, cada mitad tiene la mitad del tamano original del array
4. **Costo de combinar**:
	* **O(n)** para combinar ambas mitades, recorre ambas mitades una vez
	* Total de ops: n comparaciones + n inserciones = **O(n)**
5. **_T(n)_** = aT(n/c) + f(n) = **2T(n/2) + O(n)**
	* **2T(n/2)** = 2 llamadas recursivas de costo n/2
	* **O(n)** = costo de la funcion merge
6. log$_c$ a = log$_2$ 2 = 1 
	* n$^{log_2 \space 2}$ = n $\rightarrow$ **T(n)** = $\Theta$(n) 
	* f(n) = O(n) = $\Theta$(n) = n$^{log_2 \space 2}$ $\rightarrow$ Caso 2 del Teorema Maestro
	* **T(n)** =  $\Theta$(n$^{log_2 \space 2}$ log n) = **$\Theta$(n log n)** 

## 2 - _BusquedaBinaria_
1. 
	* **Divide**: 
		* medio = (izq + der) // 2 (calcular punto medio)
		* arr[medio] > objetivo (decide que mitad revisar)
	* **Conquer**:
		* busqueda_binaria ( arr , objetivo , izq , medio - 1)
		* busqueda_binaria ( arr , objetivo , medio + 1 , der )
	* **Combine**: 
		* return medio, pero en realidad **no hay fase de combine**
2. **Uno solo**, se elige busqueda binaria por izquierda o derecha
	* Mitad izquierda si arr[medio] > objetivo
	* Mitad derecha si arr[medio] < objetivo
3. **Tamano n/2**, en cada llamada recursiva la busqueda se reduce a la mitad
4. **O(1)** porque no hay operacion de combine, solo retorno el valor + O(1) costo de comparaciones + O(1) calculo del medio
5. **_T(n)_** = aT(n/c) + f(n) = **T(n/2) + O(1)**
6. log$_2$ 1  = 0
	- c = 2 = # divisiones de subproblemas (a mitad del rango)
	- a = 1 = # subproblemas (izq o der)
	- n$^{log_2 \space 1}$ = n$^0$ = 1 $\rightarrow$ **T(n)** = $\Theta$(1)
	- f(n) = O(1) = $\Theta$(1) = $\Theta$(n$^0$) $\rightarrow$ Caso 2 del Teorema Maestro
	- **T(n)** = **$\Theta$(n$^0$ log n)** = **$\Theta$(log n)**

## 3 - _IzquierdaDominante_
	def IzquierdaDominante(arr):
		if len(arr) <= 2:
			return sum(arr)
		
		medio = len(arr) // 2
		mitad_izq = arr[:medio]
		mitad_der = arr[medio:]
		
		suma_izq = IzquierdaDominante(mitad_izq)
		suma_der = IzquierdaDominante(mitad_der)
		
		if suma_izq > suma_der:
			return suma_izq + suma_der
		return -1

	def esMasALaIzquierda(arr):
		res = IzquierdaDominante(arr)
		
		if res != -1:
			return "Es mas a la izquierda"
		return "No es mas a la izquierda"

## 4 - _IndiceEspejo_
	def indiceEspejo(arr, inicio=1):
		if len(arr) == 1:
			if arr[0] == inicio:
				return arr[0]
			return "No existe indice espejo"
		
		medio = len(arr) // 2
		mitad_izq = arr[:medio]
		mitad_der = arr[medio:]
	
		if arr[medio] == inicio + medio:
			return arr[medio]
			
		# Sino busco si el indice es mayor que el valor de arr[medio]
		# Como es un arr estrictamente creciente, si el indice es > arr[medio]
		# Entonces el indiceEspejo estara en la mitad derecha del arr
		# si indice es < arr[medio] entonces estara en la mitad izquierda
		# O(log n) ya que siempre reviso solo una mitad (izq o der)
		
		if arr[medio] < inicio + medio:
			return indiceEspejo(arr[medio+1], inicio + medio + 1)
		else:
			return indiceEspejo(arr[:medio], inicio)

- **Funcion T(n)**: aT(n/c) + f(n) = 1.T(n/2) + O(1)
	- **T(n/2)** = Una llamada recursiva (izq o der) sobre la mitad (2) del arreglo
	- **O(1)** = Costo de comparar con indice + devolver el valor si es ==
- **Complejidad usando el Teorema Maestro**
	- log$_c$ a = log$_2$ 1 = 0 $\rightarrow$ n$^{log_2 \space 1}$ = n$^0$ = 1
	- f(n) = O(1) = O(n$^0$) = $\Theta$(n$^{log_c \space a}$) $\rightarrow$ **Caso 2 del TM**
	- **T(n) = $\Theta$(log n)**

## 5 - _PotenciaLogaritmica_
si _b es par_ -> tomo b = 2k -> a$^b$ = a$^{2k}$ = a$^k$ . a$^k$
si _b es impar_ -> b = 2k + 1 -> a$^b$ = a$^{2k + 1}$ = a . a$^k$ . a$^k$
```
potenciaLog(a, b):
	si b == 0:
		return 1
	si b == 1:
		return a
		
	mitad = potencia(a, b // 2)
	
	si b es par:
		return mitad * mitad
	sino:
		return a * mitad * mitad
```

#### Calculo de complejidad
**a** = 1 (una llamada recursiva), 
**b** = 2 (division del problema),
**f(n)** = O(1) = O(n$^0$) (devuelvo un unico resultado)

**log$_b$ a** = log$_2$ 1 = 0
O(n$^0$) = 1 -> c = 0 = log$_b$ a => **Caso 2 del Teorema Maestro**

-> O(n$^0$ log n) = **O(log n)**
## 6 -  _MaximoMontaña_
1. **Casos posibles** para arr[medio]
	* Es mayor que ambos vecinos $\rightarrow$ es el maximo
	* Es menor que el vecino izquierdo $\rightarrow$ Maximo esta en la mitad izquierda
	* Es menor que el vecino derecho $\rightarrow$ Maximo esta en la mitad derecha
2. Se divide en **1 subproblema**
	- En cada paso se *descarta una mitad* del arreglo
	- Depende de la *comparacion con vecinos*
		- Si arr[medio] < arr[medio-1] $\rightarrow$ exploro izquierda
		- Si arr[medio] < arr[medio+1] $\rightarrow$ exploro derecha
		- Sino $\rightarrow$ encontre el maximo
3. **Tamaño del subproblema**: n/2
4. Funcion **T(n)** = aT(n/c) + f(n) = **T(n/2) + O(1)**
	* T(n/2) = Una llamada recursiva sobre la mitad del arreglo
	* O(1) = Costo de comparaciones con vecinos + retornar el maximo
5. **Complejidad usando el Teorema Maestro**
	- **a = 1** (un subproblema)
	- **c = 2** (division por la mitad)
	- **f(n) = O(1)** (costo constante de comparaciones)
		* log$_c$ a = log$_2$ 1 = 0
		* n$^{log_c \space a}$ = n$^0$ = 1
		* f(n) = O(1) = O(n$^0$) = O(n$^{log_c \space a}$) = Caso 2 del Teorema Maestro
		* **T(n) = $\Theta$(n$^0$ log n) = $\Theta$(log n)**

#### Ej. de MaximoMontaña:
**[1,5,9,7,3,2,1], con Maximo = 9**
- **izq** = 0, **der** = 6 = len(arr) - 1, **medio** = 3 = (izq + der) / 2
	- arr[3] (medio) = 7, arr[2] (izq) = 9, arr[4] (der) = 3
	- 7 $\ngtr$ 9 y 7 $>$ 3 $\rightarrow$ maximo esta en mitad izquierda
- $\rightarrow$ **izq** = 0, **der** = (medio - 1) = 2, **medio** = 1
	* arr[1] (medio) = 5, arr[0] (izq) = 1, arr[2] (der) = 9
	* 5 $>$ 1 y 5 $\ngtr$ 9 $\rightarrow$ maximo esta en mitad derecha
- $\rightarrow$ **izq** = (medio + 1) = 2, **der** = 2, **medio** = 2
	- arr[2] = 9, arr[2] = 9, arr[2] = 9 $\rightarrow$ **maximo = 9 en posicion 2**

## 7 - _ComplexityQuest_
**1) T(n) = T(n − 2) + 5**
T(n) = T(n − 2) + 5 = T(n-4) + 10 = ... = _T(n - 2k) + 5k_
Cuando n - 2k = 0 -> k = n/2
-> **T(n) = T(0) + 5(n/2) = O(n)**

**2) T(n) = T(n − 1) + n**
T(n) = T(n − 1) + n = T(n - 2) + (n - 1) + n = ...
= **n + (n - 1) + (n - 2) + ... + 1 = O(n$^2$)**

 **4) T(n) = T(n − 1) + n$^2$**
 T(n) = T(n − 1) + n$^2$ = T(n - 2) + (n$^2$ - 1) + n$^2$ = ...
 n$^2$ + (n$^2$ - 1) + (n$^2$ - 2) + ... + 1 = **n veces n$^2$ = n . n$^2$ = O(n$^3$)**

**5) T(n) = 2T(n − 1)**
T(n) = 2T(n - 1) = 2$^2$T(n - 2) = 2$^3$T(n - 3) = ... = 2$^n$T(0)
= **n veces multiplicar por 2 = O(n$^2$)**

**6) T(n) = T(n/2) + n**
a = 1, b = 2, c = 1 
log$_b$ a = log$_2$ 1 = 0
Como log$_b$ a = 0, c = 1 -> _log$_b$ a < c_ -> **Caso 1 del TM**
**T(n) = O(n$^1$) = O(n)**

**7) T(n) = T(n/2) + $\sqrt{n}$**
(hacer)

**8) T(n) = T(n/2) + n$^2$**
a = 1, b = 2, c = 2
log$_b$ a = log$_2$ 1 = 0 
log$_b$ a = 0, c = 2 -> **Caso 1 del TM**
**T(n) = O(n$^1$) = O(n)**

