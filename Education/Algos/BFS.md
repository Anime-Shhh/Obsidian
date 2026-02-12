Explores all vertices of a graph level by level. starting from root. then all neighbors of root, then all its neighbors, and so on.
It uses a **Queue** to keep track of the next vertex to explore

code
```python
bfs(graph, start):
	visited = []
	visited.add(start)
	queue.append(start)
	
	while queue is not empty:
	node = queue.remove()
	process(node)
	for neighbor in getNeighbors(graph, node):
		if neighbor not in visited:
		visited.add(neighbor)
		queue.append(neighbor)
```

BFS Shortest Path
```python
bfs_shortest_path(graph, start):
	map_dist = {start: 0} and queue = []
	queue.add(start)
	while queue is not empty:
		u = queue.remove()
		for v in getNeighbors(graph, u):
			if v not in getKeys(map_dist):
				map_dist.add({v, map_dist.getvValue(u) + 1})
				queue.append(v)
	return map_dist
```