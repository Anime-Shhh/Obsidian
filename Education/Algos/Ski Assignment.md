Given a list of people's heights P and a list of ski heights S, both with length n. Figure out a way to assign skis to each person such that you have the minimize the average person height and ski height difference. Essentially, minimize the absolute sum of differences 
### [[Greedy Solution]]
1. First you would sort the peoples heights
2. Sort the ski heights
3. For i=1 through n, assign all i indices the same person and ski.

code 
```python
P.sort()
S.sort()
assignments = {}
abs_diff = 0
for i in range(len(S)):
	assignments[P[i]] = S[i]
	abs_diff += abs(P[i]-S[i])
	
print(abs_diff)
print(assignments)
```

**Proof**:
Sorting both lists in increasing order and assigning the shortest person the shortest ski, and the second shortest person the second shortest ski, and so on, will lead to the least absolute sum in differences. Assigning the shortest ski to the shortest person minimizes the height difference. Let's say if the shortest person was given the second shortest ski, there might be a chance that the height difference is less, but due to that exchange, the second shortest person would get the shortest ski, which would result in a larger difference, and thus a larger sum of differences.
**Important**: Swapping pairs will not deter the difference since you are just exchanging assignments, but if you were to do any other arrangement, it would cause a larger sum of differences
