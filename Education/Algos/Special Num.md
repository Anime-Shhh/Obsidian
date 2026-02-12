A number is defined as special if it satisfies the following:
```
n = 197(a) + 232(b)
```
given n, find out the minimum combination of a and b, if any.


## [[Dynamic Programming]]
Code:
```python
indices = [float("inf")] * (n+1) #used to see when a or b are used
last = [-1] * (n+1) #used to retrace steps
indices[0] = 0
for i in range(n+1):
	if indices[i-197] + 1 < indices[i] and i >= 197:
		indices[i] = indices[i-197] + 1
		last[i] = 197
	if indices[i-232] + 1 < indices[i] and i >= 232:
		indices[i] = indices[i-232] + 1
		last[i] = 232

if indices[n] == float("inf"):
	return "no solution"

a = b = 0
curr = n
while curr > 0:
	if last[curr] == 197:
		curr -= 197
		a += 1
	else:
		curr -= 232
		b += 1

return (a, b)
	
```

I dont really get it, no proof or explanation Just memorize this


Notes:
* last\[] is essentially a cache so that helps you backtrack
* indices\[] also does the same, it keeps track of how many of the numbers have been used


### Runtime:
O(n) for initializing indices and last according to the numbers
