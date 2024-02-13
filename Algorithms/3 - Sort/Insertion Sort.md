---
tags:
  - algorithm/sort
  - python
---

- `O(n^2)` (Worst case)
- Slower than merge sort, however not array copy required
- Why use it?
	- Simple implementation, easy to write
	- Fast for very small data sets
	- Faster than other simple sorting algorithms like Bubble Sort
	- Adaptive: Faster for partially sorted data sets
	- Stable: Does not change the relative order of elements with equal keys
	- In-Place: Only requires a constant amount of memory
	- Online: Can sort a list as it receives it
## Python
```python
def insertion_sort(nums):
    j = 1
    for i in range(len(nums)):
        j = i
        while j > 0 and nums[j-1] > nums[j]:
            nums[j-1], nums[j] = nums[j], nums[j-1]
            j -= 1
    return nums
```
