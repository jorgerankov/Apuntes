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


# <u>Resolución para lógica proposicional</u>
- **Entrada**: Una fórmula σ de la lógica proposicional
- **Salida**: Un booleano que indica si σ es válida
## Método de resolución
1. Escribir $\neg$σ como un **conjunto $C$ de cláusulas** (_forma clausal_)
2. Buscar **refutar $C$**
##### Si se encuentra una refutación de $C$**:
- Vale $\neg$σ ⊢ ⊥, tal que ¬σ es insatisfactible/contradicción
- Luego, vale σ -> σ es válida/tautología
##### Si no se encuentra:
- No vale $\neg$σ ⊢ ⊥, tal que σ es satisfactible
- Luego, no vale ⊢ σ, tal que σ no es válida 
## Pasaje a forma clausal
_Todas las reglas transforman la fórmula en otra equivalente_
#### Paso 1
Deshacerse del conectivo "==>"
> σ => $\tau$ ---> $\neg$σ $\lor$ $\tau$ 

_La fórmula resultante solo usa los conectivos_ {¬, ∨, ∧}

#### Paso 2
Empujar el conectivo "$\neg$" hacia adentro
> $\neg$(σ $\land$ $\tau$) ---> $\neg$σ $\lor$ $\neg\tau$ 
> $\neg$(σ $\lor$ $\tau$) ---> $\neg$σ $\land$ $\neg\tau$
> $\neg\neg$σ ---> σ

##### La fórmula resultante está en **forma normal negada** (NNF):
> σ$_{nnf}$ ::= P | $\neg$P | σ$_{nnf}$ $\land$ σ$_{nnf}$ | σ$_{nnf}$ $\lor$ σ$_{nnf}$

#### Paso 3
Distribuir $\lor$ sobre $\land$
> 