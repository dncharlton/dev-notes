---
tags:
  - algorithm/sort
  - "#python"
---


## Python
```python
def selection_sort(nums):
    for i in range(len(nums)):
        smallest_index = i
        for j in range(i + 1, len(nums)):
            if nums[j] < nums[smallest_index]:
                smallest_index = j
        nums[i], nums[smallest_index] = nums[smallest_index], nums[i]
    return nums
```
