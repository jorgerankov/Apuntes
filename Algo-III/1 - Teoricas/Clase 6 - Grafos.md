 - Modelan **relaciones entre vertices**
 - Representa **problemas de la vida real** que consideran una red como _estructura subyacente_
### <u>Que es un Grafo G = (V, X)</u>
 Es un **par de conjuntos**,
 - **V** _es un conjunto de puntos/nodos/vertices_ 
 - **X** es un _subconjunto del conjunto de pares no ordenados_ de elementos distintos de V
 - Los **elementos de X** se llaman **aristas/ejes**
 - Dados v,w ∈ V, si e = (v,w) ∈ X:
	 - _v y w_ son **adyacentes** (comparten un mismo par)
	 - _e_ es **incidente** a v y w
- La **vecindad** de un vertice v, **N(v)**:
	- Es el _conjunto de los vertices adyacentes a v_
	- **N(v)** = {w ∈ V : (v,w) ∈ X}
- #### Notacion
	- n$_G$ = |V|
	- m$_G$ = |X|

### <u>Multigrafos</u>
Grafos en el que **puede haber varias aristas** entre **el mismo par de vertices distintos**
### <u>Pseudografo</u>
Grafos en el que **puede haber varias aristas entre cada par de vertices** y tambien **puede haber aristas** _(loops)_ que **unan a un vertice con si mismo**

### <u>Grado de un vertice v en el grafo G</u>
- **d$_G$ (v)**: es la cantidad de _aristas incidentes a v en G_
- **∆(G)**: El **maximo grado de los vertices** de G
- **δ(G)**: El **minimo grado de los vertices** de G

La **suma de los grados** de los vertices de un grafo = _2 veces el numero de aristas_: $\sum^{n}_{i = 1}$d(v$_i$) = 2m
- Para todo grafo, la cantidad de vertices que tienen grado impar es par
### <u>Grafo Completo</u>
- Todos los vertices son **adyacentes entre si**
- K$_n$ es el **grafo completo** de n vertices
### <u>Complemento de un Grafo G$^c$ = (V, X)</u>
- Tiene el **mismo conjunto de vertices** que G
- Tiene todos los vertices que **no son adyacentes en G**
### <u>Recorridos, caminos, circuitos y ciclos</u>
- ***Recorrido***: Es una **sucesión de vértices conectados por aristas** donde **cada arista une dos vértices consecutivos** del recorrido
- ***Camino***: Es un recorrido que **no pasa dos veces por el mismo vertice**
- ***Seccion***: 
- ***Circuito***: Es un recorrido que **empieza y termina en el mismo vertice**
- ***Ciclo***: Es un circuito de **3 o mas vertices que no pasa dos veces por el mismo vertice**
### <u>Longitud: l(P)</u>
Es la **cantidad de aristas que tiene** un _recorrido P_
### <u>Distancia d(v,w)</u>
- Es la **longitud del recorrido mas corto** entre _dos vertices v y w_
- **d(v,w) = ∞** si _no existe recorrido entre v y w_
- $\forall$ vertice v, **d(v, v) = 0**
- Si un _recorrido P entre v y w_ tiene **longitud d(v,w), P debe ser un camino**
- #### Propiedades ($\forall$ u, v, w pertenecientes a V)
	- d(u, v) $\geq$ 0 y d(u, v) = 0 si y solo si u = v
	- d(u, v) = d(v, u)
	- d(u,w) $\leq$ d(u, v) + d(v,w)
### <u>Subgrafos</u>
Es un grafo formado **a partir de un subconjunto de los vértices y aristas de otro grafo**
- Si H ⊆ G y H $\neq$ G -> H es **subgrafo propio de G**, H ⊂ G
- H es un **subgrafo generador de G** si H ⊆ G y V$_G$ = V$_H$
- #### Subgrafo inducido 
	- Un subgrafo H = (V$_H$, X$_H$) de G = (V$_G$ , X$_G$) es **inducido** si **todo par u, v** ∈ V$_H$ con (u, v) ∈ X$_G$ entonces tambien (u, v) ∈ X$_H$
### <u>Grafo Conexo</u>
- Un grafo es **conexo** si **existe camino entre todo par de vertices**
- Una **componente conexa** de un grafo G **es un subgrafo conexo maximal de G**
### <u>Grafos bipartitos</u>
Es un tipo de grafo en el que el **conjunto de vértices puede dividirse en dos grupos** (conjuntos) **disjuntos**
- **Ningún vértice** dentro de un mismo grupo **está conectado entre sí**
- Todas las aristas **unen un vértice de un grupo con un vértice del otro grupo**

