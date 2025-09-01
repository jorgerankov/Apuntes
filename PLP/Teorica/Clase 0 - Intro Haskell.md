# <u>Tipos</u>

### Sinonimo de Tipos
- Define un **alias** usando una declaracion como:
	- **type** _NombreNuevo = NombreOriginal_
- Agrega **claridad** a su uso:
	- **type** Edad = Int
### Tipos Enumerativos
- Nuevos tipos de datos
- Dado por un numero finito de valores, donde cada uno tiene un **unico constructor**
- Los nombres de los constructores _**siempre** empiezan con mayuscula_
<br>
**Ejemplo:**
```
Data Simpson = Homero
			 | Marge
			 | Bart
			 | Lisa
			 | Maggie
			 deriving Show
			
-- deriving Show sirve para imprimir los datos
-- de cada Data en consola 
```
- Las **funciones sobre tipos enumerativos** se definen usando _pattern matching_:
```
edad :: Simpson -> Int
edad Homero = 36
edad Marge = 34 
edad Bart = 10
edad Lisa = 8
edad Maggie = 1 
```

### Funcion Parcial vs Total
- **Funcion parcial**: Funcion que con _ciertos tipos de datos puede llegar a fallar_. Ejemplo: div 1 0 = 1/0 = Error
	- Hay que _documentar la precondicion_ o codearla para los casos base / border
	- Debe _cumplir el contrato_ pasado como documento<br><br>
- **Funcion Total**: Funcion que corre con todo tipo de dato que se le pase como parametro

# <u>Listas</u>
## Listas con funciones Observadoras
- **null: [a] -> Bool**, _True_ si la lista esta vacia, _False_ si no
- **head: [a] -> a**, Toma una lista y _devuelve su primer elemento_
- **tail: [a] -> [a]**, Toma una lista y _devuelve la misma lista sin el primer elemento_
### Uso de listas con Pattern Matching
Esquema de **recursion estructural**
Sirve para definir "recorridos" sobre listas:
```
f [] = valor para lista vacia
f (x:xs) = combinacion de x con (f xs)
```

# Tipos de Recursion
- **Estructural**: Permite acceder a los argumentos no recursivos de los constructores, y a los resultados de la recursión para las subestructuras
- **Primitiva**: Como la estructural, pero además permite acceder a las subestructuras
- **Global**: Como la primitiva, pero además permite acceder a los resultados de las recursiones anteriores