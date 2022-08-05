Given a route $1,2,3,4,...,7,8..$, output the best route with minimal total distance.


#### pseudo code
```text
procedure 2optSwap(route, v1, v2) {
    1. take route[0] to route[v1] and add them in order to new_route
    2. take route[v1+1] to route[v2] and add them in reverse order to new_route
    3. take route[v2+1] to route[end] and add them in order to new_route
    return new_route;
}
```


#### example
Here is an example of the above with arbitrary input:
-   Example route: A → B → E → D → C → F → G → H → A
-   Example parameters: v1=1, v2=4 (assuming starting index is 0)
-   Contents of new_route by step:
    1.  **(A → B)**
    2.  A → B → **(C → D → E)**
    3.  A → B → C → D → E → **(F → G → H → A)**