
## [[Activity Selection Problem]]
Given a list of activities and each activity is given a start and end time, you need to figure out the maximum amount of activities you can do in a day. 

**Constraints**: the activities cannot overlap


## [[Greedy Solution]]:
1. Sort the list of activities by their end time in increasing order. 
2. Traverse through the sorted list, selecting the activity with the earliest finish time, as long it starts after the previously selected activity(if any)
3. repeat steps until you reach the end of the list or you cannot add any more 
4. return the amount of the selected activities

code:
```python
# lets have activities be like this for example:
class activity:
	def __init__(self, start, end):
		self.start = start
		self.end = end
	
activities.sort(key=lambda x:x.end)
sols = []
for activity in activities:
	if sols and activity.start < sols[-1].end
		pass
	else:
		sols.append(activity)
return len(sols)
```

**Proof**: 
Lets say my solution is Greedy and suboptimal, and there is a solution OPT which is optimal.

**Case 1:** Let's say greedy chose activities a1, a2, a3 and OPT chose b1, b2, b3, b4. So OPT is optimal. By the greedy approach, a1, a2, and a3 are the same as b1, b2, and b3. For OPT to have b4, b4 needs to start after or equal to when b3 ends. This is the same logic that greedy follows, so therefore, greedy also must have b4, showing it is optimal.
**Case 2:** Let's say greedy chose activities a1, a2, a3 and OPT chose b1, b2, b3, b4. So OPT is optimal. a1 and b1 are equal, but b2 and a2 are not. This means that greedy is suboptimal. By the greedy strategy, it would choose a2 based on the earliest end time and the fact that the activity starts after a1. By this logic, the only reason a2 would be different than b2 is because a2 ends at the same time or earlier than b2. By this logic, it means that a2 is either the same end time as b2 or before b2. if it is the same as b2, then it matches the OPT solution. Otherwise, a2 ends before b2, which would mean that a2 is more optimal than b2 since it ends earlier than b2, meaning that if a2 and b2 were swapped, OPT would still contain a cardinality of 4, which is what its previous solution was as well. Thus proving that greedy is optimal.