# <u>Ejercicio 11</u>

_Se pide completar la siguiente tabla con el análisis de los nonogramas predefinidos. Indicar qué consultas se usaron para averiguar cada uno de los datos. Si algún nonograma no puede ser analizado, indicar el motivo._

|  N   |   Tamaño    | ¿Tiene solución única? | ¿Es Deducible sin backtracking? |
| :--: | :---------: | :--------------------: | :-----------------------------: |
| $0$  |  $2$ x $3$  |                        |                                 |
| $1$  |  $5$ x $5$  |                        |                                 |
| $2$  |  $5$ x $5$  |                        |                                 |
| $3$  | $10$ x $10$ |                        |                                 |
| $4$  |  $5$ x $5$  |                        |                                 |
| $5$  |  $5$ x $5$  |                        |                                 |
| $6$  |  $5$ x $5$  |                        |                                 |
| $7$  | $10$ x $10$ |                        |                                 |
| $8$  | $10$ x $10$ |                        |                                 |
| $9$  |  $5$ x $5$  |                        |                                 |
| $10$ |  $5$ x $5$  |                        |                                 |
| $11$ | $10$ x $10$ |                        |                                 |
| $12$ | $15$ x $15$ |                        |                                 |
| $13$ | $11$ x $5$  |                        |                                 |
| $14$ |  $4$ x $4$  |                        |                                 |
<div style="page-break-after: always;"></div>







# <u>Ejercicio 12</u>

_Indicar si el predicado replicar/3 es reversible en el segundo argumento. Se pide analizar si replicar(+Elem, -N, -Lista) funciona correctamente._

Teniendo en cuenta que:
- **_+Argumento_**: Significa que el argumento debe **estar instanciado** (ligado a un valor concreto) **antes de llamar** al predicado;
- **_-Argumento_**: Significa que el argumento **debe estar sin instanciar** (variable libre) **antes de llamar** al predicado. El predicado **lo instancia**

Y sabiendo que `length(L, N)` es **bidireccional** (funciona tanto declarando una lista explícitamente (definiendo sus elementos) como no), para luego probar de ejecutar en la consola de Prolog **`replicar(+Elem, -N, -Lista)`**:
```
?- replicar(x, N, [x, x, x]).
N = 3.
```

Podemos llegar a deducir que el predicado _replicar/3_ es reversible en el segundo argumento. Más aún, si probamos de ejecutar **`replicar(x, N, L).`** en consola (sin instanciar N y sin definir la lista L), obtenemos:
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
...
```
Demostrando que no es necesario instanciar N para que la función se ejecute como se espera.

**Finalmente, queda demostrado que el predicado _replicar/3_ es reversible en el segundo argumento (N).**