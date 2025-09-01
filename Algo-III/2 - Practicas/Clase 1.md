_(Cap. 4 Cormen -> Arbol de recursion)_

T(n) = { O(1) =si n = 0
		{ $\sum_{k=0}^{n-1}$ [T(k)] + O(n) sino

T(n-1) = { $\sum_{k=0}^{n-2}$ [T(k)] + C(n-1)

    
# 1 - Palabras en cadena

**separar(S)** = 
$\Bigl\{$ True si |S| = 0,
$\Bigl\{ \bigvee^{|S|}_{i=1}$ (palabra(S[: i]) $\land$ separar(S[i :])) si |S| > 0

***Calculo de complejidad:***
T(n) - T(n-1) = T(n-1) + C
-> **T(n) = 2T(n-1) + C = O(2$^n$)**
-> T(n) $\leq$ C'2$^n$ - d $\leq$ C' 2$^n$

**Por induccion:**
T(n) = 2T(n-1) + C
-> T(n) $\leq_{HI}$ 2(C'*2$^{n-1}$ - d) + C
= C'2$^n$ -2d + C
= C'2$^n$ - d - (d - C) $\leq$ C'2$^n$ - d

# 2 - ABBs optimos

**Ejemplo**: 
[4 3 7 1 2] -> # Accesos
[1, 2, 3, 4, 5] -> Valores
	
**Costo(a, f)** = Nivel del arbol * Cantidad de accesos


**1)** _C = Costo, A = Arbol, f = # accesos, i, j = indices_  
**C(A, f, i, j)** =
	i $\leq$ j = { $\sum_{k = i}^{j}$ f(k) + C(A$_{izq}$, f, A$_{raiz - 1}$) + C(A$_{der}$, f, A$_{raiz + 1}$, j)
	i $>$ j = 0

**2)** Complejidad:
**T(n)** = $\sum_{k = 1}^{n}$ [T(k - 1) + T(n - k)] + O(n) = 2$\sum_{k = 0}^{n-1}$  T(k) + O(n)
= **O(3$^n$)**
