

$$
\begin{align}
\text{Constants:} &\\
b_i: & \text{seats of booking $i$}\\
v_j: & \text{vehicle capacity of vehicle assigned to trip $j$} \\
\text{Known:} &\\
\mathcal{T}(\mathcal{L}): & \text{a set of trips $T(L)$, $L$ is a combination of locations $\{ l_{i^L_1}, l_{i^L_2}, \ldots, l_{i^L_2} \}$ } \\
\text{Variables:} &\\
f_j: & \text{operation fee of vehicle assigned to trip $j$}\\
c_j: & \text{distance cost of trip $j$}\\

y_j: & y_j =
	\begin{cases}
      1 & \text{if trip $j$ is selected}\\
      0 & \text{otherwise}
  \end{cases} \\
Y_{jl}: & Y_{jl} =
	\begin{cases}
      1 & \text{if booking $j$ has $l$ as destination}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi^{bT}_{ij}: &\chi^{bT}_{ij} =
	\begin{cases}
      1 & \text{if booking $i$ is assigned to trip $j$}\\
      0 & \text{otherwise}
    \end{cases} \\
\alpha^{bL}_{il}: &\alpha^{bL}_{il} =
	\begin{cases}
      1 & \text{if booking $i$ has location $l$ as destination}\\
      0 & \text{otherwise}
    \end{cases} \\
\chi^{TL}_{jl}: &\chi^{TL}_{jl} =
	\begin{cases}
      1 & \text{if trip $j$ covers location $l$}\\
      0 & \text{otherwise}
    \end{cases} \\
\end{align}
$$
Given $b$ as booking $b$'s seat, $v$ as vehicle $v$'s' capacity, $f$ operation fee of each vechicle , $\alpha$ requirement of bookings, $C(TSP)$ the outcome of TSP.  the goal is to minimize the total cost
$$ \text{COST} = \sum_j (f_j + c_j)\cdot y_j
$$
when satisfies
$$
\begin{align}
\chi^{bT}_{ij} + \chi^{bT}_{i'j} & = 1 \qquad \text{if $i$ and $i'$ are incompatible} & (1)\\
\sum_j\chi^{bT}_{ij} & = 1 \qquad & (2)\\
\sum_ib_i \cdot \chi^{bT}_{ij} &\leq v_j \qquad v_j \in V  & (3)\\
\sum_{l \in \chi_{C(TSP)}} \chi_{C(TSP)} & \leq \chi_{ik}^L & (4)
\end{align}
$$
The constraints are based on the following consideration:
1. Incompatible bookings constraint, the more stricter version is $$\chi^T_{ij} \cdot \chi^T_{i'j} = 0$$. It introduces nonlinearity, so in the formalization we adopt the linear one.
2. Each booking is required to be picked up by a vehicle.
3. Each booking's destination (location) request should be met by any route
4. Each vehicle's capacity should not be exceeded.


Concerns:
The number of the third constraints could be exponential due to the exponetial combination of different locations into different route for a vehicle. (There are ways to handle this).