# Prolog
##### Opera con **términos de primer orden**:
> X, Y, succ(succ(zero)), bin(I, R, D)

##### Las **fórmulas atómicas** son de la forma **pred(t$_1$, ..., t$n$)**:
> padre(X, Y), suma(zero, X, X)

## Programa
Es un **conjunto de reglas**, donde cada regla es de la forma:
> $o$ :- $\tau_1$, ..., $\tau_n$ 

> Ej: abuelo(X, Y) :- padre(X, Z), padre(Z, Y)
> donde $o$, $\tau_1$, ..., $\tau_n$ son fórmulas atómicas
- Las reglas en las que n = 0 se llaman **hechos**. Ejemplo: $o$ 

#### Interpretación lógica 