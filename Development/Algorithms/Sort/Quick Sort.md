---
tags:
  - algorithm/sort
  - python
---

- `O(n*log(n))` to `O(n^2)`
- An already sorted list results in `O(n^2)`to solve this we can:
	- Shuffle: Shuffle the list before hand and **practically ensure** `O(n*log(n))`
	- Median: Choose the median of three elements e.g. start, end, middle. This is then used as the pivot. This approach **cannot** break down to `O(n^2)`
- **Pros:
	- Very fast in the average case
	- In-Place: Saves on memory, doesn't need to do a lot of copying and allocating
- Cons:
	- More complex implementation
	- Typically unstable: changes the relative order of elements with equal keys**

## Python
```python
def quick_sort(nums, low, high):
    if low < high:
        nums, p = partition(nums, low, high)
        nums = quick_sort(nums, low, p - 1)
        nums = quick_sort(nums, p + 1, high)
    return nums

def partition(nums, low, high):
    pivot = nums[high]
    i = low
    for j in range(low, high):
        if nums[j] < pivot:
            nums[i], nums[j] = nums[j], nums[i]
            i += 1
    nums[i], nums[high] = nums[high], nums[i]
    return nums, i
``` 
