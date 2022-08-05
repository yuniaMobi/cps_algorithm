### progress

#### algorithm analysis
[x] psedo code of optimize() ✅
+ analysis (psedo code + complexity) of optimize() main loop is 70% completed.
+ operations analysis
	[x] premerge ✅  
	+ area/trip level
		[x] swap_area ✅
		[x] combine_trip ✅ 
		[x] exhaust_trip ✅ 

	+ hotel/booking level
		[x] syphoon booking ✅
		- [ ] taxi_split (need help to understand)
		[x] swap_hotel ✅

#TODO:
	polish and push to github

#### case analysis
[x] case 1 53 55 77 ✅
[doing] 3 other cases

#### algorithm improvement
+ see 'local search algorithm draft.md'
+ 2-step local operations: Based on the analysis of case 1, we might want to add 2-local operation. for example, for swap area, we might want to repeat swap area twice to generate candiates then choose the best.
+ [discussion] add swap booking: based on case 1, it seems that a constructed variant of case 1 could create trouble for our production model due to lacking of swap booking (see case 1 53 55 57.md disctussion section )

#### formalization
[x] formalization1 ✅ set covering + segmentation
[x] formalization2 ✅ variant of CVRP
[x] formalization3 ✅ variant of CVRP
	
#TODO
[] add graph to formalization 2 & 3
[???] formalize validation constraints, i.e. all the testing functions in code base and trip.feasible() (around 20-30?)
