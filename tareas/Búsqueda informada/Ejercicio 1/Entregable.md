# Este reporte corresponde a la tarea: Búsqueda informada -> Ejercicio 1.

## Elaborado por: Arianna Rodríguez Rodas

### 1. La pareja origen–destino elegida y un diagrama del subgrafo usado (con km y, si cabe, h de cada ciudad).

**Pareja elegida:** `Oradea` (origen) → `Eforie` (destino).

![Subgrafo Oradea → Eforie](evidencias/grafo%20busqueda%20informada%20ejercicio%201.png)

- Camino de A*: Oradea → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest → Urziceni → Hirsova → Eforie.
- Camino de Greedy: Oradea → Sibiu → Fagaras → Bucharest → Urziceni → Hirsova → Eforie.
- El punto donde discrepan es en **Sibiu**: A* baja por Rimnicu Vilcea, Greedy por Fagaras.

**h(ciudad) hacia Eforie** (distancia euclidiana):

| Ciudad | h |
|---|---|
| Oradea | 513 |
| Sibiu | 391 |
| Fagaras | 301 |
| Rimnicu Vilcea | 349 |
| Pitesti | 253 |
| Bucharest | 166 |
| Urziceni | 120 |
| Hirsova | 64 |
| Eforie | 0 |


### 2. Tabla comparativa con Path, Depth, Cost, Expanded (y la heurística usada).

Heurística en ambos: distancia euclidiana a Eforie.

| Algoritmo | Status | Path | Depth (carreteras) | Cost (km) | Expanded | Generated |
|---|---|---|---|---|---|---|
| Greedy best-first | success | Oradea → Sibiu → Fagaras → Bucharest → Urziceni → Hirsova → Eforie | 6 | 730 | 6 | 18 |
| A* | success | Oradea → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest → Urziceni → Hirsova → Eforie | 7 | 698 | 11 | 32 |

### 3. Reporte

**¿A\* encontró el camino de menos km? ¿Greedy coincidió o se desvió?**

Sí, A* encontró el camino de menos km (698 km). Greedy no coincidió, se desvió porque devolvió un camino de 730 km, o sea, 32 km más caro. Aunque el camino de Greedy tiene menos carreteras (6 vs 7 de A*) tener menos tramos no significa menos km.

**¿Por qué Greedy puede devolver un camino más caro aunque h sea admisible?**

Porque Greedy ordena la frontera solo por h(n) e ignora el costo acumulado g(n). En Sibiu tiene que elegir entre Fagaras (h=301) y Rimnicu Vilcea (h=349). Como Fagaras "se ve más cerca" de Eforie en línea recta (h menor), Greedy la elige, aunque el tramo real por ahí termine costando más km. Que h sea admisible solo garantiza que no sobreestima la distancia al destino; no garantiza que el algoritmo que solo mira h elija el camino más barato, porque no toma en cuenta lo que ya gastó (g).

A* en cambio usa f = g + h. En Sibiu compara Fagaras (g=250, h=301, f=551) contra Rimnicu Vilcea (g=231, h=349, f=580). Aunque Fagaras tiene menor f en ese momento, al continuar la búsqueda A* descubre que el costo real total por Rimnicu Vilcea y Pitesti es menor y determina que el óptimo es de 698 km.

**En el camino de A*, ¿f tiende a no disminuir a lo largo de la ruta? Relaciónalo con que h sea consistente.**

Sí. Mirando la tabla g/h/f de A*, f va: 513, 542, 580, 581, 595, 634, 676, 698. Es no decreciente a lo largo del camino. Esto pasa porque h es consistente, ya que, al avanzar una carretera, lo que sube g se compensa con lo que baja h, así que f nunca disminuye. Esta propiedad es la que garantiza que A*, con h consistente, no tenga que reabrir nodos y devuelva el camino óptimo en km.

**Nota sobre nodos expandidos:** Greedy expandió menos nodos (6 vs 11 de A*), es decir "trabajó menos", pero a cambio pagó un camino más caro. A* explora más porque considera el costo real, y ese esfuerzo extra es lo que le permite encontrar el óptimo.

### 4. Evidencias de haber ejecutado Greedy, A* y el listado de heurísticas.

**Listado de heurísticas — `ejecucion_02_heuristics.txt`** (`python 02_heuristics.py --from-city Oradea --to Eforie`)

```text
Heuristic: Euclidean distance to Eforie (map coordinates)

  h(n)  city
      0  Eforie  <- goal
     64  Hirsova
    120  Urziceni
    160  Vaslui
    166  Bucharest
    188  Giurgiu
    231  Iasi
    253  Pitesti
    290  Neamt
    301  Fagaras
    309  Craiova
    349  Rimnicu Vilcea
    391  Sibiu
    397  Mehadia
    397  Drobeta
    406  Lugoj
    482  Timisoara
    511  Arad
    513  Zerind
    513  Oradea  <- start
```

**Greedy best-first — `ejecucion_03_greedy_best_first_search.txt`** (`python 03_greedy_best_first_search.py --from-city Oradea --to Eforie`)

```text
Algorithm: Greedy best-first search
Problem:   Oradea → Eforie
Heuristic: Euclidean distance to Eforie (map coordinates)
Status:    success
Path:      Oradea → Sibiu → Fagaras → Bucharest → Urziceni → Hirsova → Eforie
Depth:     6 roads
Cost:      730 km

  city                  g     h     f
  Oradea                   0   513   513
  Sibiu                  151   391   542
  Fagaras                250   301   551
  Bucharest              461   166   627
  Urziceni               546   120   666
  Hirsova                644    64   708
  Eforie                 730     0   730

Expanded:  6 nodes
Generated: 18 nodes
Frontier:  max size 7
```

**A\* — `ejecucion_04_a_star_search.txt`** (`python 04_a_star_search.py --from-city Oradea --to Eforie`)

```text
Algorithm: A* search
Problem:   Oradea → Eforie
Heuristic: Euclidean distance to Eforie (map coordinates)
Status:    success
Path:      Oradea → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest → Urziceni → Hirsova → Eforie
Depth:     7 roads
Cost:      698 km

  city                  g     h     f
  Oradea                   0   513   513
  Sibiu                  151   391   542
  Rimnicu Vilcea         231   349   580
  Pitesti                328   253   581
  Bucharest              429   166   595
  Urziceni               514   120   634
  Hirsova                612    64   676
  Eforie                 698     0   698

Expanded:  11 nodes
Generated: 32 nodes
Frontier:  max size 6
```
