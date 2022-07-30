
Denote

$$
\begin{align}
c_i: & \text{volumn of client } i \\
v_j: & \text{vehicle capacity of vehicle }j  \\
f_j: & \text{operation fee of vehicle } j\\

y_j: & y_j =
	\begin{cases}
      1 & \text{if vehicle $j$ is put into use}\\
      0 & \text{otherwise}
    \end{cases} \\
Y_{jk}: & Y_{jk} =
	\begin{cases}
      1 & \text{if vehicle $j$ covers location $k$}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi^V_{ij}: &\chi^V_{ij} =
	\begin{cases}
      1 & \text{if client $i$ is assigned to vehicle $j$}\\
      0 & \text{otherwise}
    \end{cases} \\
\alpha^L_{ik}: &\alpha^L_{ij} =
	\begin{cases}
      1 & \text{if client $i$ has location $k$ as destination}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi_{C(TSP)}: &\chi_{C(TSP)} =
	\begin{cases}
      1 & \text{if combination C of location is picked}\\
      0 & \text{otherwise}
    \end{cases} \\
\end{align}
$$
Given $c$ client volumn, $v$ vehicle capacity, $f$ operation fee of each vechicle , $\alpha$ requirement of clients, $C(TSP)$ the outcome of TSP.  the goal is to minimize the total cost
$$ \text{COST} = \sum_j f_j\cdot y_j 
$$
while satisfies
$$
\begin{align}
\chi^V_{ij} + \chi^V_{i'j} & = 1 \qquad \text{if $i$ and $i'$ are incompatible}\\
\sum_i\chi^V_{ij} & = 1 \qquad \\
\sum_jc_i \cdot \chi^V_{ij} &\leq v_j \qquad v_j \in V \\
\sum_{k \in \chi_{C(TSP)}} \chi_{C(TSP)} & \leq \chi_{ik}^L
\end{align}
$$
The constraints are based on the following consideration:
0. incompatible clients are 互斥
1. Each client is required to be picked up by a vehicle
2. Each client's destination (location) request should be met by any route
3. Each vehicle's capacity should not be exceeded.


Concerns:
The number of the third constraints could be exponential due to the exponetial combination of different locations into different route for a vehicle. (There are ways to handle this).