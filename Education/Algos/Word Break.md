Problem:
Given a String S (as a array of characters(list)) and a dictionary where if you give the inputs dict(i,j) it'll return whether S\[i:j] is a valid substring that is in dict. Words in dict can be used more than once. Return whether the string S can be partitioned into substrings


## [[Dynamic Programming]]
Solution:
1. create a cache dp[] and initialize all of the indices with False, True will be only when there is a substring word that is in dict and works all the way to the end of the array S
2. Base Case 
3. reversely traverse through the String with i, and check if there is a substring from dict that exists from i to i+word length. 
	1. ensure that there is enough room for that check, like i might be n-1 and the word length is 7, which will elad ot a out of bounds check.
4. if it exists, then set the dp[] of that equal to the dp[] of i + len(word) since by recursion,      dp\[i+len(word)] will already be set to True since in order for dp\[i] to work, the dp\[i+len(word)] also needs to a valid word from the dict, which is also checked previously when the reverse iteration reached to i+len(word).
5. once you initialize a dp\[i] to be true, just have another check below to avoid more unnecessary checks of other words in dict
```python
	if dp[i]:
		break
```
5. return if dp\[0] is True or false
code:
```python

dp = [False] * (len(S)+1)
dp[len(S)] = True

for i in range(len(S) - 1, -1, -1)
	for word in wordDict:
		if (i+len(word)) <= len(S) and S[i:i+len(word)] == word:
			dp[i] = dp[i+len(word)]
		#ensure that once one solution is found, it doesnt keep looking for more
		if dp[i]:
			break

return dp[0]
```

essentially, you're making a cache named dp which works backwards and stores what indices have valid solutions

Runtime:
O(n) for traversing through the array S






My code and attempt:

```python
#dict(i,j) gives a boolean of whether it is a word or not in O(1)
dp = [False] * (len(S)+1)
dp[0] = True

for j in range(1, len(S)+1);
	for i in range(0:j):
		if dp[i] and dict(i:j):
			dp[j] = True
			break # we found a solution, no need to check mroe
			
return dp[len(S)]
```

Runtime: O(n^2)