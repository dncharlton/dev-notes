---
tags:
  - data_structures
---
An abstract data type that represents a set of vertices and the edges that connect those vertices.
## PROPERTIES
- Graphs can have between `0` and `n` vertices, there's no maximum
- Graphs can have between `0` and `~n^2` edges, where `n` is the number of vertices
- Vertices don't need to be connected at all (they can have no edges). That said, they may be unreachable if this is the case
- An edge connects exactly 2 vertices, and there can't be 2 edges between the same two vertices.
- Some graphs (called weighted graphs) assign a "cost" to each edge. For example, if a graph represented a geographical map of cities in the real world, the cities would be vertices and the edges would be roads. The weight on the roads could be their lengths. We won't be using weighted graphs for now.

Complete Graph - Where all vertices all connected by edges
- `edges = (vertices * (vertices/2))/2`
	- 2 vertices -> 1 edge
	- 3 vertices -> 3 edges
	- 4 vertices -> 6 edges
	- 5 vertices -> 10 edges
		- 4 + 3 + 2 + 1
	- 6 vertices -> 15 edges
		- 5 + 4 + 3 + 2 + 1

![[Adjacency Matrix]]

![[Adjacency List]]

![[Breadth First Search (BFS)]]

![[Depth First Search (DFS)]]