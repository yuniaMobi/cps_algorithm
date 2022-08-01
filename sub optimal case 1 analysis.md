trip 53 bus 55 bus 77 taxi (see file 'optimization improvement example 1')
![[optimization improvement example 1.pdf]]
This is potentially resulted from how we handling local search swap_area()

Recall in our optimizer, we handles trips as followed:

step 1: generate candidates
[see codes](https://github.com/takemobiteam/tui-continuous-planning-system/blob/main/cps/planning_engine/local_optimizer.py#L334-L341)
```text
for any trips pair t1, t2:
	candiates <- swap any two compatible areas in between t1 and t2
	candidates <- try to combine t2 and a third trip into t1
	candidates <- try to disspate t1 to other trips (exhaust)
```
step 2: sort the candidate and yield a best trip
step 3: For best trip's old trip, we only retain the best trip and kill all the other potentials from this old trip. (even a third swap might result in an optimal).
[see codes](https://github.com/takemobiteam/tui-continuous-planning-system/blob/main/cps/planning_engine/local_optimizer.py#L376-L383)
for any old trip resulted in current best trip:
	remove old trip itself
	remove any candidates originated from this old_trip

From the beginning, we know we can get to the optimal through two area swaps. For example, if we first swap_area(trip 53, trip 55) AND RETAIN THE RESULT which swap Maria Studios (from 55) with Altantica Eleon Grand (from 53). Then in the next optimization run, we have another area swap swap_area(trip 53, trip 77) and might yield a solution which swap Plessas Palace (from 77) with TUI BLUE Zante Maris (from 53). But if as our optimize does, if the first swap between 53 and 55 yield a best trip which is not the same as the above first swap, then the solution with the above first swap would be killed in step 3. 

Generally speaking, if an optimal solution is not monotonically cost-reducing from pair-wise swapping, there is a risk that we kill the path to the optimal too early.

![[sub optimal case 1.jpg]]






