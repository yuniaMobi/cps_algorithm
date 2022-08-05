
Given a set of bookings $b_i \in \mathcal{B}$ and a unlimited set of vechicle $v_j \in \mathcal{V}$. Each booking $b_i$ associate with its seats $s_i$ and locations $l_i \in \mathcal{L}$.  Each vechicle has its own operation fee $f_j$ and capacity $c_j$.
The goal is to select a subset of vechicles, each associates with a  $p_j$ covering a subset of locations $L(p_j) \subset \mathcal{L}$ and an assignment of subset of clients. The vehicles take its clients to their destinations with minimum cost.

The goal is t
$$
\min \sum_j f_j + dist(p_j)
$$
while satisfies:
+ clients' total seats is within the capacity of their vehicle
+ all the destinations are covered.
+ max distance
+ max locations
+ ....


A ==trip== is an assignment of a subset of bookings, represented by a list: $t_i = [ b_1^i, b_2^i, \ldots, b_{i_n}^i ]$

Given an initial solution $[t_1, t_2, \ldots, t_k]$,
The local operations for a given trip $t = [b_1, b_2, \ldots, b_k]$ includes the following:

+ booking level:
	+ swap booking $b_i^1$ with $b_i^2$ from another trip $t_2$
		$t_1= [b^1_1, b^1_2, \ldots, b^1_{k_1}]$, $t_2= [b^2_1, b^2_2, \ldots, b^2_{k_2}]$  
		$t'_1= [b^2_2, b^1_2, \ldots, b^1_{k_1}]$, $t'_2= [b^2_1, b^1_1, \ldots, b^2_{k_2}]$
	+ insert booking $b_i$ into $t_1$ from another trip $t_2$
		$t_1= [b^1_1, b^1_2, \ldots, b^1_{k_1}]$, $t_2= [b^2_1, b^2_2, \ldots, b^2_{k_2}]$  
		$t_1'= [b^1_1, b^1_2, \ldots, b^1_{k_1}, b^2_s, b^2_{s+1}, \ldots, b^2_t]$, $t'_2= [b^2_1, \ldots, b^2_{s-1}, \ldots, b^2_{t+1}, b^2_{t+2}, \ldots, b^2_{k_2}]$
	+ delete booking $b_i$ from $t2$ and add it to another trip $t_1$
		
+ area level (set level):
	+ insert one area of bookings $\{b^1_i,\ldots\}$ into $t_1$ from another trip $t_2$
	+ delete one area of bookings $\{b^1_i,\ldots\}$ from $t_1$ and add it to another trip $t_2$
	+ swap two area of bookings $\{b^1_i,\ldots\}$ with $\{b^2_i,\ldots\}$ from another trip $t_2$

+ Trip level (?) hotel level