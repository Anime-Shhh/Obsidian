Given a target V, you need to find the least amount of coins needed to sum to that solution.
Ex: V=17 Sol = [10, 5, 1, 1] so 4 coins

## [[Greedy Solution]]
** Important** you can only use greedy if you have unlimited amount of coins for each denomination. 
1. initialize result as empty
2. Find the largest denomination less than V, add that to result until result + denomination goes over target. 
3. Decrement the denomination
4. repeat the previous steps until result == target

code:
```python
res = V
count = 0
denoms = [1, 5, 10, 25]

i = len(denoms)-1
while i > -1:
	curr_denom = denoms[i]
	
	while res >= curr_denom:
		res -= curr_denom
		count += 1
	
	i -= 1
	
	if res == 0:
		break

if res != 0:
	print("greedy failed)
else:
	return count
```

This will only work for unlimited coins of each denomination.
**Proof**: 
Let's say you have 1 quarter, 3 dimes, and 5 pennies. And you want to make 30 cents:
Greedy output: \[25, 1, 1, 1, 1, 1] which is 6 coins (1 quarter and 5 pennies)
Dynamic approach/Optimal approach: \[10 ,10, 10] which is 3 dimes


## [[Dynamic Programming]]

Problem:
Given denominations d\[1 . . . k] and an integer N . Write a DP algorithm to compute the minimum number of coins required to make the sum N . If impossible, return –1.


**Assuming that denominations are sorted. Idk if it matters but assuming that anyways**
Code:
```python
dp = [float("inf")] * (N+1)
dp[0] = 0
#ex: denoms=[1,5,20] N=26
for d in denoms:
	for i in range(1, len(dp))
		curr = i//d
		r = dp[i%d]
		if (curr + r) < dp[i]:
			dp[i] = curr + r

if dp[N] == float("inf"):
	return -1
else:
	return dp[N]

```


Chat is telling me this is wrong but its hallucinating me being wrong with test cases that work.
Imma leave this as is. **Cross check with someone in class**