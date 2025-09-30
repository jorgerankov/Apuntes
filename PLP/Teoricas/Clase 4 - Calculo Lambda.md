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
		- 