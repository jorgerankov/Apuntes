# <u>Logica de Primer Orden</u>
Permite **razonar** acerca de **elementos sobre los que se predica**

 > Ejemplo:
 > ∀X.(EsPar(X) ⇒ ¬EsPar(succ(X)))
 
 Extiende a la logica proposicional **con terminos y cuantificadores**
# <u>Programacion Logica</u>
- El usuario escribe una formula: $\exists$X. **P**(X)
- El sistema busca satisfacer o refutar la misma
- Si la satisface, _el sistema genera una salida que verifica la propiedad P_

# <u>Lenguajes de primer orden</u>
Esta dado por:
- Un conjunto de **simbolos de funcion F** = {f, g, h...} con una aridad asociada $\geq$ 0 
- Un conjunto de **simbolos de predicado P** = {P, Q, R...} con una aridad asociada $\geq$ 0 

# <u>Terminos de primer orden</u>
- Hay un lenguaje de primer orden fijado y un conjunto infinito de **variables** $X$ = {X, Y, Z, ...}
### Definicion
- El conjunto $T$ de **terminos** se define:
	- t ::= X | f(t$_1$, ..., t$_n$)
- Donde
	- **X** -> una variable
	- **f** -> un simbolo de funcion de aridad n

## <u>Formulas de primer orden</u>
Gramatica de las formulas en logica proposicional extendidas:
![[Screenshot From 2025-10-25 10-32-22.png]]

- P $\equiv$ un simbolo de predicado de aridad n
- Los cuantificadores ligan una variable X

##### Ocurrencia de una variable X
- Ligada si esta bajo el alcance de un cuantificador
- LIbre si no

- Dos formulas que solo difieren en los nombres de las variables ligadas **se consideran iguales**

##### σ{X := t}
Es la **sustitucion de las ocurrencias libres de X** en la formula σ por el termino t, evitando la captura de variables

# <u>Deduccion natural</u>
- **Contexto Γ** -> ES un conjunto finito de formulas
- **Secuente** -> Es de la forma Γ ⊢ σ

Se agregan reglas de introduccion y eliminacion para ∀ y ∃

#### Cuantificacion universal
![[regla_univ.png]]

#### Cuantificacion existencial
![[Cuant_exist.png]]
# <u>Estructura de primer orden</u>
Es un par $M$ = (_M_, _I_) donde
- _M_ es un conjunto **no vacio** -> _universo_
- _I_ es una funcion que le da interpretacion a cada simbolo
- Para cada simbolo de funcion f de aridad n
	- _I_(f) : _M_$^n$ -> _M_
- Para cada simbolo de predicado **P** de aridad n
	- _I_(**P**) $\subseteq$ M$^n$

# <u>Interpretacion de terminos</u>

### Asignacion
Es una funcion que **a cada variable** le asigna un **elemento del universo** -->  **a** : $X$ → _M_

### Interpretacion de terminos (Def)
Cada termino t ∈ $T$ se interpreta como un elemento **a**(t) ∈ _M_, extendiendo la definicion de **a** a terminos
- **a**(f(t$_1$, ..., t$_n$)) = _I_(f)(**a**(t$_1$), ..., **a**(t$_n$))
# <u>Interpretacion de formulas</u>
##### Relacion de **satisfaccion a** ⊨$_M$ σ
-> La asignacion **a** (bajo la estructura $M$) satisface la formula σ

![[Screenshot From 2025-10-25 11-05-41.png]]

# <u>Validez y satisfactibilidad</u>
### Una formula σ es
- #### Valida
	- Si **a** ⊨$_M$ σ para toda $M$, **a**
- #### Invalida
	- Si **a** /⊨$_M$ σ para alguna $M$, **a**
- #### Satisfactible
	- Si **a** ⊨$_M$ σ para alguna $M$, **a**
- #### Insatisfactible
	- Si **a** /⊨$_M$ σ para toda $M$, **a**

# <u>Modelos</u>

- _Sentencia_ -> Formula σ sin variables libres
- _Teoria de primer orden_ -> Un conjunto de sentencias

### Consistencia
Una teoria $T$ es consistente si $T$  ̸⊢ ⊥ (???)
### Modelo (def)
Una estructura $M$ = (_M_, _I_) es un modelo de una teoria T si vale
⊨$_M$ σ para toda formula σ ∈ $T$

# <u>Correccion y completitud</u>
#### Dada una teoria T, son $\equiv$
- $T$ es consistente
- $T$ tiene (al menos) un modelo
#### Dada una formula σ, son $\equiv$
-  ⊢ σ es derivable
-  σ es valida
#### Dada una formula σ, son $\equiv$
- ⊢ ¬σ es derivable
- σ es insatisfactible

# <u>Unificacion de terminos</u>
![[Pasted image 20251025113823.png]]

### Falta poner _Terminacion del algoritmo de unificacion_ y _Correccion del algoritmo de unificacion_

