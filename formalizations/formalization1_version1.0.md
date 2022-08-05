Given a set of bookings $b_i \in \mathcal{B}$ and a unlimited set of vechicle $v_j \in \mathcal{V}$. Each booking $b_i$ associate with its seats $s_i$ and locations $l_i \in \mathcal{L}$.  Each vechicle has its own operation fee $f_j$ and capacity $c_j$.
The goal is to select a subset of vechicles, each associates with a  $p_j$ covering a subset of locations $L(p_j) \subset \mathcal{L}$ and an assignment of subset of clients. The vehicles take its clients to their destinations with minimum cost.

The following formalization is based on the we have potential paths for vehicles beforehand (see $\mathcal{T}(\mathcal{L})$). 
$$
\begin{align}
\text{Constants:} &\\
s_i: & \text{seats of booking $i$}\\
c_j: & \text{vehicle capacity of vehicle assigned to trip $j$} \\
\gamma^{bL}_{il}: &\gamma^{bL}_{il} =
	\begin{cases}
      1 & \text{if booking $i$ has location $l$ as destination}\\
      0 & \text{otherwise}
    \end{cases} \\
\gamma^{PL}_{pl}: &\gamma^{bL}_{il} =
	\begin{cases}
      1 & \text{if path $p$ covers location $l$}\\
      0 & \text{otherwise}
    \end{cases} \\
\text{Known:} &\\
\mathcal{P}: & \text{a set of paths $p$, $p$ can be represented by a list of locations $\{ l^p_1, l^p_2, \ldots, l^p_{p_k} \}$ } \\
f_j: & f(v_j), \text{ operation fee of vehicle assigned to trip $j$}\\
d_p: & dist_{TSP}(\cup \{ l\}| \chi_{pl} > 0), \text{ total distance cost of path $p$}\\
\text{Variables:} &\\
y^T_j: & y^T_j =
	\begin{cases}
      1 & \text{if trip $j$ is selected}\\
      0 & \text{otherwise}
  \end{cases} \\
y^P_p: & y^P_p =
\begin{cases}
  1 & \text{if path $p$ is selected}\\
  0 & \text{otherwise}
\end{cases} \\
\chi^{bT}_{ij}: &\chi^{bT}_{ij} =
	\begin{cases}
      1 & \text{if booking $i$ is assigned to trip $j$}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi^{TL}_{jl}: &\chi^{TL}_{jl} =
	\begin{cases}
      1 & \text{if trip $j$ covers location $l$}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi^{PT}_{pj}: &\chi^{PT}_{pj} =
	\begin{cases}
      1 & \text{if path $p$ is assigned to trip $j$}\\
      0 & \text{otherwise}
    \end{cases} \\
\end{align}
$$
$$ \text{COST} = \sum_j (\alpha f_j + \beta d_j)\cdot y_j
$$
when satisfies
$$
\begin{align}
\chi^{bT}_{ij} + \chi^{bT}_{i'j} & = 1 \qquad \text{if $i$ and $i'$ are incompatible} & (1)\\
\sum_j\chi^{bT}_{ij} & = 1 \qquad & (2)\\
\sum_is_i \cdot \chi^{bT}_{ij} &\leq v_j \qquad v_j \in V  & (3)\\
\sum_{j} \chi_{ij}^{bT} \cdot \chi_{jl}^{TL} & \geq \gamma_{il}^{bL} & (4) \\
\sum_{p} \chi_{pj}^{PT} \cdot \gamma_{pl}^{PL} & \geq  \chi_{jl}^{TL}  & (5)\\
\chi_{ij}^{bT}  & \leq y^T_j & (6) \\
\chi^{PT}_{pj} & \leq y^P_p & (7)  \\
\end{align}
$$
The constraints are based on the following consideration:
(1) Incompatible bookings constraint, the more stricter version is $$\chi^T_{ij} \cdot \chi^T_{i'j} = 0$$. It introduces nonlinearity, so in the formalization we adopt the linear one.
(2) Each booking is required to be picked up by a vehicle.
(3) Each vehicle's capacity should not be exceeded.
(4) Each booking's destination (location) request should be met.
(5) Each location is visted through pathes that cover it.
(6) Vehicle is selected to pick up bookings.
(7) Path is selected to cover locations.



Concerns:
The number of potential paths could be exponential.