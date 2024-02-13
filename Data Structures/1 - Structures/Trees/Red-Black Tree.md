---
tags:
  - data_structures
  - tree
---

![[Red-Black Tree.png]]
A  red-black tree is a kind of self-balancing binary search tree. Each node stores an extra bit, which we will call the color, red or black. The color ensures that the tree remains approximately balanced during insertions and deletions.

When the tree is modified, the new tree is rearranged and repainted to restore the coloring properties that constrain how unbalanced the tree can become in the worst case.

1. Each node is either red or black
2. The root is black. This rule is sometimes omitted. Since the root can always be changed from red to black, but not necessarily vice versa, this rule has little effect on analysis.
3. All `Nil` leaf nodes are black.
4. If a node is red, then both its children are black.
5. All paths from a single node go through the same number of black nodes to reach any of its descendant `NIL` nodes.

## Python
```python
class RBNode:
    def __init__(self, val):
        self.red = False
        self.parent = None
        self.val = val
        self.left = None
        self.right = None

class RBTree:
    def __init__(self):
        self.nil = RBNode(None)
        self.nil.red = False
        self.nil.left = None
        self.nil.right = None
        self.root = self.nil

    def rotate_left(self, x):
        if x == self.nil or x.right == self.nil:
            return
        y = x.right
        x.right = y.left
        if y.left != self.nil:
            y.left.parent = x

        y.parent = x.parent
        if x.parent is None:
            self.root = y
        elif x == x.parent.left:
            x.parent.left = y
        else:
            x.parent.right = y
        y.left = x
        x.parent = y

    def rotate_right(self, x):
        if x == self.nil or x.left == self.nil:
            return
        y = x.left
        x.left = y.right
        if y.right != self.nil:
            y.right.parent = x

        y.parent = x.parent
        if x.parent is None:
            self.root = y
        elif x == x.parent.right:
            x.parent.right = y
        else:
            x.parent.left = y
        y.right = x
        
        x.parent = y

    def insert(self, val):
        newNode = RBNode(val)
        newNode.parent = None
        newNode.left = self.nil
        newNode.right = self.nil
        newNode.red = True

        parent = None
        current = self.root

        while current != self.nil:
            
            parent = current
            if newNode.val < current.val:
                current = current.left
            elif newNode.val > current.val:
                current = current.right
            else:
                return
        newNode.parent = parent
        if parent is None:
            self.root = newNode
        elif newNode.val < parent.val:
            parent.left = newNode
        else:
            parent.right = newNode

        self.fix_insert(new_node)

    def fix_insert(self, new_node):
        while new_node != self.root and new_node.parent.red:
            if new_node.parent == new_node.parent.parent.right:
                u = new_node.parent.parent.left
                if u.red:
                    u.red = False
                    new_node.parent.red = False
                    new_node.parent.parent.red = True
                    new_node = new_node.parent.parent
                else:
                    if new_node == new_node.parent.left:
                        new_node = new_node.parent
                        self.rotate_right(new_node)
                    new_node.parent.red = False
                    new_node.parent.parent.red = True
                    self.rotate_left(new_node.parent.parent)
            else:
                u = new_node.parent.parent.right

                if u.red:
                    u.red = False
                    new_node.parent.red = False
                    new_node.parent.parent.red = True
                    new_node = new_node.parent.parent
                else:
                    if new_node == new_node.parent.right:
                        new_node = new_node.parent
                        self.rotate_left(new_node)
                    new_node.parent.red = False
                    new_node.parent.parent.red = True
                    self.rotate_right(new_node.parent.parent)
        self.root.red = False
```

