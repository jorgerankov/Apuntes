# <u>Intro a Prolog</u>
##### Opera con **términos de primer orden**:
> X, Y, succ(succ(zero)), bin(I, R, D)

##### Las **fórmulas atómicas** son de la forma **pred(t$_1$, ..., t$n$)**:
> padre(X, Y), suma(zero, X, X)

## <u>Programa</u>
Es un **conjunto de reglas**, donde cada regla es de la forma:
> σ :- $\tau_1$, ..., $\tau_n$ 

> Ej: abuelo(X, Y) :- padre(X, Z), padre(Z, Y)
> donde σ, $\tau_1$, ..., $\tau_n$ son fórmulas atómicas
- Las reglas en las que n = 0 se llaman **hechos**. Ejemplo: σ

#### Interpretación lógica de las reglas
>$\forall$X$_1$, ..., $\forall$X$_k$ . (($\tau_1 \space \land \space ...\space \land \space \tau_n$) => σ)
>
>Donde X$_1$,...,X$_k$ son todas las variables libres de las fórmulas

## <u>Consulta</u>
> ?- σ$_1$, ..., σ$_n$ 

#### Interpretación lógica de las consultas
> $\exists$X$_1$, ..., $\exists$X$_k$ . (σ$_1$ $\land$ ... $\land$ σ$_n$)
> 
> donde X$_1$, ..., X$_k$ son todas las variables libres de las fórmulas

- Prolog busca demostrar la fórmula $\tau$ de la consulta
	- Busca refutar $\neg\tau$
	- Se basa en el **método de resolución**



