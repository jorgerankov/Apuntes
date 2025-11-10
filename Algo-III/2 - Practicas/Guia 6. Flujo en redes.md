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
s -> t con capacidad 1
Flujo maximo: 4 (par)

Camino s -> a -> t: flujo = 3
Camino s -> t: flujo = 1

Total: 4, que es par, tal que no existe un flujo maximo donde todas las aristas tengan flujo impar y el flujo total sea impar a la vez

# e. V
Iniciamos con f(e) siendo un numero racional para toda arista e. Cada iteracion encuentra un camino aumentante y, si aumentamos cada arista del camino por un valor racional, si f(e) era racional y sumamos un racional, el valor final de la misma también será racional. Mas aun, si las capacidades son números enteros, el flujo máximo también es entero, que pertenece al mundo de los racionales.

# 2)
4 nodos y 5 aristas:
(s -> u)  capacidad F     
(u -> v)  capacidad F
(v -> t)  capacidad F
(s -> v) capacidad F
(u -> t) capacidad F
# 3)
**a)** O(V * E$^2$) (cant. total de vertices * cant. total de aristas$^2$)
**b)** 