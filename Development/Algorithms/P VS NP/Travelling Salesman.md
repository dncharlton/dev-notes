---
tags:
  - algorithm/problem
  - python
---

# Brute Force

- tsp -> `O(n!)`
- verify_tsp -> `O(n)`
- NP
## Python
```python
#Brute force all paths between cities until minimum travel distance is hit otherwise return false
def tsp(cities, paths, dist):
    perm = permutations(cities)
    for p in perm:
        d = 0
        for i in range(1, len(p)):
            d += paths[p[i-1]][p[i]]
            # print(path)
        if d < dist:
            return True #return p for path or d for distance
    return False

#Pretty parent function to call helper cleanly
def permutations(arr):
    res = []
    res = helper(res, arr, len(arr))
    return res

#Get all permutations possible for cities
def helper(res, arr, n):
    if n == 1:
        tmp = arr.copy()
        res.append(tmp)
    else:
        for i in range(n):
            res = helper(res, arr, n - 1)
            if n % 2 == 1:
                arr[n - 1], arr[i] = arr[i], arr[n - 1]
            else:
                arr[0], arr[n - 1] = arr[n - 1], arr[0]
    return res

#Second verification of path
def verify_tsp(paths, dist, actual_path):
    d = 0
    for i in range(1, len(actual_path)):
        d += paths[actual_path[i-1]][actual_path[i]]
    return d < dist # return d for actual distance or leave as is for bool
```

