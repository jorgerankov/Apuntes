# 1 - SumaSubconjuntosBT
**a) Escribir el conjunto de soluciones candidatas para C = {6, 12, 6} y k = 12**
- Son todos los vectores binarios posibles, todos los posibles **"incluir o no incluir"** cada elemento de C
```
a = {(0,0,0), (1,0,0), (1,1,0), (1,0,1), (0,1,0), (0,1,1), (0,0,1), (1,1,1)}
``` 
**b) Escribir el conjunto de soluciones válidas para C = {6, 12, 6} y k = 12**
```
a = {(1,0,1), (0,1,0)}
```
**c) Escribir el conjunto de soluciones parciales para C = {6, 12, 6} y k = 12**
- Son **todos los prefijos** de todos los vectores candidatos
```
i = 1 = {(0), (1)}
i = 2 = {(0,0), (0,1), (1,0), (1,1)}
i = 3 = {(0,0,0), (1,0,0), (1,1,0), (1,0,1),
			 (0,1,0), (0,1,1), (0,0,1), (1,1,1)}
```


# 2 - MagiCuadrados
**a) ¿Cuántos cuadrados habría que generar para encontrar todos los cuadrados mágicos si se utiliza una solución de fuerza bruta?** -> $(n^{2})!$   



# 1 - Palabras en cadena

**1) separar(S)** = 
$\Bigl\{$ True si |S| = 0,
$\Bigl\{ \bigvee^{|S|}_{i=1}$ (palabra(S[: i]) $\land$ separar(S[i :])) si |S| > 0

***2) Calculo de complejidad:***
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
  
**Costo(a, f)** = Nivel del arbol * Cantidad de accesos

**1)** _C = Costo, A = Arbol, f = # accesos, i, j = indices_  
**C(A, f, i, j)** =
	i $\leq$ j = { $\sum_{k = i}^{j}$ f(k) + C(A$_{izq}$, f, A$_{raiz - 1}$) + C(A$_{der}$, f, A$_{raiz + 1}$, j)
	i $>$ j = 0

**3)** Complejidad:
**T(n)** = $\sum_{k = 1}^{n}$ [T(k - 1) + T(n - k)] + O(n) = 2$\sum_{k = 0}^{n-1}$  T(k) + O(n)
= **O(3$^n$)**