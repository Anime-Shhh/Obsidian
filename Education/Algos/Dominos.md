Problem: Given a set of n dominos and start and end numbers, find whether it is possibe to make a valid chain that starts and ends with the corresponding given values.
*** You dont have to use all of the dominos in the process, you stop once you find a combo that starts and ends with the given values ***


Assume there are the following vars and funcs for domino d
* d.first: gets the first number in the domino
* d.second: gets the second number in the domino
* d.contains x: sees if the domino contains the number x

``` python
def isChain(S, start, end):
if !S:
	return false
else: 
	for d in S:
	if d.contains(start):
		choose d
		new start = -1
		if d.first==start:
			new_start = d.second
		elif d.second == start:
			new_start = d.first
		if isChain(S, new_start, end):
		return true
		unchoose d
```

Analyze time complexity T(n)
at each level of recursion
* you choose 1 out of n remaining dominos
* Then you make a recursive call on n-1 dominos
T(n) = n T(n-1) + O(1)

**By iteration method:**
time complexity is n!

