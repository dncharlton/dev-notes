---
tags:
  - algorithm/search
  - python
---
![[Search Animations.gif]]

- `O(log(n))`
-  Fast sorting algorithm, memory heavy as it needs a single copy of the array
## Pseudo-code
```
function binary_search(A, n, T) is
    L := 0
    R := n − 1
    while L ≤ R do
        m := floor((L + R) / 2)
        if A[m] < T then
            L := m + 1
        else if A[m] > T then
            R := m − 1
        else:
            return m
    return unsuccessful
```

## Python
```python
def binary_search(target, arr):
    l = 0
    r = len(arr)-1

    while l <= r:
        m = (l+r)//2
        if arr[m] < target:
            l = m + 1
        elif arr[m] > target:
            r = m - 1
        else:
            return True
    return False
```
