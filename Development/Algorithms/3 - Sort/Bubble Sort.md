---
tags:
  - algorithm/sort
  - python
---

- `O(n*n)`
	- Min: `O(n)`
	- Max: `O(n*n)`

## Python
```python
def bubble_sort(nums):
    swap_occured = True
    while swap_occured:
        swap_occured = False
        for i in range(1, len(nums)):
            if nums[i-1] > nums[i]:
                nums[i], nums[i-1] = nums[i-1], nums[i]
                swap_occured = True
    return nums
```
