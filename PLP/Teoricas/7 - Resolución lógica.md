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
> σ $\lor$ ($\tau$ $\land$ $\rho$) ---> (σ $\lor$ $\tau$) $\land$ (σ $\lor$ $\rho$)
> (σ $\land$ $\tau$) $\lor$ $\rho$ ---> (σ $\lor$ $\rho$) $\land$ ($\tau$ $\lor$ $\rho$)

##### La fórmula resultante está en forma normal conjuntiva (CNF)
Es una conjunción de disyunciones de literales
> Fórmulas en CNF ---> σ$_{cnf}$ ::= ($k_1$ $\land$ $k_2$ $\land$ ... $\land$ $k_n$)
> Clausulas ---> $k$ ::= ($l_1$ $\lor$ $l_2$ $\lor$ ... $\lor$ $l_m$)
> Literales ---> $l$ ::= **P** | **$\neg$P**

#### Paso 4
##### Sabiendo que $\lor$ es:
- Asociativa ---> σ $\lor$ ($\tau$ $\lor$ $\rho$) <--> (σ $\lor$ $\tau$) $\lor$ $\rho$
- Conmutativa ---> σ $\lor$ $\tau$ <--> $\tau$ $\lor$  σ 
- Idempotente ---> σ $\lor$ σ <--> σ
Notamos una **cláusula** (_disyunción de literales_):
> ($l_1$ $\lor$ $l_2$ $\lor$ ... $\lor$ $l_n$) se nota {$l_1$, $l_2$, ..., $l_n$}

##### Mismo para $\land$:
> ($k_1$ $\land$ $k_2$ $\land$ ... $\land$ $k_n$) se nota {$k_1$, $k_2$, ... $k_n$}

## Resumen
1. Reescribir ==> usando $\neg$ y $\lor$
2. Pasar a forma normal negada, empujando $\neg$ hacia adentro
3. Pasar a forma normal conjuntiva, distribuyendo $\lor$ sobre $\land$ 

# Refutación
Una vez obtenido el conjunto de cláusulas $C$ = {$K_1$, ..., $K_n$}, se busca una **refutación** ==> una demostración de $C$ ⊢ ⊥
Se basa en la **regla de deducción**:
![[Pasted image 20251028114411.png]]
La conclusión se llama la **resolvente de las premisas**

**Entrada**: Un conjunto de cláusulas $C_0$ = {$K_1$, ..., $K_n$}
**Salida**: $SAT/INSAT$, indica si $C_0$ es insatisfactible ($C_0$ ⊢ ⊥)

### Algoritmo de refutación
Sea $C$ := $C_0$ ==> Repetir mientras sea posible
1. Si { } $\in$ $C$, devolver $INSAT$
2. Elegir dos cláusulas $K$, $K'$ $\in$ $C$ tales que
	- $K$ = {**P**, $l_1$, ..., $l_n$}
	- $K'$ = {$\neg$**P**, $l_1'$, ..., $l_m'$}
	- La resolvente ρ = {$l_1$, ..., $l_n$, $l_1'$, ..., $l_m'$} no está en $C$
		- Si no es posible, devoler $SAT$
3. Tomar $C$ := $C$ $\cup$ {ρ} y volver al paso 1 

# <u>Resolución para lógica de primer orden</u>
**Entrada**: Una fórmula σ cerrada de la LPO
**Salida**: Un booleano indicando si σ es válida
> **Si σ es válida, el método siempre termina
> Sino, el método puede no terminar**

### Método de resolución de primer orden (semi-decisión)
1. Escribir $\neg$σ como un conjunto $C$ de **cláusulas**
2. Buscar una **refutación** de $C$
	- Si $\exists$ alguna refutación, **el método encuentra alguna**
	- Sino, **el método puede "colgarse"**
	- 