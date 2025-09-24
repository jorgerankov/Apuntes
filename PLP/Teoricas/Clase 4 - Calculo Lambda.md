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
## Sistema de tipos
Se formaliza con un _sistema deductivo_
- #### Contextos de tipado
	- Conjunto finito de pares (xi : τi)
	- sin variables repetidas
	- Se nota con letras griegas mayusculas
- #### Juicios de tipado
	- Predica sobre juicios de la forma Γ ⊢ M : τ
	- 
