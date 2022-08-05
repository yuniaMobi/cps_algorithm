Problem setting (capacitated vehicle routing problem)

$G=(V, E)$ : A graph showing the location and route of the customer (or, booking)
$V=\{0,1, \ldots, n\}$ : A collection of nodes represeting hotels. The node that represents the Depot (airport) is 0 , and the nodes that represent each customer are 1 to $\mathrm{n}$
$E$ : Set of Edges connecting each node $e_{i j}=(i, j)$
$K=\{1,2, \ldots,|K|\}:$ Set of vehicles
$s_{i} \geq 0$ : size of booking $i$, i.e. number of customers w.r.t booking $i$.
$Q_k \geq 0$ : Maximum vehicle capacity (Not all vehicles have the same maximum capacity $\mathrm{Q}$ )
$d_{i j}$ : Travel distance between hotel $i$ and $j$ (distance between $i$ and $j$ )
$c_k$: cost of vehicle $k$, proportional to its capacity $Q_k$

A decision variable that indicates whether the vehicle $k$ has taken the route $e_{i j}:  \quad x_{i j}^{k}= \begin{cases}1 & \text { taken } \\ 0 & \text { Not taken }\end{cases}$

[CVRP formalization](https://how-to.aimms.com/Articles/332/332-Formulation-CVRP.html)
[CVRP another formalization](https://medium.com/jdsc-tech-blog/capacitated-vehicle-routing-problem-cvrp-with-python-pulp-and-google-maps-api-5a42dbb594c0)
[Bin packing](https://en.wikipedia.org/wiki/Bin_packing_problem)
[Bin pakcing approx ratio](https://www.researchgate.net/figure/1-Summary-of-heuristics-for-the-Bin-Packing-Problem_tbl1_265974871)


permutation
exchange
vehicle


+ Minimize cost
	$\min \sum_{k \in K} \sum_{(i, j) \in E} c_k + d_{i j} x_{i j}^{k}$
+ Each hotel should be vistied at least once
	$\sum_{k \in K} x_{i j}^{k}\geq 1$ $\forall j \in V \backslash\{0\}$
+ constraint which means “the number of vehicles coming in and out of a location is the same”
	$\sum_{i \in V, i \neq j} x_{i j}^{k}-\sum_{i \in V} x_{j i}^{k}=0 \quad \forall j \in V, \forall k \in K$
+ constraint which means “the delivery capacity of each vehicle should not exceed the vehicle's maximum capacity”
	$\sum_{i \in V} \sum_{j \in V \backslash\{0\}, i \neq j} s_{j} x_{i j}^{k} \leq Q_k \quad \forall k \in K$
+  constraint for “removal of subtours”
	$\sum_{k \in K} \sum_{(i, j) \in S, i \neq j} x_{i j}^{k} \leq|S|-1 \quad S \subseteq V \backslash\{0\}$
+ $\quad x_{i j}^{k} \in\{0,1\} \quad \forall k \in K, \forall(i, j) \in E$

branching bound (?)
