### Algo design techniques:
#### greedy
* fractional knapsack
* Activity selection
* interval partitioning
* graph traversal: BFS
* spanning tree: prims and kruskal algo
* single source shortest path: dijkstras algo
* max flow problem: ford-fulkerson algo
#### dynamic
* 0-1 knapsack
* weighted activity selection problem
* subset problem
* single source shortest path: bellman-ford algorithm

#### divide and conquer
* binary search: Binary search
* Sorting: Quick sort and merge sort
* Finding k'th smallest number: using median of medians
* Closest Pair of points
* Analysis:
	* typical recurrence form for div and conq is this:
	* T(n) = aT(n/b) + f(n)
	* where a is # of sub problems
	* n/b is size of each subproblem
	* f(n) is time to divide and combin

#### backtracking:
* Dominos chain
* k-Vertex coloring (k>2)
* Finding maximum independent set
* Finding minimum vertex cover

#### reduction to known polynomial problems:
* Bipartite matching to max flow
* edge disjoint paths to maxflow
* mincut to maxflow
* vertex-disjoint paths to edge-disjoint paths
* Edge-disjoint paths to vertex-disjoint paths
* Circulation of maxflow




* P complexity class: Decision problems for which there is a poly time algorithm
* NP Complexity class: Decision problems for which there is a poly-time certifier
* EXP Complexity class: Decision problme sfor which there is an exponential-time algorithm
* *NP completeness* = NP as well as NP-Hard


Preparation guidelines:
* Understand, not memorize and focus on why algos work, not what makes them correct
* learn to prove why certain algos dont work and why. like providing counterexamples


#### **Example problems:**
1. Can the matching problem be solved optimally on a general(non-bipartite) graph using reduction to MaxFlow problem? True/False? provide explanation if true, counterexample if false.
2. Given the array A[1..n] heights of n buildings, a peak is an index 1 < i < n such that A[i] >= A[i-1] and A[i] >= A[i+1] design a divide and conqur algo to find a peak, any one.
	1. Ans: initial thought was to just go in incriments/windows of size 3 to see if the middle is a peak. Actual answer would use binary search, that way u dont have to do O(n) time in case the peak is the last one
3. You are given a set of n tasks, each represented as a vertex vi, each task has a start time si and a end time ei. two tasks are connected by an edge if they overlap in time.   continued in image
4. show that the Set cover problem is NP-Complete (vertex cover problem too)
5. Find minimum vertex cover on a given tree. Design a DP solution(optimal substructure, recurrence function, pseudocode, time complexity and space complexity analysis)

Fractional knapsack problem (packinb)


***** study up on residual graphs and why theyre needed, and also min cut
