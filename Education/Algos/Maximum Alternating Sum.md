Given a list of numbers, you want to make the largest amount of groups such that each group is alternating: odd, even, odd, even. 
For instance, given A=\[3,6,1,3,7], the resulting optimal groups would be: \[3], \[6], \[1], \[3, 7]

## [[Greedy Solution]]
1. set a check for odd and even as a number and have it alternate. odd = 1, even = 0
2. traverse through the list of numbers
3. if the current number % 2 is check, then make it a group and add it to the solutions list
4. if it doesnt == check, then move on to the next number in the list and add it to the previous number and repeat the check
5. switch the check
6. repeat the previous steps
7. return the list of answers


code
```python
check = 1 # odd = 1, even = 0
curr_sum = 0
curr_nums = []
answers = []
for num in nums
	curr_sum += num
	curr_nums.append(num)
	if curr_sum % 2 == check:
		answers.append(curr_nums)
		curr_sum = 0
		curr_nums = []
		check = check^=1
		
```

**Proof:** 
Since you need to classify 



## Optimized code(more space)
code:
```python
check = 1 # odd = =1, even = 0
odds = []
evens = []
groups = []
temp_group=[]
for num in nums:
	if num%2 == 1:
		odds.append(num)
	else:
		evens.append(num)
	
while True:
	if check == 1:#odd
		if odds:
			groups.append([odds.pop()])
			check ^= 1
		else:
			break
	else: #even
		if evens:
			groups.append([evens.pop()])
			check ^= 1
		elif odds and len(odds)>1:
			n1, n2 = odds.pop(), odds.pop()
			groups.append([n1, n2])
			check ^= 1
		else:
			break

return groups
```