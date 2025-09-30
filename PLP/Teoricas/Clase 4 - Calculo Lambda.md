Lenguaje definido solo en **dos operaciones**: _construir funciones y aplicarlas_
## λ$^b$ - Lambda simplemente tipado con booleanos
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
### α-equivalencia
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
- #### Semantica formal
	- **Semantica operacional**
		- Indica como se ejecuta el programa _hasta llegar a un resultado_
		- _small-step_ (paso a paso) / _big-step_ (directa al resultado)
	- **Semantica denotacional**
		- Interpreta los _programas como objetos matematicos_
	- **Semantica axiomatica**
		- Establece _relaciones logicas_ entre el estado del programa _antes y despues de la ejecucion_
- #### Semantica op. small-step
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
- #### Sustitucion
	- **M{x := N}** reemplaza todas las ocurrencias libres de x en M por N
	- #### Propiedades
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