Trivial case: 
All the bookings have the same hotel(one destination)

The premerge function on the first stage - merge  is a variant of FFD(first fit decreasing) for bin packing prolbem. 

+ It is a variant in the sense that it follows a first fit decreasing but it doesn't iterate all the packatble bookings for one trip. (it covers all the shared hotel)
+ For a classical FFD, the approximation ratio of FFD is $F F D(S, C) \leq 11 / 90 P T(S, C)+6 / 9$ and it is tight
+ If we want to do a classical FFD, we could:
	+ computing the compatible group for each booking
	+ start with any booking and try to pack a trip with all its compatible booking 





$\mathcal{B}$: all the bookings as input
$\mathcal{T}$: all the input trips, any trip is a subset of bookings
$\mathcal{A}$: Areas
$\mathcal{V}$: vehicles v.cost, v.capacity

$b_i \in \mathcal{B}$, $a_i \in \mathcal{A}$, $T \subset \mathcal{B}$

find an assignment of bookings, i.e. $\sigma: b \mapsto T$, such that

[Bin packing](https://en.wikipedia.org/wiki/Bin_packing_problem)
[Bin pakcing approx ratio](https://www.researchgate.net/figure/1-Summary-of-heuristics-for-the-Bin-Packing-Problem_tbl1_265974871)