# What is dynamic programming?

#### A method for solving complex problems
* by breaking down into simpler subproblems
* solve subproblems and store their solution to avoid recomputing

#### 3 important concepts:
* Optimal substructure 
* Recursive function
* Memoization

### Activity Selection Problem:




### Log Cutting Problem:
You have a log of length _n_. For each possible cut position _l_ (1 through n), you are given a value _vi_ representing how much value you receive if you cut that piece. 

Ex:

| Value | Length |
| ----- | ------ |
| 1     | 1      |
| 5     | 2      |
| 8     | 3      |
| 9     | 4      |
| 10    | 5      |
Greedy approach would be: take highest value/length cut first


# Land allocation problem([[Knapsack Problem]])

As opposed to the previous Greedy Solution, you cannot do fractional pieces of land



### brute force solution
* given a lost of all possible combinations of plots
``` 
Sol = {} and max = -1

for each possible set S of plots,
	if cost(S) > B:
		continue
	else:
		if (Area(S) > max)
			Sol = S and max = Area(S)
``` 
