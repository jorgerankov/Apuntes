
# Inferencia de tipos
- **Notacion**: Tomamos terminos sin anotaciones de tipos
	- λx.U $\neq$ λx : τ. M
- ***erase(M)***: termino que me _permite borrar las anotaciones de tipos de M_, y **devuelve M Sin anotaciones de tipos**
#### Problema de inferencia de tipos
- Dado un termino U, busco ver si es tipable
- Si es tipable,
	- Quiero buscar un Γ, un termino M y un tipo τ
	- Tal que erase(M) = U y Γ ⊢ M : τ
#### Algoritmo para inferencia de tipos
- Se basa en manipular datos _parcialmente conocidos_
- **Incorpora incognitas** ($X_1, X_2, X_3...$) a los tipos
- **Resuelve ecuaciones** entre tipos **con incognitas**
# Unificacion
##### Es el problema de resolver sistemas de ecuaciones entre tipos con incognitas
- Hay definido un _conjunto finito de constructores de tipos_
	- Tipos constantes
	- Constructores unarios
	- Constructores binarios
- Los **tipos** se **forman usando un conjunto de incognitas y constructores**: τ ::= X$_n$ | C(τ1, . . . , τn)
#### Sustitucion
- Funcion que le asigna un tipo a cada incognita
- **Notacion** de _funcion que asocia (**sustitucion**) las variables a cada tipo_:
  **S** = {X$_{k_1}$ := τ$_1$, . . . , X$_{k_n}$ := τ$_n$}, Donde **S(X$_{k_i}$)** = τ$_i$ para cada 
  1 $\leq$ i $\leq$ n
- Si τ es un tipo => **S(τ) reemplaza cada incognita de τ por el valor que le otorga S**
#### Problema de unificacion
Es un **conjunto finito E de ecuaciones entre tipos** que **pueden involucrar incognitas**
#### Unificador
- Aplicado en E, es **una sustitucion S** tal que
	- S(τ$_1$) = S(σ$_1$), 
	- ... 
	- S(τ$_n$) = S(σ$_n$)
- La solucion a un problema de unificacion _no es unica_
#### Algoritmo de unificacion Martelli–Montanari
Dado un conjunto de ecuaciones E (problema de unificacion):
- Mientras  E $\neq$ ∅, se **aplica sucesivamente alguna de las seis reglas**
- La regla puede resultar en una **falla**
- Sino, la regla es de la forma **E →$_S$ E'**, donde **E se reduce a resolver E' aplicando la sustitucion S** 
#### Ej
_Calcular unificadores m´as generales para los siguientes problemas de unificacion:_
{(X2 → (X1 → X1)) ?= ((Bool → Bool) → (X1 → X2))}
