# <u>Programacion Funcional</u>

- **Pregunta**
	- ->  (modelado) -> **Programa + Entrada**
		- -> (computo) -> **Salida**
			- -> (interpretacion) -> **Respuesta**

**Define funciones y las aplica para procesar informacion**
- Aplicarlas *no tiene efectos secundarios*
- misma entrada -> misma salida
- Estructuras de datos **inmutables**
<br>
- Son datos como cualquier otro
	- Se pueden **pasar como parametros**
	- **Devolver** como resultados
	- Formar **parte de estructuras de datos**
	<br>
- Esta dado por un **conjunto de ecuaciones**

# <u>Expresiones</u>
**Secuencias de simbolos que sirven para representar datos, funciones y funciones aplicadas a los datos**

**Pueden ser**
- **Constructor**: _True, False, []_
	- Es una función especial que se usa para crear valores de un tipo de datos algebraico
	- Son funciones **puras** - siempre devuelven el mismo resultado para los mismos argumentos
- **Variable**: _longitud, ordenar, x, xs_
	- Se define para que va a ser usado o se usa en el momento para saber su valor/utilidad 
- **Aplicacion de una expresion a otra**: _ordenar lista, not True, (+) 1_
	- Aplica variables a constructores $\rightarrow$ **aplicacion** de **variable** *not* a **constructor** *True*  
	<br>
- Su **aplicacion** es **asociativa a izquierda _(izquierdista)_**

# <u>Tipos</u>
- **Especificaciones que sirven para decir que invariante cumple un dato o una funcion**
- Ejemplos:
	- **99** :: Int
	- **not** :: Bool -> Bool
	- **(+)** :: Int -> (Int -> Int)
- El **tipo** de una **funcion** expresa un **contrato**
### Condiciones de tipado (bien tipado)
1. Todas las expresiones **deben tener tipo**
2. Toda variable se **debe usar** siempre con un **mismo tipo**
3. Los **dos lados de una ecuacion** deben tener el **mismo tipo**
4. El **argumento** de una funcion debe tener el **tipo del dominio**
5. El **resultado** de una funcion debe tener el **tipo del codominio**
	- Ejemplo: _not True = False, main = not 1_

- ***Solo tienen sentido los programas bien tipados***
- Convenimos en que '**->**' es **asociativo a derecha**

# <u>Polimorfismo</u>
**Son expresiones que tienen mas de un tipo**
**Se usan variables de tipo _a, b, c_ para denotar tipos desconocidos**

**Ejemplo: flip** -> flip f x y = f y x	
```
	flip (:) [2, 3] 1
		= (:) 1 [2, 3]
	equiv 1 : [2, 3]
		= [1, 2, 3]
```
	
# <u>Modelo de computo</u>
- Dada una expresion, se computa su _valor_ usando las _ecuaciones_
	- **Expresiones** -> **Valores**, 3 + 2 = 5 y 5 = 5
- Hay expresiones bien tipadas que no tienen valor (ej 1 / 0)
	- -> **se indefinen** o tienen valor **⊥**
### Ecuaciones Orientadas
- Un programa funcional esta dado por un _conjunto de ecuaciones_ que son **orientadas**
- Una ecuacion e1 = e2 se _interpreta desde_:
	- Punto de vista _**denotacional**_
		- e1 y e2 tienen el _mismo significado_
	- Punto de vista _**operacional**_
		* Computar el valor de e1 _se reduce a computar el valor de e2_
	<br>
- El lado _izquierdo_ de una ecuacion debe ser una **funcion aplicada a patrones**, donde _un patron puede ser_:
	- Una _variable_
	- Un _comodin_
	- Un _constructor aplicado a patrones_
	<br>
- El **lado izquierdo no debe tener variables repetidas**

### Evaluacion de expresiones
**Evaluar consiste en:**
1. Buscar la **subexpresion mas externa** (mas _a la izquierda_) que **coincida** con el **lado izquierdo** de una ecuacion
2. **Reemplazar** la subexpresion que coincide con el lado izquierdo de la ecuacion por la **expresion correspondiente al lado derecho**
3. **Continuar evaluando** la expresion resultante

**La evaluacion se frena si**:
- La expresion _es un constructor o un constructor aplicado_
	- Ejemplos: True, (:) 1, [1, 2, 3]
- La expresion es una _funcion parcialmente aplicada_
	- Ejemplos: (+), (+) 5
- Se alcanza un _estado de error_
	- i.e. una expresion distinta a las ecuaciones que definen a la funcion aplicada -> indefinicion o no terminacion (loop)
<br>
**(En Haskell) el orden de ecuaciones es relevante** -> si varias ecuaciones coinciden **se usa la primera**


### Funciones de orden superior
- Son la _abstraccion de un esquema_
- Puede ser seguido por _muchas funciones que hagan cosas distintas y que usen el mismo esquema_

\ = _funcion anonima_ en Haskell -> _Funcion sin nombre_


#### Fibonacci

```
fib n =
(mientras (\ (_, _, i) -> i /= 0)
	entonces (\ (x, y, i) -> (y, x+y, i-1))
	sino (0, 1, n))
	
donde a = (Int, Int, Int)`
```