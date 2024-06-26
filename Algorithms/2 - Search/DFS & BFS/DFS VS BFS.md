---
tags:
  - algorithm/search
  - python
---
## IS THE SOLUTION CLOSE TO THE ROOT?

If you have a good reason to believe the vertex you're looking for is close to the root (where you plan to start searching) then BFS should be faster.
## IS THE GRAPH EXTREMELY WIDE, BUT NOT VERY DEEP (FROM THE ROOT)?

Imagine a tree with `10` vertices on the first level. Each of those ten vertexes point to _another_ ten vertexes. The number of vertices at each level would be:

```
level 0: 1
level 1: 10
level 2: 100
level 3: 1000
level 4: 10000
```

Because BFS stores entire horizontal levels in memory, you may not have enough memory on your machine to execute the search.

## IS THE SEARCH SPACE INFINITE?

In some searches, the graph has infinite size. For example, imagine a simulation of a game of chess.

The first level of the graph would be all the possible current moves, the next level would be all the possible 2nd moves, and this could go on forever, especially when you consider that there are loops within the game. For example, each player could just move their queens back and forth forever.

In these cases, true DFS is practically impossible, you would need to either use BFS, another algorithm, or put a limit on how far your DFS algorithm can search before returning.

## ARE YOU TRYING TO REACH AN "END"?

Think of a maze simulator. You want your algorithm to explore the end of a path before exiting to know if it has hit a dead end. DFS will typically find a solution much more quickly than BFS for this kind of exhaustive search.

![[Depth First Search (DFS)]]

![[Breadth First Search (BFS)]]
