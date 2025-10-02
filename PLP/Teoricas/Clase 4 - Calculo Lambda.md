Lenguaje definido solo en **dos operaciones**: _construir funciones y aplicarlas_

## Expresiones
### $E ::= x | E E | \lambda x.E$ 
Una **expresion** puede ser:
- Una **variable** ($x$)
- Una **aplicacion** de una funcion a un determinado parametro ($E E$ aplica una funcion a otra funcion)
- Una **abstraccion lambda**, con un parametro y un cuerpo ($\lambda x.E$)
### Variables
- Identificadores asociados a cualquier letra a,b,c...
- **Dos tipos**:
	- **Libres**: no dependen de un parametro de la funcion
	- **Ligadas**: dependen de un parametro de la funcion
	- **Ej**: $x$ es una var. _ligada_ e $y$ es una _libre_: (x) => x + y
### Variables libres y ligadas
**Definicion formal de variables libres**:
- Variables **libre de una variable**: $FV(x)\space =\space \{ x\}$
- Variables **libre de una aplicacion**: $FV(M\space N)\space =\space FV(M) \cup FV(N)$
- Variables **libre de una abstraccion**: $FV(\lambda x.M)\space =\space FV(M) - \{ x\}$
- 
### Aplicacion
- Representa la **aplicacion de una funcion a un det. parametro**
- Tanto la funcion como el param. **son expresiones lambda**
- Ejemplos (_se asocia de izquierda a derecha_): 
	- $f\space x$ == f(x)
	- $f\space x\space y$ == f(x) (y)
	- $f(x\space y)$ == f(x(y))
### Abstraccion
- Representacion de una **funcion pura**, con su parametro y funcion de retorno
- Usa $\lambda$ para _representar una funcion_ y el punto para _separar el param. de la expresion de retorno_
- Se asocia de _derecha a izquierda_
- Ejemplos: 
	- $\lambda \space x.\space x$ devuelve lo que reciba de $x.$ y el resultado es una nueva expresion que es solamente $x$ (funcion Identidad)
	- $\lambda x.\space y$ == (x) => y --> Toma $x$, devuelve $y$
	- $\lambda x.\space yz$ == (x) => y(z) --> Toma $x$, devuelve la aplicacion de $z$ en $y$
	- $(\lambda x.\space y)z$ == ((x) => y) (z) --> Funcion que toma $x$, devuelve $y$, y todo esto lo valuo en $z$
	- $\lambda x.\space \lambda y.\space x$ == (x) => (y) => x
## Notacion reducida (parentesis)
- Omite parentesis exteriores: $(\lambda x.\space (M)) \equiv\space \lambda x.M$ 
- La **aplicacion** es **asociativa a izquierda**: $(M\space N)\space L \equiv\space M\space N\space L$ 
- Las **abstracciones** son **asociativas a derecha**: $\lambda x.\space (\lambda y.M) \equiv \lambda x.\lambda y.M$ 
- La **aplicacion** tiene **precedencia** (_prioridad_) **sobre la abstraccion**: $\lambda x.(M N) \equiv \lambda x.MN$ 
 
## λ$^b$Lambda simplemente tipado
#### Sintaxis de los tipos
- τ , σ, ρ, . . . ::= bool
	- | τ → σ
- “→” es _asociativo a derecha_ 
#### Sintaxis de los terminos
- **λx : τ . M**
- **M N**: Aplicacion del termino M a N (crea un nuevo termino)
- **if M then N else P**: Si M es un termino entonces N, sino P
	- Al aplicar esto creo un nuevo termino
- Su aplicacion es _asociativa a izquierda_
#### α-equivalencia
- Son dos terminos M y N que **difieren** solamente en **el nombre de sus variables ligadas**
- Es una _relacion de equivalencia_
## Sistema de tipos
Se formaliza con un _sistema deductivo_
- #### Contextos de tipado
	- Conjunto finito de pares (xi : τi)
	- sin variables repetidas
	- Se nota con letras griegas mayusculas
