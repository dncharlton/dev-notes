---
tags:
  - data_structures
  - python
---
##### Graphic:
![[Graph.png]]
##### Table Example:
| |0|1|2|3|4|
|---|---|---|---|---|---|
|0|false|true|false|false|true|
|1|true|false|true|true|true|
|2|false|true|false|true|false|
|3|false|true|true|false|true|
|4|true|true|false|true|false|
##### Array Format:
```python
[
  [False, True , False, False, True ],
  [True , False, True , True , True ],
  [False, True , False, True , False],
  [False, True , True , False, True ],
  [True , True , False, True , False]
]
```


## Python
```python
class Graph:
    def __init__(self, num_vertices):
        self.graph = [[False for j in range(num_vertices + 1)] for i in range(num_vertices + 1)]    

    def add_edge(self, u, v):
        self.graph[u][v] = True
        self.graph[v][u] = True

    # don't touch below this line

    def edge_exists(self, u, v):
        if u < 0 or u >= len(self.graph):
            return False
        if len(self.graph) == 0:
            return False
        row1 = self.graph[0]
        if v < 0 or v >= len(row1):
            return False
        return self.graph[u][v]

```