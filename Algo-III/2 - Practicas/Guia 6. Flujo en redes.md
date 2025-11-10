# 1) a. V
Considerando el algoritmo de Ford-Fulkerson, cada iteracion del algoritmo aumenta el flujo por el minimo de capacidades residuales en el camino aumentante. Como todas las capacidades iniciales son pares, todos los valores residuales serán pares. Por lo tanto, cada incremento de flujo es par, y la suma de incrementos es par.

# b. V
Todas las capacidades residuales son pares. Por el algoritmo de Ford-Fulkerson, cada incremento de flujo es par y, por lo tanto, el flujo acumulado en cada arista será par. Si f(e) era par y aumentamos por un valor par, f(e) + par = par.