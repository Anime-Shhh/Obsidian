### 1. **Decide whether you think the following statement is true or false. If it is true, give a short explanation. If it is false, give a counterexample.**
 
#### a. Let S be the solution of the Fractional [[Knapsack Problem]] with n items using the greedy strategy of picking as much of the items as possible according to highest value/cost until the budget is exhausted. If you add a constant value v > 0 to all the n items, the new solution obtained by the same greedy strategy is the same as S.

**Solution**: in this case you can just give a counterexample.

Lets say that **vi** is the original value and **wi** is the original weight and then **v** is the constant value added. Lets take the scenario

| Item   | Value | Weight |
| ------ | ----- | ------ |
| Item 1 | 51    | 100    |
| Item 2 | 1     | 2      |
Now lets say we added v = 9 to both of them, this would result in the ratio of Item 1 going from 0.51 to 0.6 but the other one would become 5 now, and because of this the order would be changed and so would the greedy solution
**This is ==False==** 
** solved **

#### b. In the Activity Selection Problem, an alternative optimal greedy strategy is as follows: Let x be the class with the earliest start time and let y be the class with the second earliest start time. If x and y are disjoint, choose x and recurse on everything but x. If x completely contains y, discard x and recurse. Otherwise, discard y and recurse. 

**Solution**:
The general solution is this: The classic optimal greedy solution: sort activities by **earliest finish time** and repeatedly pick the next activity with earliest finish that does not conflict with the already chosen ones. That runs in O(nlog⁡n) for the sort plus O(n) to scan — overall O(nlog⁡n).

now in the new proposed problem:
There are 3 cases:
**Case 1** — x and y are disjoint, meaning that x's finish time is less than or equal to y's start time
* This solution claims that if x finishes before or equal to y's start time, then x should be chosen and the problem keeps recursing on everything but x
* This will never not lead to a non optimal solution because choosing x will never lead to a non-optimal solution
* Since all start times besides x start are >= y's start time >= x's finish time, this means that there is no downside to choosing x since it will always lead to 1 more activity being chosen

**Case 2** - x completely contains y (sx <= sy and fx >= fy)
* This case claims that x should be discarded and y should be used instead and continue recursing on the remaining options
* Let's say that there is an optimal solution that contains x **OPT**.
* Our solution, which chooses y will not lead to a solution that is less optimal than **OPT**. 
* Since every activity that is compatible with x starts after or equal to when x ends, and since x also finish's after or equal to when y finishes, this means that any activity that is compatible with x is also compatible with y, meaning that choosing y will never lead to a solution less optimal than **OPT**
* So the proposed solution still stands
**Case 3** - x and y overlap but neither contain each other so sx <= sy and fx < fy
* this case claims that it is safe to discard y and continue by choosing x and recursing on everything but x and y
* So, the counterargument to this would claim that if x and y overlap but neither contain each other, then you should discard x and choose y, so lets try to disprove that.
* since x and y overlap, x is not in **OPT**
* for every other activity z, is in **OPT** which has y, has a sz >= sy since we have claimed that y is the 2nd earliest start time, so every other activity after that must start at the same time or after
* now lets take the next activity after y, there are 2 cases for that activity z:
	* **Case a**: z compatible with y
		* This means that sz is >= fy and since fy>fx that means z is also compatible with x.
	* **Case b**: z not compatible with y
		* this means that z overlaps. So sz < fy and we also need to say that sz < fx (since we are assuming that x is not in the optimal solution) and by doing this, it means z is not compatible with either y or x. so under the assumption that x is not in the **OPT**, y is not chosen in this case, and neither is x, so any activity that conflicts with x also conflicts with y.
* This means that there exists an optimal solution that uses x instead of y and still has the same cardinality, so this means that discarding y is safe
**So this part is ==true==**

** Solved **

#### c. Interval partitioning and activity selection problems can be solved by the same greedy strategy – earliest finish time first

**Solution:**

### unsolved !!!


#### d. n the Activity Selection Problem, if each activity has a value, and the goal is to maximize the total sum of values of the selected activities (instead of maximizing the number of activities), then repeatedly choosing the highest-valued activity that does not conflict with the already chosen ones always yields an optimal solution.

**Solution:**

Simply give a counterexample:
lets say these were the given times and values;
* A: [1,10] V(A) = 100
* B: [1,5] V(A) = 70
* C: [5,10] V(A) = 60

As you can see, choosing the highest value first does not yield the optimal solution
The answer is ==**False**==

** Solved **

#### e. The greedy highest-denomination-first strategy for the Coin Change (Canonical Systems) problem is guaranteed to remain optimal when the supply of each de- nomination is limited, whenever a solution exists. For instance, suppose you have only 1 penny (1¢), 4 nickels (5¢), and 1 dime (10¢), and you need to make 16¢, the greedy strategy yields the optimal result, minimizing the number of coins required, which is 3 in this case.

**Solution:**

