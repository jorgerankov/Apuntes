
| $N$  |  $Tamaño$   | $¿Tiene\space solución\space única?$ | $¿Es\space deducible\space sin\space backtracking?$ |
| :--: | :---------: | :----------------------------------: | :-------------------------------------------------: |
| $0$  |  $2$ x $3$  |                                      |                                                     |
| $1$  |  $5$ x $5$  |                                      |                                                     |
| $2$  |  $5$ x $5$  |                                      |                                                     |
| $3$  | $10$ x $10$ |                                      |                                                     |
| $4$  |  $5$ x $5$  |                                      |                                                     |
| $5$  |  $5$ x $5$  |                                      |                                                     |
| $6$  |  $5$ x $5$  |                                      |                                                     |
| $7$  | $10$ x $10$ |                                      |                                                     |
| $8$  | $10$ x $10$ |                                      |                                                     |
| $9$  |  $5$ x $5$  |                                      |                                                     |
| $10$ |  $5$ x $5$  |                                      |                                                     |
| $11$ | $10$ x $10$ |                                      |                                                     |
| $12$ | $15$ x $15$ |                                      |                                                     |
| $13$ | $11$ x $5$  |                                      |                                                     |
| $14$ |  $4$ x $4$  |                                      |                                                     |
# Ejercicio 12

_Indicar si el predicado replicar/3 es reversible en el segundo argumento. En concreto se pide analizar si replicar(+Elem, -N, -Lista) funciona correctamente._

Teniendo en cuenta que:
- **_+Argumento_**: Significa que el argumento **debe estar instanciado** (ligado a un valor concreto) **antes de llamar** al predicado.
- **_-Argumento_**: Significa que el argumento **debe estar sin instanciar** (variable libre) **antes de llamar** al predicado. El predicado **lo instancia**.

Y sabiendo que `length(L, N)` es **bidireccional** (funciona tanto declarando una lista explícitamente (definiendo sus elementos) como no), para luego probar de ejecutar **`replicar(+Elem, -N, -Lista)`** en consola:
```
?- replicar(x, N, [x, x, x]).
N = 3.
```

Podemos llegar a deducir que el predicado replicar/3 es reversible en el segundo argumento. Más aún, si probamos de ejecutar **`replicar(x, N, L).`** en consola, obtenemos:
```
?- replicar(x,N,L).
N = 0,
L = [] ;
N = 1,
L = [x] ;
N = 2,
L = [x, x] ;
N = 3,
L = [x, x, x] ;
N = 4,
L = [x, x, x, x]
...
```
Demostrando que no es necesario instanciar