Si el conjunto de vértices es V, **existen _dos subconjuntos U y W_ tales que**:
- _U_ ∪ _W_ = V
- _U_ ∩ _W_ = ∅
- Cada arista conecta un vértice de _U_ con uno de _W_

Un _grafo bipartito con subconjuntos V1, V2_, es **bipartito completo** si **todo vertice en V1 es adyacente a todo vertice en V2**
### <u>Isomorfismo de grafos</u>
Dados dos grafos G = (V, X) y G' = (V' , X') son **isomorfos**:
- Si  existe una **funcion biyectiva f : V → V'** tal que $\forall$ v,w ∈ V: ***(v,w) ∈ X <-> (f(v), f(w)) ∈ X'***
- La **funcion f** es llamada **funcion de isomorfismo**
- Cuando G y G' son isomorfos --> se denota **G = G'**
##### Si dos grafos G = (V, X) y G' = (V', X') son isomorfos
- Tienen el mismo numero de vertices
- Tienen el mismo numero de aristas
- Tienen el mismo numero de componentes conexas
### <u>Representacion de grafos</u>
- ##### Matrices
	- la respresentacion de grafos mediante matrices **es util conceptual y teoricamente**
- ##### Listas
	- Estructuras **mas eficientes en espacio**
- ##### Matriz de adyacencia
	- A ∈ {0, 1}$^{n×n}$, donde los elementos a$_{ij}$ de A se definen como:
		- **1** si G **tiene una arista** entre los vertices v$_i$ y v$_j$
		- **0 si no**
	- La suma de los elementos de la columna o fila i de A **es igual a d(v$_i$)**
### Digrafos
Es una estructura en la que **las aristas tienen una dirección**. Es decir, **cada arista va de un vértice** (nodo) **a otro**, formando un **par ordenado**
- Dado un _arco e = (u,w)_ llamaremos al primer elemento (u) ***cola*** de e y al segundo elemento (w), ***cabeza*** de e
- El ***grado de entrada*** d$_{in}$(v) de un vertice v de un digrafo es **la cantidad de arcos que llegan a v**
- El ***grado de salida*** d$_{out}$(v) de un vertice v de un digrafo es la **cantidad de arcos que salen de v** == _la cantidad de arcos que tienen a v como cola_
- El ***grafo subyacente*** de un digrafo G es el grafo G$^s$ que resulta de remover las direcciones de sus arcos
- ##### Recorrido/Camino orientado
- ##### Circuito/Ciclo orientado
- Un digrafo se dice ***fuertemente conexo*** si _para todo par de vertices u, v_ **existen caminos orientados de u a v y de v a u**




# Definiciones
#### Vertices:
- Son los valores del grafo
- Se dibujan o definen como nodos
#### Aristas
- Las lineas que conectan los vertices unos con otros
- Permite unir nodos entre si
#### Vertices Adyacentes
- Nodo que tiene al menos una conexion con otro nodo unidos mediante una arista
- Ejemplo: 
```
	  V2 ---- V1
	  |
	  V4
	  
	V1 y V4 son vertices adyacentes con V2  
```

#### Vertice aislado
- Aquel vertice que no tiene aristas con ningun otro vertice
- No es adyacente con ningun vertice
#### Aristas incidentes en un vertice
- Son las aristas que tienen al menos un vertice como extremo
- Ejemplo:
```		
	|-----a2-----|
	V1 ---a1--- V2 --a3-- V4

	a1, a2 y a3 son aristas incidentes de V2
```
#### Aristas adyacentes en un vertice
- Son las aristas que tienen un unico vertice en comun
- En el ejemplo anterior, a1 y a3 son aristas adyacentes ya que el unico vertice que tienen en comun entre ambas es v2 
#### Aristas paralelas
- Son las aristas que estan comprendidas entre los mismos vertices
- En el ejemplo, a1 y a2 son aristas paralelas
#### Bucles / Lazos
- Son las aristas que apuntan a un mismo vertice

### Grafo simple
- Si y solo si no tiene aristas paralelas ni bucles
- El ejemplo no es un grafo simple
## Representacion matricial de G
### Matriz de adyacencia
- Matriz booleana de $n$ x $n$ (cuadrada)
- **Ma(G)** (Matriz de adyacencia de G) 
  **cuyos elementos m$_{ij}$ son:**
	- 1 si v$_i$ es adyacente a v$_j$
	- 0 si v$_i$ no es adyacente a v$_j$
