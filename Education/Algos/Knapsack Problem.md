Given items and their corresponding sizes and value, you need to decide the optimal arrangement/selection of items such that you get the maximum value out of them without going over your capacity
## [[Greedy Solution]] Approach
![[Pasted image 20250925191749.png]]
!!**There is a slight variation though, you are able to select fractional size as well, you dont need to get the full size of the item!!

Greedy approaches:
1. Choose the smallest size item at every step
![[Pasted image 20250925192402.png]]
2. Choose the greatest value at every step
![[Pasted image 20250925192609.png]]

However, None of these are the optimal greedy approaches. Instead you can make a new column in which you calculate the **value per size ratio** for that item and take the best fractional value at each step per item

### Optimal Solution:
![[Pasted image 20250925193253.png]]
As you can see, instead of going by size or value, if you go by the largest **value per size** for each step, you will get a marginally better solution than the other solutions. Like in this case, the **value per size** greedy solution gave 23.18 whereas prioritizing value gave 23.1 and the other gave something even less(look above)

### !!! IMPORTANT !!! The greedy approach only works when fractions are allowed



## [[Dynamic Programming]] Approach
### Optimal solution:
* The time complexity is #pseudo_polynomial


The dynamic solution would would create a table of size items and weight. It would fill the table such that every row would be the items and then in that row, every column would be the capacity, increasing by one . And every entry would be the maximum amount of weight for that given bag size (prioritized by value). For instance, imagine this table below

![[Pasted image 20251001182855.png]]

Here is what it looks like for the land allocation version:

![[Pasted image 20251001195417.png]]


Solution:



code:
```python
# max weight = B
# weights = weigths
# vals = values


n = 4  # rows/number of items
B = 5  # columns

arr = [[0 for _ in range(B+1)] for _ in range(n+1)]

for i in range(1, n+1):
	w = weigths[i-1], v = vals[i-1]
	for j in range(1, B+1):
		if w > j:
			arr[i][j] = arr[i-1][j]
		else:
			arr[i][j] = max(arr[i-1][j], v + arr[i-1][j-w])
			
			
return arr[n][B]
```