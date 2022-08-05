$t1$


```python
flight_hotel_groups[booking.flight, booking.hotel]

flight_hotel_groups: dictionary
key: [flight, hotel]
val: list of booking which has the flight and hotel as indicated by key


```

booking:
booking.arrival: bool: if it is an arrival or departure

compatibility: dict: key: booking_id, val: bool True/false


Trip:
bookings: list of bookings ==sharing the same flight.terminal.location==, ==flight.terminal.airport.id== and ==arrival/departure state==
instance:?
parameters: ?

trip.flight_hotel_dict: key: flight, hotel; val: booking
trip.flight_hotel_groups = list(trip.flight_hotel_dict.values())
trip.area_dict[booking.hotel.area.id].append(tuple([booking]))
trip.hotel_dict[booking.hotel].append(booking)


flights: all the flights in bookings
max_stops
hotel_groups: all the booking's hotel_groups
hotel_locs: all the booking's hotel_location (aligned)
seated_pax


what is max_num_grouped_flights_departure


#### Trip feasible condition:
	Check if a trip satisfies constraints. Return: bool

+ empty trip is alwasy feasible
+ customer satisfaction constraints:
	+ flight constraint: max_grouped_flight
	+ max duration constraint
	+ max stops constraint
+ capacity constraints(?)
+ vehicle existance constraint
+ vehicle capacity constraint(?)
+ booking compactible constraint : any two of the bookings should be compatible
two compatible -> 3 compatible -> ...?



Questions about functions:

+ local_optimizer\_Trip.get_trip_cost



syphon_bookings:


$b1$ and $b2$ are compatible if:
instance_test_functions = [

exclusive_check
some bookings are exclusive with others means that they are incompatible with others
	+ what is hotel.exclusive? area.exclusive?
	+ what does it do?
based on:
	+ hotel
	+ hotel.area
	+ hotel.area.area_group
	+ tour_operator
	+ tour_operator.tour_operator_group_flight

compatible_distance_check:
	+ dist(b1.hotel, b2.hotel) <= max_time
	+ (arrival and departure has different max_time)

area_compatibility_check: two areas are incompatible means that they are always not arrived within one trip (?)
	+ area_incompatibility_arrival: dict: key: area1, val: areas incompatible w.r.t area 1
	+ area_incompatibility_departure ?

based on hotel.area

  

parametered_test_functions = []

  

test_functions = [

unique_check
check if one of bookings is duplicate, i.e. with the same booking id

combinable_check:
+ if b1 is labeled as is_combinable (True or False)
+ if b2 is labeled as is_combinable (True or False)

separate_terminal_check:
if b1 and b2 share the same filght terminal

depart_arrive_check
if b1 and b2 are both departure or arrival

dossier_code_check, (???)
Only bookings that have the same dossier code (if any) are compatible

interval_overlap_check:
check if flight_time interval overlap

first_flight_check
check if a filght is labeled as first_flight and otherbookings are subsequent (should we check all other bookings' flight time?)

force_pickup_dropoff_check,
b1 and b2 should have the same pickup or dropoff attributes: 
+ force_pickup_time or force_dropoff_time
+ hotel.location
+ flight.terminal.location

But why?

-> premerge 
	do we check compatibility between bookings in one merge (Yes, but just for pairwise)
	bookings in one trip share the same hotel are or same hotel
	bookings in one trip are pairwise compatible
-> optimize (a set of local search)
	+ swap area for all pairwise compatible trips for all areas in these two trips
	+ 

$b_i \in \mathcal{B}$, $h_i \in \mathcal{H}$, $T_i \subset \mathcal{B}_i$
$B_i^{comp} = \{b_j| b_j \sim_{comp} b_i \}$
$T_i^{comp} = \{ T_j| \exists b \in T_j, b \sim_{comp} b' \text{ for } \forall b' \in T_i\}$
+ premerge:
	+ $T_h: \{b_i| h_i = h, h \in \mathcal{H}\}$
	+ 