### Matriz de incidencia
- Matriz booleana de $n$ x $m$ 
  (#$vertices$ x #$aristas$)
- **Mi(G)** (Matriz de incidencia de G) 
  **cuyos elementos m$_{ij}$ son:
	- 1 si v$_i$ es extremo de a
	- 0 si v$_i$ no es extremo de a
## Grado / Valencia de un vertice
#### Funcion grado: g V -> N$_0$
- g(v$_i$) = Cantidad de aristas incidentes en v$_i$
- Los bucles se cuentan x2
- **La suma de los grados de los vertices es igual al doble de la cantidad de aristas**
## Caminos y ciclos en grafos
#### Camino
- Sucesion de aristas adyacentes
#### Ciclo
- Camino cerrado (V inicial = V final)
## Caminos y ciclos eulerianos
#### Camino de Euler
- Camino que pasa por todas las aristas solo una vez
- Un grafo tiene camino euleriano si
	- Es conexo
	- Todos los vertices tienen grado par o a lo sumo 2 grados impar
#### Ciclo de Euler
- Ciclo que pasa por todas las aristas del grafo
	- Un grafo tiene ciclo euleriano si
		- Es conexo
		- Todos los vertices tienen grado par


### Grafo regular 
- Aquellos grafos donde cada vertice el la mismo grado
- Ejemplo: un cuadrado es un grafo 2-regular (cada vertice tiene 2 aristas => cada vertice es de grado 2)
### Grafo completo k$_n$
- Aquellos grafos donde cada vertice es adyacente a todos los demas
- Ejemplo: Un triangulo es un grafo completo k$_3$
### Grafos bipartitos
- Aquellos grafos que hacen una particion de su conjunto de vertices
- **G es bipartito** <=> 
	- V = V1 $\cup$ V2 con V1 $\neq \space \emptyset \space \land$ V2 $\neq \space \emptyset$ 
	- $\land$  V1 $\cap$ V2 = $\emptyset$ 
### Grafos bipartitos completos K${n,m}$
- Son grafos bipartitos de n + m vertices con $\forall$ las aristas posibles
- Ejemplo: K$_{3,2}$ tiene 3 vertices por un lado y 2 por el otro
- La cantidad de aristas de un grafo K$_{n,m}$ es $n . m$ 
### Sub-Grafos
- Es un grafo que **esta incluido en otro** grafo
- Para **obtener subgrafos de un grafo** se puede:
	- Suprimir uno o varios vertices y las aristas incidentes en ellos
	- Suprimir solamente una o varias aristas
- Si tengo un grafo {a,b,c,d,e,f,g} y quiero ver G$_{a,e,g}$, me quedo solo con los vertices y aristas de {b,c,d,f} 
### Grafos conexos
#### Relacion de conexion
- Relacion que se define en el conjunto de vertices
- Un vertice se relaciona con otro <=> $\exists$ un camino del vertice $i$ al vertice $j$ o si $i$ = $j$
- v$_i$ R v$_j$ <=> $\exists$ camino de v$_i$ a v$_j$ $\lor$ v$_i$ = v$_j$
- Se puede llegar de cualquier vertice a cualquier otro mediante algun camino entre ellos
## Desconexion de Grafos
Dado un Grafo G conexo:
#### Istmo / Punto de corte
- Vertice tal que al surpimirlo/removerlo desconecta al grafo
#### Puente
- Es una arista tal que al surpimirla/removerla desconecta al grafo
#### Conjunto desconectante
- Completar

## Digrafos - Grafos dirigidos
#### Definicion
- Es una **terna** formada por 
	- Un **conjunjo de vertices** V $\neq\space\emptyset$
	- Un **conjunto de aristas dirigidas** o "arcos" 
	- Y una **funcion de incidencia** $\delta$ que a cada arista le hace corresponder un par ordenado de vertices (v$_i$, v$_j$), con v$_i$ siendo el extremo inicial y v$_j$ el extremo final
#### Caminos
- **Simples**: $\forall$ los vertices son $\neq$
- **Elementales**: Si $\forall$ las aristas son $\neq$
### Funcion Grado
#### Grado positivo
- Cantidad de **arcos** (aristas dirigidas) **que "entran" al vertice** =>  g$^+$(v)
#### Grado Negativo
- Cantidad de **arcos** (aristas dirigidas) **que "salen" del vertice** => g$^-$(v)
#### Grado Total
- **Suma** de los **grados** positivo y negativo => g(v)
#### Grado Neto
- **Diferencia** entre **grados** positivo y negativo => g$_N$(v)
#### Propiedades:
- $\sum$ g$^+$(v$_i$) = | A |; $\sum$ g$^-$(v$_i$) = | A |
- $\sum$ g(v) = 2 | A |; $\sum$ g$_N$(v$_i$) = 0
