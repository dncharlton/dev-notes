---
tags:
  - data_structures
---

| 0   | connects with | 1   | 4   |     |     |
| --- | ------------- | --- | --- | --- | --- |
| 1   | connects with | 0   | 2   | 3   | 4   |
| 2   | connects with | 1   | 3   |     |     |
| 3   | connects with | 1   | 2   | 4   |     |
| 4   | connects with | 0   | 1   | 3   |     |

## Python

```python
class Graph:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u in self.graph.keys():
            self.graph[u].add(v)
        else:
            self.graph[u] = set([v])
        if v in self.graph.keys():
            self.graph[v].add(u)
        else:
            self.graph[v] = set([u])

    def edge_exists(self, u, v):
        if u in self.graph and v in self.graph:
            return (v in self.graph[u]) or (u in self.graph[v])
        return False

    def unconnected_vertices(self):
        unconnected = []
        for key, value in self.graph.items():
            if len(value) == 0:
                unconnected.append(key)
        return unconnected

    def adjacent_nodes(self, node):
        return list(self.graph[node])

```

