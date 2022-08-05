#### formalization progress
+ a second formalization -> OR variants of CVRP
+ known results: apporximation algorithm of CVRP $\alpha$ + 1 >= 2 ($\alpha$ is the approximation ratio of TSP)
+ (academic) constant 1.2 1.5 2 time polynomial time complxity


#### Information
+ how long we could afford to wait for a solution? <=15 mins
+ the number of hotels: 1000
+ the number of bookings 10,000

hotels: could be 1000, in most case around 300
hotel_areas: 20, 30 (hotels within one hotels areas are close)

#### algorithm progress
Two main directions:
1 IP: integer programming
2 local search
	+ intractable, but it performs quite well in most of case
+ Key to design local search algorithm:
	+ connectivity analysis: check if there exist a path from initial to optimal, regardless of time.
	+ force the solution cost to decrease in each local search.

Implement:
+ c++ python(numpy itertool.product)