A hiker starts at altitude 0 and wants to reach a mountaintop at altitude n. There are campsites at various pre-sorted altitudes. The hiker can climb at most m vertical feet at a time before needing to rest at a campsite.

## [[Greedy Solution]]
1. if not given sorted list of increasing elevations campsites, then sort them
2. Let m be the elevation you can climb before giving up
3. have the climber climb to the next highest campsite that is <= m elevation
4. if the hikers position + m >= N, which is the top of the mointain, just have them get to the top

code
```python
pos, stops, i = 0, 0, 0
# C is the list of campsites sorted
# m is the max steps the hiker can take
while pos < N:
	if pos + m >= N:
		break
	let j = some index >= i where C[j] <= pos + m
	# in other words, the campsite at index j is the next biggest possible climb
	if c[j] > (pos + m):
		print("climb not possible")
	else:
		pos = c[j]
		stops += 1
		i = j+1
	
```

**Proof**:
Let O be the optimal solution which has one less step than Greedy which is G. with i being 0, the index of the first campsite. G:(g1, g2, ... gk) and O:(o1, o2, ot) where t\<k since O takes less stops

**Base case:** 
j=0 (the first campsite sorted by elevation)
By the greedy solution, G would choose the campside that is the farthest away from the current position but less than m. so g1(the first stop) while O also chooses some stop before m. Since Greedy contition chooses the furthest one possible: m>=g1>=o1

**Inductive step**:
Lets assume the same goes for the the next t-1 steps. Meaning that the greedy approach will always choose a campsite >= optimals campsite. We want to prove that gt>=ot>=N
since ot-1 and gt-1 are such that gt-1 is >= ot-1 , this means that when the next campsite is chosen, g will choose one that is the greatest stop possible <= m. And it will also choose a campsite that is >= ot since ot can also take at most m steps more, which is also the limit for greedy solution. since gt-1 is equal to or higher than ot-1, g can make the same amount of steps or greater than o since they both can go the max of m steps while g can take more than or equal to the steps that o takes. By this logic, if ot takes the hiker to the top, then gt can also take the hiker to the top, which means that greedy solution takes the same amount of steps to get tot eh top as optimal. Thus, by contradiction, we prove that the greedy solution is optimal