This can also be proven by just a counter example:

Lets say you have the following:
* 1 quarter (.25)
* 3 dimes (0.1)
* 0 nickels (0.05)
* 5 pennies (0.01)

Let's say you were tasked with gathering .30. In this case, the highest denomination first method would not work since that would yield 6 coins(1 quarter and 5 pennies) whereas the optimal solution is 3 times

So the answer is ==**False**==

** Solved **

#### f. n the Caching Problem, if a memory location is never be requested again in the future, evicting it from the cache cannot decrease the total number of cache misses

This can also be proven with a concrete counterexample:

Lets say that the cache has a fixed size of 2 and it currently contains [A,B] and A is to be never accessed again but B is. There are 2 cases of the cache misses in the future sequence of C,B:
* **Case 1**: Cache misses, there is no C, so B is removed and C is loaded(bad choice):
	* Miss count = 1. Now C is accessed, but now B is also missing so thats another cache miss. Now miss count = 2
	* ==final miss count = 2==
* **Case 2:** Cache misses, there is no C, A is removed and C is loaded(good choice):
	* Miss count = 1. Now C is accessed, and then B is also accessed. 
	* ==final miss count = 1==
As you can see, evicting the memory location that will never be used again resulted in less cache misses. Proof by contradiction

** Solved **


#### g. In the Minimizing Maximum Lateness problem with n assignments, each with a deadline and a time required for completion, if all assignments have the same deadline but possibly different times required for completion, any ordering of the assignments gives the same maximum lateness.

This is ==**True**.== 

Since all the jobs have the same deadline **D**, this means that the maximum lateness depends on when the last job is done. No matter how you arrange all the jobs, they will all have the same combined time. And the lateness = combined time - **D**

** solved **

#### h. In the Minimizing Maximum Lateness problem with n assignments, if all assignments require the same time to complete but have different deadlines, then any ordering of the assignments yields the same maximum lateness. 

Lets say 2 assignments are as follows:
* A: T(A) = 5, D(A) = 5
* B: T(B) = 5, D(B) = 10

In this case, the ordering does matter, if I do B first and then A, I will be late by 5. But if I do A first, then I get A done on time, and B as well, so I am not late

This is **==False==**

** solved **

### 2. A set of n intervals is given, each with a start time and a finish time. The task is to find a proper coloring of n intervals. In other words, assign a color to each interval so that any two overlapping intervals are always assigned different colors. Provide a greedy strategy to compute the minimum number of colors needed to properly color a given set of n intervals. Provide a formal proof of correctness and analyze the time complexity of your algorithm.


Here is the logic by which to solve:
1. Sort the interval pairs [S,F] by start time in increasing order and break ties by whichever finish time is first
2. set up a min heap and have it maintain the top of the heap be the task that has the earliest end time.
3. iterate through the intervals in increasing:
	```
	let curr = [s,f]
	if h and h.top().finishtime() <= s:
		h.pop() 
		s.color = h.pop's color
		h.append(s,c) 
	else:
		s.color =  # assign new color
		push(s, c)
	```

##### Time complexity:
* Sort = n(logn)
* iteration = n
* insertion and removal from heap = (log k) where k < n
Overall time: n log n

### 4.  A server has n customers waiting, each requiring a known service time ti. The total waiting time for all customers depends on the order they are served. The total waiting time is calculated as T = sum of n and i=1(time spent waiting by customer i).
##### (a) Design an efficient greedy algorithm to determine the service order that minimizes this total waiting time.
Sort by shortest serving time first. Serve in that order.
##### (b) Provide a formal proof of correctness for your algorithm. (Hint: use the exchange argument). 
Not formal proof but heres the explanation:
The wait time for each person, k, depends on the sum of all the wait times of people from 1 up to k - 1. If you do any other order, lets say greatest first, the person who should have been served in 2 minutes now has to wait for lets say the largest order which takes an hour before hand. 
##### (c) Analyze the time complexity of your algorithm.
Sorting takes n log n and iterating through them all is n
so tottal time is n log n

### 5. 


### 6. A hiker starts at altitude 0 and wants to reach a mountaintop at altitude n. There are campsites at various pre-sorted altitudes. The hiker can climb at most m vertical feet at a time before needing to rest at a campsite.
##### (a) Design a greedy algorithm to find the sequence of campsites the hiker should visit to minimize the number of stops.
```
# let n be top of mountain
pos = 0
stops = 0
i = 1 # index of campsites
while pos < N:
	if pos + m >= N:
		break #you can reach the top directly
	let j = some number >= i where c[j] <= pos + m #feasable climb
	if c[j] > pos + m:
		Not a possible climb
	else:
	pos = c[j]
	i = j+1
	stops += 1

return stops
```
##### (b) Provide a proof of correctness for your algorithm. A proof by contradiction is a suitable approach.
##### (c) Analyze the time complexity of your algorithm.
O(n) for n campsites if everyone is visited. no time wasted sorting