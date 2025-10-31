## Base de conocimiento 
- describe el **dominio del problema** (Set de bases y hechos que describen el problema)
- Formado por **hechos y reglas de inferencia**
- Se usa **haciendo consultas sobre dicha base** 

No siempre devuelve el mismo valor para todos los inputs, como hace Haskell
- Digo que cosas valen y el sistema _razona_ sobre eso
- Devuelve $\forall$ los valores que cumplen lo pedido, no hay un unico output
## Sintaxis
- ##### Variables
	- Valores que no fueron ligados
	- Despues de ligarse ya no pueden ser modificados
- ##### Numeros
- ##### Atomos
	- Constantes, texto
	- Empiezan con minuscula o estan entre ' '
- ##### Teminos compuestos $\equiv$ estructuras
	- Es un nombre seguido de n argumentos, donde cad auno de ellos es un temrino
	- n es la aridad del termino compuesto
	- Pueden tener varias variables
- ##### Termino
	- variable, numero, atomo o termino compuesto
- ##### Clausula
	- Es una linea del programa. Puede ser Hecho o Regla
- ##### Predicado


```
pred mayorA2(X): V cuando X es mayor que 2
	
	% Va a ser Nat y de minima va a valer 3
	mayorA2(suc(suc(suc(X)))). :- natural(X).
	mayorA2(suc(X)) :- mayorA2(X).

pred menor(X,Y): V cuando X < Y
	
	menor(cero, suc(X)) :- natural(X).
	menor(suc(Y), suc(Y)) :- menor(X,Y). 
	
pred amaALosGatos

	AMG(Z)
	/    \
z := john 
```