- #### Juicios de tipado
	- Predica sobre juicios de la forma Γ ⊢ M : τ
	- ***Ver reglas de tipado***
	- #### Propiedades
		- **Unicidad de tipos**
			- Si Γ ⊢ M : τ y Γ ⊢ M : σ son derivables, entonces τ = σ
		- **Weakening + Strengthening**
			- Si Γ ⊢ M : τ es derivable y fv(M) ⊆ dom(Γ ∩ Γ′ ) entonces Γ ′ ⊢ M : τ es derivable
## Semantica formal
- **Semantica operacional**
	- Indica como se ejecuta el programa _hasta llegar a un resultado_
	- _small-step_ (paso a paso) / _big-step_ (directa al resultado)
- **Semantica denotacional**
		- Interpreta los _programas como objetos matematicos_
- **Semantica axiomatica**
		- Establece _relaciones logicas_ entre el estado del programa _antes y despues de la ejecucion_
### Semantica op. small-step
- **Programas**
	- es un _termino M tipable y cerrado_ (fv(M) = ∅)
	- El juicio de tipado ⊢ M:τ debe ser derivable para algun τ
- **Juicios de evaluacion**
	- hace _afirmaciones sobre juicios de evaluacion_ **M → N** (M y N son programas)
- **Valores**
	- son los posibles resultados de **evaluar programas**:
			- V ::= true | false | λx : τ. M
- **Ver Reglas de evaluacion para expresiones booleanas**
- **Ver Reglas de evaluacion para funciones (abstraccion y aplicacion)**
 
 **Sustitucion**
- **M{x := N}** reemplaza todas las ocurrencias libres de x en M por N
## Propiedades de evaluacion
- **Determinismo**
	- Si M → N1 y M → N2 entonces N1 = N2
- **Preservacion de tipos**
	- Si ⊢ M : τ y M → N entonces ⊢ N : τ
- **Progreso**
	- Si ⊢ M : τ entonces
		- O bien M es un valor, 
		- O bien existe N tal que M → N
- **Terminacion**
	- Si ⊢ M : τ , entonces no hay una cadena infinita de pasos
- **Canonicidad**
	- Si ⊢ M : bool es derivable, entonces la evaluacion de M termina y el resultado es true o false
	- Si ⊢ M : τ → σ es derivable, entonces la evaluacion de M termina y el resultado es una abstraccion
### Forma normal
- Es un termino que no puede evaluarse mas
	- **Lema**: Todo valor esta en forma normal
- **Estado de error**: 
	- Evaluacion donde el termino esta en **forma normal**, pero **no es un valor**
	- El sistema de runtime en una implementacion real generaria una excepcion
### Evaluacion en muchos pasos
-  **Juicio en muchos pasos**
	- Es la clausura reflexiva-transitiva de →. Es la menor relacion tal que
		- Si M → M′ , entonces M ↠ M′
		- M ↠ M para todo M
		- Si M ↠ M′ y M′ ↠ M′′, entonces M ↠ M′′
- #### Propiedades
	- **Unicidad de formas normales**
		- Si M ↠ U y M ↠ V con U, V formas normales, entonces U = V
	- **Terminacion**
		- Para todo M existe una forma normal N tal que M ↠ N
## Calculo λ$^{bn}$
#### Tipos
- τ, σ, ... ::= ... | nat
#### Semantica informal
```
M ::= ... 
	| zero
	| succ(M) el sucesor de M 
	| pred(M) el predecesor de M 
	| isZero(M) true/false, si M == cero o no
```
#### Ver reglas de tipado

#### Conjunto de valores
- **V** ::= ... | zero | succ(**V**)
- **_Ver semantica operacional_**
#### Forma normal
- Un programa M es una _f.n._ si no existe M′ tal que M → M'
- Las f.n.'s que no son valores se llaman **terminos de error**
#### Propiedades
- **Determinismo**
	- Si M → N1 y M → N2 entonces N1 = N2
- **Preservacion de tipos**
	- Si ⊢ M : τ y M → N entonces ⊢ N : τ
- **Progreso**
	- Si ⊢ M : τ entonces:
		- O bien M es un valor, 
		- O bien existe N tal que M → N
- **Terminacion**
	- Si ⊢ M : τ , entonces no hay una cadena infinita de pasos
