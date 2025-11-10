# 1) a. V
Considerando el algoritmo de Ford-Fulkerson, cada iteracion del algoritmo aumenta el flujo por el minimo de capacidades residuales en el camino aumentante. Como todas las capacidades iniciales son pares, todos los valores residuales serán pares. Por lo tanto, cada incremento de flujo es par, y la suma de incrementos es par.

# b. V
Todas las capacidades residuales son pares. Por el algoritmo de Ford-Fulkerson, cada incremento de flujo es par y, por lo tanto, el flujo acumulado en cada arista será par. Si f(e) era par y aumentamos por un valor par, f(e) + par = par.

# c. F
La suma de números impares puede ser par (si hay una cantidad par de impares). Tomo como contraejemplo una red simple con 4 nodos: s, a, b, t
s -> a (capacidad 3), s -> b (c3), a -> t (c3), b -> t (c3)
Camino 1 (s -> a -> t): flujo = 3
Camino 2 (s -> b -> t): flujo = 3
Flujo maximo: 6 (par)

# d. F
Contraejemplo: Red con 3 nodos: s, a, t
s -> a con capacidad 3
a -> t con capacidad 3
s -> t con capacidad 3
Flujo maximo: 4 (par)