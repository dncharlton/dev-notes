---
tags:
  - data_structures
  - tree
---

Trees aren't particularly useful data structures unless they're ordered in some way. One of the most common types of ordered tree is a [Binary Search Tree](https://en.wikipedia.org/wiki/Binary_search_tree) or `BST`. In addition to the properties we've already talked about, a binary tree has some additional constraints:

1. Instead of a list of children, each node has at most 2 children, a right and a left child
2. The left child's value must be less than its parent's value
3. The right child's value must be greater than its parents
4. No two nodes in the BST can have the same value

![[Tree Binary.png]]

Average insert complexity:
- `O(log(n))`

BST Depth:
- level 0 - search 1 node
- level 1 - search 2 nodes
- level 2 - search 4 nodes
- level 3 - search 8 nodes
- level 4 - search 16 nodes
- level 5 - search 32 nodes
- level 6 - search 64 nodes
- level 7 - search 128 nodes
- level 8 - search 256 nodes
- level 9 - search 512 nodes
- level 10 - search 1024 nodes
- `O(log(n))` where n is the number of nodes is the depth of the tree
Therefore we only need 10 steps to reach a desired element of a 1024 size tree or 11 steps for a size of 2048

### Types of Binary Trees:
- [[Balanced tree]]
- [[Unbalanced Tree]]
- [[Red-Black Tree]]

## Python

```python
class BSTNode:
    def __init__(self, val=None):
        self.left = None
        self.right = None
        self.val = val

    def insert(self, val):
        # If the current value is empty, set the value
        if not self.val:
            self.val = val
            return

        # If the current value is the new value to be inserted, skip
        if self.val == val:
            return

        # If the new val is less than the node, set to left or traverse further
        if val < self.val:
            if self.left is None:
                self.left = BSTNode(val)
                return
            self.left.insert(val)
            return

        # only other option is that it is greater than current node 
        # and add or travel further or
        if self.right is None:
            self.right = BSTNode(val)
            return
        self.right.insert(val)
        return

	def get_min(self):
        min = self
        while min.left is not None:
            min = min.left

        return min.val

    def get_max(self):
        max = self
        while max.right is not None:
            max = max.right

        return max.val

    def delete(self, val):
        # return none if nothing is there
        if self.val is None:
            return None

        # if delete val is less than current val
        if val < self.val:
            # and left val not empty
            if self.left:
                # delete left val
                self.left = self.left.delete(val)
            # return self
            return self
            
        # if delete val is more than current val
        if val > self.val:
            # and right val not empty
            if self.right:
                # delete right val
                self.right = self.right.delete(val)
            # return self
            return self
        # if right is empty return left
        if self.right is None:
            return self.left

        # if left is empty return right
        if self.left is None:
            return self.right

        # with node delete being the current node, 
        # we find the minimum node on the right and place it onto the current node
        # then we replace current node with minimum right node, then we delete 
        # the minimum right node
        min_larger_node = self.right
        while min_larger_node.left:
            min_larger_node = min_larger_node.left
        self.val = min_larger_node.val
        self.right = self.right.delete(min_larger_node.val)
        return self

    def preorder(self, visited):
        if self.val is not None:
            visited.append(self.val)
            
        if self.left is not None:
            self.left.preorder(visited)
            
        if self.right is not None:
            self.right.preorder(visited)
            
        return visited

    def postorder(self, visited):
        if self.left is not None:
            self.left.postorder(visited)
            
        if self.right is not None:
            self.right.postorder(visited)
            
        if self.val is not None:
            visited.append(self.val)
            
        return visited

    def inorder(self, visited):
        if self.left is not None:
            self.left.inorder(visited)
            
        if self.val is not None:
            visited.append(self.val)
            
        if self.right is not None:
            self.right.inorder(visited)
            
        return visited

    def exists(self, val):
        if self.val == val:
            return True

        if val < self.val:
            if self.left is None:
                return False
            return self.left.exists(val)

        if self.right is None:
            return False
        return self.right.exists(val)
```

