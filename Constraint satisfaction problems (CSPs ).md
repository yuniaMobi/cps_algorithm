Constraint satisfaction problems on finite domains are typically solved using a form of [search](https://en.wikipedia.org/wiki/Search_algorithm "Search algorithm"). The most used techniques are variants of [backtracking](https://en.wikipedia.org/wiki/Backtracking "Backtracking"), [constraint propagation](https://en.wikipedia.org/wiki/Constraint_propagation "Constraint propagation"), and [local search](https://en.wikipedia.org/wiki/Local_search_(optimization) "Local search (optimization)"). These techniques are also often combined, as in the [VLNS](https://en.wikipedia.org/wiki/Very_large-scale_neighborhood_search "Very large-scale neighborhood search") method, and current research involves other technologies such as [linear programming](https://en.wikipedia.org/wiki/Linear_programming "Linear programming").[[14]](https://en.wikipedia.org/wiki/Constraint_satisfaction_problem#cite_note-14)

[Backtracking](https://en.wikipedia.org/wiki/Backtracking "Backtracking") is a recursive algorithm. It maintains a partial assignment of the variables. Initially, all variables are unassigned. ==At each step, a variable is chosen, and all possible values are assigned to it in turn. For each value, the consistency of the partial assignment with the constraints is checked; ==in case of consistency, a [recursive](https://en.wikipedia.org/wiki/Recursion "Recursion") call is performed. When all values have been tried, the algorithm backtracks. In this basic backtracking algorithm, consistency is defined as the satisfaction of all constraints whose variables are all assigned. Several variants of backtracking exist. [Backmarking](https://en.wikipedia.org/wiki/Backmarking "Backmarking") improves the efficiency of checking consistency. [Backjumping](https://en.wikipedia.org/wiki/Backjumping "Backjumping") allows saving part of the search by backtracking "more than one variable" in some cases. [Constraint learning](https://en.wikipedia.org/wiki/Constraint_learning "Constraint learning") infers and saves new constraints that can be later used to avoid part of the search. [Look-ahead](https://en.wikipedia.org/wiki/Look-ahead_(backtracking) "Look-ahead (backtracking)") is also often used in backtracking to attempt to foresee the effects of choosing a variable or a value, thus sometimes determining in advance when a subproblem is satisfiable or unsatisfiable.

[Constraint propagation](https://en.wikipedia.org/wiki/Constraint_propagation "Constraint propagation") techniques are methods used to modify a constraint satisfaction problem. More precisely, ==they are methods that enforce a form of [local consistency](https://en.wikipedia.org/wiki/Local_consistency "Local consistency"), which are conditions related to the consistency of a group of variables and/or constraints. ==Constraint propagation has various uses. First, it turns a problem into one that is equivalent but is usually simpler to solve. Second, it may prove satisfiability or unsatisfiability of problems. This is not guaranteed to happen in general; however, it always happens for some forms of constraint propagation and/or for certain kinds of problems. The most known and used forms of local consistency are [arc consistency](https://en.wikipedia.org/wiki/Arc_consistency "Arc consistency"), [hyper-arc consistency](https://en.wikipedia.org/wiki/Hyper-arc_consistency "Hyper-arc consistency"), and [path consistency](https://en.wikipedia.org/wiki/Path_consistency "Path consistency"). The most popular constraint propagation method is the [AC-3 algorithm](https://en.wikipedia.org/wiki/AC-3_algorithm "AC-3 algorithm"), which enforces arc consistency.

[Local search](https://en.wikipedia.org/wiki/Local_search_(optimization) "Local search (optimization)") methods are incomplete satisfiability algorithms. They may find a solution of a problem, but they may fail even if the problem is satisfiable. They work by iteratively improving a complete assignment over the variables. ==At each step, a small number of variables are changed in value, with the overall aim of increasing the number of constraints satisfied by this assignment.== The [min-conflicts algorithm](https://en.wikipedia.org/wiki/Min-conflicts_algorithm "Min-conflicts algorithm") is a local search algorithm specific for CSPs and is based on that principle. In practice, local search appears to work well when these changes are also affected by random choices. An integration of search with local search has been developed, leading to [hybrid algorithms](https://en.wikipedia.org/wiki/Hybrid_algorithm_(constraint_satisfaction) "Hybrid algorithm (constraint satisfaction)").


SAT  Boolean satisfiability problem