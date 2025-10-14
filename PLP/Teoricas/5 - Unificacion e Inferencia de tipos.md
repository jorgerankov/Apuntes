
### Inferencia de tipos
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
- 