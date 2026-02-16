# Binary Tree

A **Binary Tree Data Structure** is a hierarchical data structure in which each node has at most two children, referred to as the left child and the right child.

It is commonly used in computer science for efficient storage and retrieval of data, with various operations such as insertion, deletion, and traversal.

## Important Terminology

### Node

A node is a single element or object that contains:

- Data
- Reference to Left Child Node
- Reference to Right Child Node

### Edges

An edge is the line connecting two nodes. It is the link between parent and child.

### Root

The top node of a binary tree is called its root node.

### Children

Children of a node are the nodes directly connected below it.

Each node can have at most two children.

- Left Child
- Right Child

### Leaf Node

A leaf node in a binary tree is a node that has no children.

### Subtree

A subtree is a smaller tree that forms from a node and all of its descendants.

### Ancestors

The ancestors of a node are all the nodes above it on the path from the root to that node.

## Applications of Binary Tree

### 1. Database Indexing

### 2. File Systems

### 3. Fast Searching

### 4. Autocompletion

### 5. DOM in HTML

### 6. Routing Algorithms

### 7. Compression Algorithms

## Types of Binary Trees

### Full Binary Tree

Every Node must have either zero or two children.

### Complete Binary Tree

All levels must be competely filled except the last one and the last level must have all nodes m-left as possible.

### Perfect Binary Tree

All leaf nodes are at the same level.

### Balanced Binary Tree

Height of the tree should be at maximum of log(N) where N is the number of nodes.

### Degenerate Tree

Every Node only has a single child.  
We can also call it a Singly Linked List.

## Binary Tree representation in code

### Python

```
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None
```
