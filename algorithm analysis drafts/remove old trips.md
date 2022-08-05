```python
for t1 in new_trips:

	for t2 in self.compatible_groups[t1].keys(): # preprocessing trips which are compatible for specific trip TODO (Some pairs, at least one pair of different trips satisfy the constraints if being merged)

		candidates += self.swap_areas(t1, t2)

		if t2 in self.combinable_trips[t1.id]: # preprocessing trips which are combinable (likely to be feasible) (All pairs are OK to be merged)

			usable_thirds = self.combinable_trips[t1.id] & self.combinable_trips[t2.id] # TODO bookings compatible vs trips compatible

			for t3 in usable_thirds:

				candidates += self.combine_trips([t1, t2, t3])

	candidates += self.exhaust_trip(t1)
```

for any trips pair t1, t2:
	candiates <- swap any two compatible areas in between t1 and t2
	candidates <- try to combine t2 and a third trip into t1
	candidates <- try to disspate t1 to other trips


```python
for old_trip in best.old_trips:

	if old_trip != self.blank_trip: # ???
	
		self.trips.remove(old_trip)
	
		for candidate in candidates:
	
			if old_trip in candidate.old_trips:
	
				to_remove.add(candidate)
	
candidates = list(filter(lambda c: c not in to_remove, candidates))
```

for any old trip resulted in current best trip:
	remove old trip itself
	remove any candidates originated from this old_trip

this means when we get a current best result from an old trip, we kill all the other potentials from this old trip, even a third swap might result in an optimal.