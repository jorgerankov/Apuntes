## <u>About</u>
- Los programas se escriben en un subconjunto de la LPO
- Es **declarativo**: Se especifican hechos, reglas de inferencia y objetivos
- **Mundo cerrado**: Solo se puede suponer lo que se declara explicitamente
- Todo **lo que no se pueda deducir** a partir del programa se supone falso
- Un **solo tipo**: los terminos

## <u>Base de conocimiento</u> 
- describe el **dominio del problema** (Set de bases y hechos que describen el problema)
- Formado por **hechos y reglas de inferencia**
- Se usa **haciendo consultas sobre dicha base** 

No siempre devuelve el mismo valor para todos los inputs, como hace Haskell
- Digo que cosas valen y el sistema _razona_ sobre eso
- Devuelve $\forall$ los valores que cumplen lo pedido, no hay un unico output
## <u>Sintaxis</u>
- ##### Variables
	- Valores que no fueron ligados
	- Despues de ligarse ya no pueden ser modificados
	- Empiezan con mayuscula o _
- ##### Numeros
- ##### Atomos
	- Constantes, texto
	- Empiezan con minuscula o estan entre ' '
- ##### Teminos compuestos $\equiv$ estructuras
	- Es un nombre seguido de _n_ argumentos, donde cada uno de ellos es un termino
	- _n_ es la aridad del termino compuesto
	- Pueden tener variables como argumentos
- ##### Termino
	- variable, numero, atomo o termino compuesto
- ##### Clausula
	- Es una linea del programa. 
	- Puede ser Hecho (declaracion de una variable) o Regla (instanciacion de una variable X, Y, Z, etc)
	- El **:-** se puede ver como un <-- y **las comas** como $\land$ 
- ##### Predicado
	- Coleccion de clausulas
- ##### Objetivo (goal)
	- Es el predicado que se consulta a Prolog y el que nos devuelve el resultado


```	
pred amaALosGatos:
		 AMG(Z)
	/             \
z := john       z := john
y := odie       y := garfield
   |                 |
 false             true
```

# <u>Sustitucion y Unificacion</u>
#### Sustitucion
- Es una **funcion _S_** : _Variables -> Term_
- **Term** := El conjunto formado por todos los posibles términos
- Se puede extender _S_ a una funcion _Term -> Term_
- Se usan sustituciones **obtenidas con el MGU** para igualar literales y aplicar la regla de resolucion
#### <u>Tener en cuenta que el orden de las cláusulas y sus literales en el programa influyen en el resultado</u>
## <u>Patrones de instanciacion</u>
- El modo esperado se comunica en los comentarios ("%")
	- **+X debe** estar instanciado, 
	- **-X no debe** estar instanciado,
	- **?X puede o no** estar instanciado
- El usuario no puede suponer mas alla de la especificacion
## <u>Aritmetica</u>
- **El motor de operaciones** aritmeticas de Prolog es **independiente del motor logico** (extra-logico)
- Expresiones: Un numero, var ya instanciada, E1+E2, ...
- ##### Algunos operadores
	- E1 < E2, E1 =< E2, E1 >= E2
	- ***X is E*** tiene exito <--> X **unifica** con el res de _evaluar la expresion aritmetica E_
## Listas
- Sintaxis: [], [H | T], [X,Y,...,Z | L]
- Ejemplos: [1,2], [1,2 | N]
