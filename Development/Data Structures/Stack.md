---
tags:
  - data_structures
  - python
---
A "list" where only the top item of the stack can be "accessed" at a time.
Stacks have the following functions:
- stack.push(a)
	- adds an item onto the tail of the stack
- stack.pop()
	- removes and returns an item from the tail of the stack 
- stack.peek()
	- returns an item from the tail f the stack
- stack.size()
	- returns the number of items in the stack

All actions are `O(1)` unless you are trying to retrieve an item not on the top of the stack, then it can reach up to `O(n)` complexity e.g. last item on the stack
## Python
Python does not have a native stack implementation, hence we need a Stack class

```python
class Stack:
    def __init__(self):
        self.items = []

    def push(self, a):
        self.items.append(a)

    def pop(self):
	    if len(self.items) == 0:
		    return None
        return self.items.pop()

    def peek(self):
	    if len(self.items) == 0:
		    return None
        return self.items[-1]

    def size(self):
        return len(self.items)
```

