# Currificacion
```
prod :: (Int, Int) -> Int
prod (x,y) = x * y

prod' :: Int -> (Int -> Int)
(prod' x) y = x * y
```

* Prod recibe una tupla de 2 elems
* Prod' es una funcion que toma un x de tipo Int y devuelve una funcion de tipo Int -> Int, que toma un entero y lo multiplica por x
<br>
* Prod' 2 es la funcion que duplica
* Prod' es la version **_currificada_** de prod

### Funcion curry
**curry :: ((a,b) -> c) -> (a -> b -> c)**
_(de no currificada a currificada)_
```
una forma de hacerlo:
((curry f) x) y = f (x, y)

otra forma:
curry f = \x -> \y -> f (x, y)
```

### Funcion uncurry
**uncurry :: (a -> b -> c) -> ((a, b) -> c)**
_(de currificada a no currificada)_
```
una forma de hacerlo:
uncurry f (x,y) -> f x y

otra forma:
uncurry f = \(x, y) -> f x y
```

```
triple :: Float -> Float
triple = (*) 3 ~= (*3) ~= (3*)

esMayorDeEdad :: Int -> Bool
esMayorDeEdad = (<=) 18 ~= (18<=)
```

### Funcion (.)
_Compone dos funciones_,
Ej: f . g de x -> f(g(x))
```
(.) :: (b -> c) -> (a -> b) -> (a -> c)
(.) f g = \x -> f (g x)
```

### Funcion flip
_Invierte los argumentos de una funcion_,
Ej: flip (\x y -> x - y), 1 5 = 4
```
flip :: (a -> b -> c) -> (b -> a -> c)
flip f x y = f y x ~= \x -> \y
```

### Funcion ($)
_Aplica una funcion a un argumento_
```
($) :: (a -> b) -> a -> b
($) f = f

f (g (h (j x))) == f $ g $ h $ j x 
```

### Funcion const
_Dado un valor, devuelve una funcion constante que devuelve siempre ese valor_
Ej: const 5 ''casa'' devuelve 5

```
const :: a -> b -> a
const x _ = x
```

**flip ($) 0**
```
flip ($) 0 g ~> ($) g 0 ~> g 0
```


# Listas
- **Por extension**: escribo todos sus elementos
- **Por secuencias**: Progresiones por rango
- **Por comprension**: [expresion | selectores, condiciones]
	- Ejemplo:
	```
  [(x,y) | x <- [0..5], y <- [0..3], x + y == 4]
					= [(1, 3), (2, 2), (3, 1), (4, 0)]
	```
	<br>
- **Listas infinitas**: [x..]
	- Ejemplos: 
		- multiplosDe3 = [0,3..] -> [0, 3, 6, 9..]
		- primos = [n | n <- [2..], esPrimo n] -> [2, 3, 5, 7..]


### Tipo de expresion (map, filter)
**map** :: (a -> b) -> ([a] -> [b])
**filter** :: (c -> Bool) -> [c] -> [c]

Tomamos que a = (c -> Bool) ya que asi _coinciden en dominio_

**map filter** :: [a] -> [b] = [c -> Bool] -> [ [c] -> [c] ]

Ejemplo:
```
(map filter) [esPar, esPrimo, (>3)]
= [filter esPar, filter esPrimo, filter (>3)]
```

# Recursion estructural
**g :: [a] -> b** tal que
- g [] = caso base
- g (x:xs) = caso recursivo
  
**g es recursion estructural si:**
- El _caso base_ devuelve un _valor z “fijo”_ -> no depende de g
- El _caso recursivo_ no puede usar g ni xs 
  (salvo en la parte derecha de la funcion al llamar (g xs))
- **Ventaja**: Si es estructural, se que es una funcion que termina -> No hay que demostrarlo
## Foldr
**Abstrae el esquema de recursion estructural**
```
foldr f z [] = z 
foldr f z (x : xs) = f x (foldr f z xs)
```
**foldr** :: (a -> b -> b) -> b -> [a] -> b
- Toda recursion estructural es una **instancia de foldr**

# Recursion primitiva
**g es recursion primitiva si:**
- El caso base devuelve un _valor z “fijo”_ -> no depende de g
- El _caso recursivo_ no puede usar la variable g
  (excepto en n (g xs)) -> **Si puede usar la variable xs**
- Similar a la estructural, pero permite referirse a xs
**trim con foldr**:
```
trim = foldr (\x r -> if x == ' ' then r else x)
```
no se puede escribir, probamos con **recr:**
```
trim = recr (\x xs r -> if x == ' ' them r else x:xs)
```
### recr

# Recursion iterativa
g es una funcion iterativa si:
- El _caso base_ devuelve el acumulador ac
- El _caso recursivo_ invoca inmediatamente a (g ac’ xs)
	- ac’ es el acumulador actualizado en base a su valor anterior
- **Toda recursion iterativa es una instancia de foldl**
### foldl
- es un **operador de iteracion**
Pseudocodigo:
```
funcion foldl f ac xs {
	mientras xs no es vacia { 
		ac := f ac (head xs) 
		xs := tail xs 
	}
	devolver ac
}
```


### Cuando usar foldr, foldl y foldl':
- **`foldr`**: cuando la **función puede producir resultado sin consumir toda la lista** (short-circuit) o querés **construir cosas perezosas** (como otra lista). También cuando la lista **puede ser infinita**.
<br>
- **`foldl`**: casi nunca en producción; solo si **necesitás** la pereza del acumulador por algún motivo específico.
<br>
- **`foldl'`**: para **reducciones numéricas grandes** (sumas, conteos, productos, min/max). Evita sorpresas de memoria.
# Tipos de datos algebraico
En general tiene la siguiente forma:
```
data T = 
			CBase_1 ⟨parametros⟩
			... 
			| CBase_n ⟨parametros⟩
			| CRecursivo_1 ⟨parametros⟩
			...
			| CRecursivo_m ⟨parametros⟩
```
- **Constructores base** -> no reciben parametros de tipo T
- **Constructores recursivos** ->  reciben al menos un parametro de tipo T
- **Valores de tipo T**
	- -> Se pueden construir aplicando constructores base y recursivos
	- -> Se aplican **solo esos** y un **numero finito de veces**