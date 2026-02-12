[[Backtracking]]
Goes as far as possible following the deepest path for each branch. Then uses either a stack or recursive function to go back when it reaches the end of a path

code
```python
DFS(node):
	if node is None:
		return ""
	if node.data == "Image.png"
		return "found"
	for child in node.children:
		DFS(child)
```
Time complexity:
O(n), since lets say a tree has n nodes, each one is getting checked