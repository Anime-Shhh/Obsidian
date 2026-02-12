Problem:
You are given an array A\[1 . . . n] of integers, which may contain both positive and negative numbers. A subarray A\[i . . . j] is called a valid continuous subarray when 1 ≤ i < j ≤ n. Write a Dynamic Programming algorithm to find the largest possible sum among all continuous subarrays


## [[Dynamic Programming]]

Solution:
1. initialize a max_sub = \[] which will serve as the max placeholder
2. initialize curr_sum = 0 which serves to see the total of the current subarray being tested
3. iterate through every num in A. add the num to the curr_sum. if curr_sum ends up being less than 0, then set curr_sum to 0.
4. set max_sub to be max(curr_sum, max_sub), this way it will take whatever is higher


code:
```python
A = [-2,1,3,-5,2,5,3,-2] #example
max_sub = A[0]
curr_sum = 0
for n in A:
	if curr_sum < 0:
		curr_sum = 0
	curr_sum += n
	max_sub = max(curr_sum, max_sub)
	
```

