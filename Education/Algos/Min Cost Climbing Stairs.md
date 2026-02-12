Problem:
Given stars of size n. Just given n. And given a array c where each index of c corresponds to the cost of taking that step at index i. You can take either 1 or 2 steps at a time.

## [[Dynamic Programming]]

Solution:
1. Initialize dp\[] of size n and have all values be -1
2. Initialize dp\[0] = 0 and dp\[1] = c\[1]
3. now iterate i through 2 to n and set dp\[i] to be min(dp\[i-1], dp\[i-2]) + c\[i]
4. finally return dp\[n] which will have the minimum cost to that step


code:
```python
dp = [-1] * (n+1)
dp[0] = 0
dp[1] = c[1]

for i in range(2, n+1):
	dp[i] = min(dp[i-1], dp[i-2]) + c[i - 1]
	
if dp[n] != -1:
	return dp[n]
```

Runtime: O(n) since you're just going over all the n steps