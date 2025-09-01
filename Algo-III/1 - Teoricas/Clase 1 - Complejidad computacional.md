# <u>Complejidad computacional</u>
* ***T$_A$(I)*** = $\sum$ de los tiempos de ejecucion de las instrucciones hechas por el algoritmo con la instancia ***I***
* **| *I* |** = # bits necesarios para almacenar los datos de entrada de ***I*** 
* **Complejidad de un algoritmo _A_:** f$_A$(n) = max$_{I: |I| = n}$ T$_A$(I)

# <u>D&C</u>
## Su funcion:
	* Dividir un problema en subproblemas del mismo tipo
	* Resolver los problemas mas pequenos
	* Combinar las soluciones
## Caracteristicas:
	* Los subproblemas deben ser mas pequenos
	* Ser el mismo tipo de tarea
	* Dividir y combinar no tienen que ser muy costosos
## Forma general $\rightarrow$ F(X):
* Si X es *suficientemente chico*, solucionar "manualmente"
* *Sino*, 
	* Dividir X en X$_1$, X$_2$, ..., X$_k$
	* $\forall$ i $\leq$ k, hacer Y$_i$ = F(X$_i$)
	* Combinar los Y$_i$ en un Y que sea solucion para X
	* Devolver Y
## Costo de tamaño n
Se expresa como **T(n)**, que ***considera***:
* Dividir el problema en _a_ subproblemas de tamaño max. **n/c** > n$_0$
* El costo de *subdividir + unir* los resultados
* Resolver los subproblemas : _aT(n/c)_ 
	* **a** = # llamadas recursivas
	* **c** = # divisiones del problema original
	* **n** = # total de elementos
	* **b'n$^d$** = Costo de dividir en subproblemas y combinar los resultados para un problema de tamaño n
# <u>Teorema Maestro</u>
Permite resolver relaciones de recurrencia de la forma ***T(n)***:
* ***T(n)*** = **a * T(n/b) + O(n$^c$)** si _n > 1_
	*  **a** = cantidad de llamados recursivos
	-  **b** = proporcion del tamaño original con el que llamamos recursivamente 
	-  **O(n$^c$)** = costo de dividir y combinar (todo lo que no son llamados recursivos)
* ***T(n) = 1*** si _n = 1_ (caso base)

### Casos de log$_c$ (a)
- Si log$_b$ a $<$ c $\rightarrow$ **T(n) = O(n$^c$) (Primer caso)**
- Si log$_b$ a $=$ c  **T(n) = O(n$^c$ log(n)) (Segundo caso)**
- Si log$_b$ a $>$ c $\rightarrow$ **T(n) = O(n$^{log_b \space a}$) (Tercer caso)** 
## Casos de f(n)
* Si f(n) = $O$(n$^{log_c \space a-\epsilon}$) para $\epsilon$ > 0 $\rightarrow$ ***T(n) = $\Theta$(n$^{log_c \space a}$)***
* Si f(n) = $\Theta$(n$^{log_c \space a}$ log$^k$n) para algun k $\geq$ 0 $\rightarrow$ ***T(n) =  $\Theta$(n$^{log_c \space a}$ log n)***
* Si f(n) = $\Omega$($^{log_c \space a+\epsilon}$) para $\epsilon$ > 0 y _af_(n/c) < _kf_(n) para k < 1 y _n_ suficientemente grandes $\rightarrow$ ***T(n) = $\Theta$(f(n))***
# <u>Algoritmo de Karatsuba</u>(x,y)
* Si _x_ e _y_ son suficientemente chicos, multiplico "a mano" y devuelvo
* Sino,
	* Separo a _x_ en x$_1$ y x$_0$
	* Separo a _y_ en y$_1$ e y$_0$
	* Calculo m$_1$ (x$_0$y$_0$), m$_2$ (x$_1$y$_1$) y m$_3$ ((x$_0$ - x$_1$)(y$_1$ - y$_0$)) por llamadas recursivas
	* Sumar m$_2$ desplazado n *b*-bits + (m$_1$ + m$_2$ + m$_3$) desplazado n/2 *b*-bits + m$_1$ 
		* Desplazar n *b*-bits = Multiplicar por b$^n$
		* n = numero de digitos del numero mas largo
	* Retornar la suma
* ***xy = m$_2$b$^n$ + (m$_1$ + m$_2$ + m$_3$)b$^{n/2}$ + m$_1$***


## Complejidad:
* ***_T(n)_ = 3T([n/c]) + cn + c'***
	* **3T(n/c)** = 3 llamadas recursivas (m$_1$, m$_2$, m$_3$) con numeros de tamaño n/c
	* **cn** = Operaciones no recursivas (separar, sumar, desplazar) son **lineales en n = O(n)**
	* **c'** = constante = **O(1)**<br><br>
	* **a** = # llamadas recursivas = 3, 
	* **c** = # divisiones de elementos = 2, 
	* **log$_c$ a = log$_2$ 3 = 1.585**
	* **n$^{log_c \space a}$ = n$^{1.585}$**<br><br>
	* Como 1 < 1.585, tengo f(n) = O(n$^{(1.585-\epsilon)}$) donde $\epsilon$ = 0.585
	* $\rightarrow$ **T(n) = $\Theta$(n$^{log_2 \space 3}$) = $\Theta$(n$^{1.585}$)**


# Comparacion de Enfoques

|   Enfoque    | Complejidad | Descripcion              |
| :----------: | ----------- | ------------------------ |
| Fuerza bruta | O(n)        | Recorrer todo el arreglo |
|     D&C      | O(log n)    | Descartar mitades        |
### Ventajas del enfoque D&C
- Aprovecha la estructura del arreglo montaña
- Complejidad logaritmica (O(log n))
- Eficiente para arreglos grandes