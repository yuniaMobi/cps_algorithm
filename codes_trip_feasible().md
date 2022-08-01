
bookings in one trip before premerge are compatible.
compatible is defined by

premerge:
	merge trips based on shared hotel or shared hotel.area

-> 
For any premerged trip $\forall t_i$,  any bookings belong to trip $t_i$, i.e. $\forall b_{j_1}^i, b_{j_2}^i \in t_i$ , $b_{j_1}^{i}$ shares the same hotel.area with $b_{j_2}^i$


$t_1$ and $t_2$ are combinable iff any booking pairs in $t_1$ and $t_2$ are compatible

$t_1$ and $t_2$ are compatible iff there exist at least one booking pair in $t_1$ and $t_2$ are compatible



self.trips = set (t1, t2, t3). 
new trips, t4 belongs to new trips
rearrage t4 with its compatible trips (maybe t1,t2,t3) --> 1st for loop

iterate existing trips t1 t2 t3 and try to rearrange them with their own compatible groups intersection with existing trips(i.e self.trips)

Issue: some generated candiate(s) coincide with some old trips from other candidates
Question: is it possible from the generation process that we just eliminate those coincidence? 
c1 == best1.old_trip

$\mathcal{B}$: all the bookings as input
$\mathcal{T}$: all the input trips

one booking one trip -> local optimizer -> pre_merge : a set of trips $t_1, \ldots, t_n$, satisfy:
+ any bookings belong to trip $t_i$, i.e. $\forall b_{j_1}^i, b_{j_2}^i \in t_i$ , $b_{j_1}^{i}$ shares the same hotel.area with $b_{j_2}^i$
+ any bookings belong to different trips $t_i$, $t_j$, don't have shared hotel.area (not right)

t4, t3, t2, t1
43 -> 432 -> 4321 
merge trips as many as possible if
+ they has shared hotel
+ each trip is feasible
	+ what is call a trip is feasible (satisfaction constraits and xxx constraits)

#### feasible check | trip.feasible()
```
def feasible(self):

"""

Check if a trip satisfies constraints

  

Return: bool

empty trip is alwasy feasible

  

customer satisfaction constraints:

max duration constraint

max stops constraint

capacity constraints:

vehicle existance constraint

vehicle capacity constraint

? flight constraint

? booking compactible constraint

"""

  

if len(self.bookings) == 0:

	return True


if self.vehicle is None:

	return False

if self.vehicle.seats > self.hotel_bound:

	return False

if self.seated_pax > self.vehicle.seats * min([b.vehicle_capacity for b in self.bookings], default=1):

	return False

if self.max_grouped_flights != 0 and len(self.flights) > self.max_grouped_flights:

	return False

if self.duration > self.max_time + 300:

	return False

if len(self.hotel_locs) > self.max_stops:

	return False

if not self.skip_b2b:

for b1, b2 in itertools.combinations(self.bookings, 2):

if b1.id not in self.instance.compatible[b2.id]:

return False

return True
```

`
