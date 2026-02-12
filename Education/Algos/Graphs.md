**Unweighted Graphs**: The rgaph's edges have no weights.
* Ex: In a social network, the edges are just connections signifying whether a person is connected to another or not. No reason

**Weighted edges**: The edges have weights
* Ex: Social interaction networks. people are verticies connected by eges representing how many times they have collaborated together

**Directed Graphs**: Edges have directions (representing one way interactions)
* Example: Online follower networks: users are vertices and a directed edge from one user A to another User B represents that user A follows user B

**simple graphs**: No self loops (edges from a vertex to itself)

**Tree graph**: Formally known as acyclic connected graph. Special requirements:
* It is connected: There is a path between every pair of vertices
* It has no cycles: There is no way back to start at a vertex and follow sequences of edges that lead back to it
* Min and max edges is (n-1) where n is the amount of vertices
* Ex: A directory 
* Traversal: [[DFS]] and [[BFS]]

[[Dijkstra's Algorithm]]