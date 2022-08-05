### Problem setting (variant of CVRP)

Given a map $G=(L, E)$ with a set of locations $L$, a set of bookings $b_i \in \mathcal{B}$ and an unlimited set of vechicle $v_j \in \mathcal{V}$. Each location has a set of bookings to be delivered to. Each booking $b_i$ associate with its seats $s_i$ and locations $l_i \in \mathcal{L}$.  Each vechicle has its own operation fee $f_j$ and capacity $c_j$.
The goal is to select a subset of vechicles, each associates with a path $p_j$ covering a subset of locations $L(p_j) \subset \mathcal{L}$ and for each vechicle, select a subset of clients to be delivered by. The vehicles take its clients to their destinations with minimum cost.

#### Remarks
+ If we have very good CVRP IP solver, we could consider use this formalization to solve the problem.
+ A postprocess is necessary. In classical CVRP, the demand (in our setting, demand of location is the total seats to be delivered to the location) is seperable. But in our case, seats in one booking is not seperable.


### counterpart in codebase
booking <-> booking 
location <-> hotels (or hotel areas)
trip <-> trip
vehicle <-> vehicle

### Annotations
$$
\begin{align}
\text{Constants:} & \\
G:& \text{$G=(L, E)$. A graph showing the location and route of the customer (or, booking)} \\
L: & \text{A collection of locations represeting hotels. The location that represents the Depot (airport) is $0$ .} \\
E : & \text{Set of direct pathes connecting each hotel $e_{i j}=(i, j)$.} \\
V: & \text{$V=\{1,2, \ldots,|J|\}$. Set of vehicles.} \\
s_{i}: & \text{$s_{i}\geq 0$. Seats of booking $i$, i.e. number of customers w.r.t booking $i$.} \\
c_j: & \text{vehicle's capacity (Not all vehicles have the same maximum capacity ).} \\
d_{i j}: & \text{Travel distance between location $i$ and $j$ (distance between $i$ and $j$ ).} \\
f_j: & \text{fee to operate vehicle to manage trip $j$. Fees could be determined by the vehicle's capacity $c_j$, the total distance to travel, the type of vehicle and the location of destinations.} \\
\text{Variables:} & \\
y^T_j: & y^T_j =
	\begin{cases}
      1 & \text{if trip $j$ is selected}\\
      0 & \text{otherwise}
  \end{cases} \\
x_{i i'}^{j}: & \text{A decision variable that indicates whether the vehicle $j$ has taken the route. } \\
x_{i i'}^{j} & = 
	\begin{cases}
	1 & \text { taken } \\
	0 & \text { otherwise}
  \end{cases}
\end{align}
$$

### Formalization (LP)
The goal is to minimize cost:
$$\min \sum_{k \in K} \sum_{(i, i') \in E} (\alpha \cdot f_j + \beta \cdot d_{i i'}  \cdot x_{i i'}^{j}) \cdot y_j$$
While satisfies:
$$\begin{align}
	\sum_{j \in V} x_{i i'}^{j} & \geq 1 \qquad \forall i \in L \backslash\{0\} & (1)\\
	\sum_{i \in L, i \neq i'} x_{i i'}^{j}-\sum_{i \in L} x_{i'i}^{j} & =0 \qquad \forall i, i' \in L, \quad\forall j \in V & (2) \\
	\sum_{i \in L} \sum_{i' \in L \backslash\{0\}, i \neq i'} s_{i} x_{i i'}^{j} & \leq c_j \qquad \forall j \in V & (3) \\
	\sum_{j \in V} \sum_{(i, i') \in S, i \neq i'} x_{i i'}^{j} &\leq |S|-1 \quad S \subseteq L \backslash\{0\} & (4) \\
	x_{ii'}^j & \leq y_j \qquad \forall i, i' \in L, \quad \forall j \in V & (5) \\
	y_j, x_{i i'}^{j} & \in [0,1] \qquad \forall j \in V, \quad\forall(i, i') \in E & (6)	
\end{align}$$
(1) Each hotel should be vistied at least once
(2) Constraint which means “the number of vehicles coming in and out of a location is the same”
(3) Constraint which means “the delivery capacity of each vehicle should not exceed the vehicle's maximum capacity”
(4) Constraint for “removal of subtours”
$\alpha$ and $\beta$ are weights to manually control. 


[CVRP formalization](https://how-to.aimms.com/Articles/332/332-Formulation-CVRP.html)
[CVRP another formalization](https://medium.com/jdsc-tech-blog/capacitated-vehicle-routing-problem-cvrp-with-python-pulp-and-google-maps-api-5a42dbb594c0)
