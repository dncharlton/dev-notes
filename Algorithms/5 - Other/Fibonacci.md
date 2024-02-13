---
tags:
  - algorithm/problem
  - python
---

# Slow Fibonacci
## Python
```python
def fib(n):
    if n == 0 or n == 1:
        return n
    return fib(n - 1) + fib(n - 2)
```

# Fast Fibonacci
## Python
```python
def fib(n):
    if n <= 1:
        return n
    current = 0
    parent = 1
    grandparent = 0
    for i in range(0, n - 1):
        current = parent + grandparent
        grandparent = parent
        parent = current
    return current
```
