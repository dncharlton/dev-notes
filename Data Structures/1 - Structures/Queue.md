---
tags:
  - data_structures
  - python
---
A "list" where new items are added to the tail and items are removed from the head
Queues have the following functions:
- queue.push(item)
	- adds an item to the tail of the queue
- queue.pop(item)
	- removes and returns an item from the head of the queue
- queue.peek()
	- returns an item from the head of the queue
- queue.size()
	- returns the number of items in the queue

Queues denote the `tail` at index `[0]` and the `head` at index `[-1]`
- `-> [tail, item, item, item, head] ->`

Big O complexity of all functions are primarily `O(1)` unless you are trying to get an item from the tail of the queue then it can reach up to `O(1)`

## Python
Python does not have native queue implementation hence we need to create a queue class:

```python
class Queue:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.insert(0, item)

    def pop(self):
        if len(self.items) == 0:
            return None
        temp = self.items[-1]
        del self.items[-1]
        return temp

    def peek(self):
        if len(self.items) == 0:
            return None
        return self.items[-1]

    def size(self):
        return len(self.items)
```

