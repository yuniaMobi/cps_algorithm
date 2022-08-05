+ for each trip t1:
	+ iterates over t1's compatible trip tk
		+ swap area -> {(t1', tk', ....)|( t1', tk', ...) > (t1, tk, ...)} k = 2,3,4,....n
		+ combine combinable trips (up to 2) -> (t1, ti, tj, tk, ...) -> (t1+ti+tj, tk, ...)
		+ dissipate t1 to other trips (exhaust trip)

+ check feasibility
+ self.trips <- best
	+ remove best.old_trip

t1 -> t1' (swap area / combine/exhaust) (t1 deleted)
 -> t1' t1'' (subtle operations)

t1 -> subtle operations
connectivity of paths




remove best.old_trips in self.trips

exhaust_trip:
rearrange origianl trips by designating t1's bookings to other viable trips

for each booking b1 in t1:
	find best viable t2 to cover b1
		viable += t2'
		modified += t2' (for comparison)
		new += t2' (improved more than once)
new += final_trip <- rest groups (form a trip with the rest groups)
new candiate(new, modified)