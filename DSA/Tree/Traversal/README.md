# Binary Tree Traversal

## Depth First Search

### Preorder Traversal (root left right)

#### Recursive

```
# Structure of a Binary Tree Node
class Node:
    def __init__(self, v):
        self.data = v
        self.left = None
        self.right = None

# Function to print preorder traversal
def printPreorder(node):
    if node is None:
        return

    # Deal with the node
    print(node.data, end=' ')

    # Recur on left subtree
    printPreorder(node.left)

    # Recur on right subtree
    printPreorder(node.right)

if __name__ == '__main__':
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.right = Node(6)

    printPreorder(root)
```

#### Iterative

Simple Iterative (with stack) [Naive Approach]
O(n) time and O(n) space

```
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None


def preOrder(root):
    res = []
    if root is None:
        return res

    stack = [root]

    while stack:
        curr = stack.pop()
        res.append(curr.data)

        if curr.right:
            stack.append(curr.right)
        if curr.left:
            stack.append(curr.left)

    return res


if __name__ == '__main__':
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)

    preorder = preOrder(root)
    print(' '.join(map(str, preorder)))
```

### In-order traversal (left root right)

#### Recursive

```
class Node:
    def __init__(self, v):
        self.data = v
        self.left = None
        self.right = None

# Function to print inorder traversal
def printInorder(node):
    if node is None:
        return

    # First recur on left subtree
    printInorder(node.left)

    # Now deal with the node
    print(node.data, end=' ')

    # Then recur on right subtree
    printInorder(node.right)

if __name__ == '__main__':
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.right = Node(6)

    printInorder(root)
```

#### Iterative

Using Stack [Naive Approach]

O(n) Time and O(h) Space

```
# Python program to print inorder traversal
# using stack.
class Node:
    def __init__(self, x):
        self.data = x
        self.left = None
        self.right = None

# Iterative function for inorder
# tree traversal
def inOrder(root):
    ans = []
    stack = []
    curr = root

    while curr is not None or len(stack) > 0:

        # Reach the left most Node of the curr Node
        while curr is not None:

            # Place pointer to a tree node on
            # the stack before traversing
            # the node's left subtree
            stack.append(curr)
            curr = curr.left

        # Current must be None at this point
        curr = stack.pop()
        ans.append(curr.data)

        # we have visited the node and its
        # left subtree. Now, it's right
        # subtree's turn
        curr = curr.right

    return ans

def printList(v):
    print(" ".join(map(str, v)))

if __name__ == "__main__":

    # Constructed binary tree is
    #          1
    #        /   \
    #      2      3
    #    /  \
    #  4     5
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)

    res = inOrder(root)
    printList(res)
```

### Postorder traversal (left right root)

#### Recursive

```
class Node:
    def __init__(self, v):
        self.data = v
        self.left = None
        self.right = None

# Function to print postorder traversal
def print_postorder(node):
    if node is None:
        return

    # First recur on left subtree
    print_postorder(node.left)

    # Then recur on right subtree
    print_postorder(node.right)

    # Now deal with the node
    print(node.data, end=' ')

if __name__ == '__main__':
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.right = Node(6)

    print_postorder(root)
```

#### Iterative (Using Two Stacks)

```
# Python program to o find the postorder
# traversal using 2 Stacks
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

# Function to do post-order traversal
# using two stacks
def postOrder(root):
    result = []
    if root is None:
        return result

    # Create two stacks
    stk1 = []
    stk2 = []

    # Push root to first stack
    stk1.append(root)

    # Run while first stack is not empty
    while stk1:

        # Pop from stk1 and push it to stk2
        curr = stk1.pop()
        stk2.append(curr)

        # Push left and right children of
        # the popped node
        if curr.left:
            stk1.append(curr.left)
        if curr.right:
            stk1.append(curr.right)

    # Collect all elements from second stack
    while stk2:
        curr = stk2.pop()
        result.append(curr.data)

    return result

def printArray(arr):
    print(" ".join(map(str, arr)))

if __name__ == "__main__":

    # Representation of input binary tree:
    #           1
    #         /   \
    #        2     3
    #      /  \
    #     4    5
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)

    result = postOrder(root)
    printArray(result)
```

#### Iterative (Using One Stacks)

```
# Python implementation
class Node:
    def __init__(self, x):
        self.data = x
        self.left = None
        self.right = None

def postOrder(root):
    res = []
    st = []
    while True:
        while root:
            st.append(root)
            st.append(root)
            root = root.left
        if not st:
            return res
        root = st.pop()
        if st and st[-1] == root:
            root = root.right
        else:
            res.append(root.data)
            root = None

if __name__ == '__main__':
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)

    postOrderList = postOrder(root)
    print(' '.join(map(str, postOrderList)))
```

### Preorder, Postorder and Inorder Traversal of a Binary Tree using a single Stack

```
# Python3 program for the above approach

# Structure of the
# node of a binary tree
class Node:
	def __init__(self, x):
		self.data = x
		self.left = None
		self.right = None

# Function to print all nodes of a
# binary tree in Preorder, Postorder
# and Inorder using only one stack
def allTraversal(root):

	# Stores preorder traversal
	pre = []

	# Stores inorder traversal
	post = []

	# Stores postorder traversal
	inn = []

	# Stores the nodes and the order
	# in which they are currently visited
	s = []

	# Push root node of the tree
	# into the stack
	s.append([root, 1])

	# Traverse the stack while
	# the stack is not empty
	while (len(s) > 0):

		# Stores the top
		# element of the stack
		p = s[-1]
		#del s[-1]

		# If the status of top node
		# of the stack is 1
		if (p[1] == 1):

			# Update the status
			# of top node
			s[-1][1] += 1

			# Insert the current node
			# into preorder, pre[]
			pre.append(p[0].data)

			# If left child is not NULL
			if (p[0].left):

				# Insert the left subtree
				# with status code 1
				s.append([p[0].left, 1])

		# If the status of top node
		# of the stack is 2
		elif (p[1] == 2):

			# Update the status
			# of top node
			s[-1][1] += 1

			# Insert the current node
			# in inorder, in[]
			inn.append(p[0].data);

			# If right child is not NULL
			if (p[0].right):

				# Insert the right subtree into
				# the stack with status code 1
				s.append([p[0].right, 1])

		# If the status of top node
		# of the stack is 3
		else:

			# Push the current node
			# in post[]
			post.append(p[0].data);

			# Pop the top node
			del s[-1]

	print("Preorder Traversal: ",end=" ")
	for i in pre:
		print(i,end=" ")
	print()

	# Printing Inorder
	print("Inorder Traversal: ",end=" ")

	for i in inn:
		print(i,end=" ")
	print()

	# Printing Postorder
	print("Postorder Traversal: ",end=" ")

	for i in post:
		print(i,end=" ")
	print()


# Driver Code
if __name__ == '__main__':

	# Creating the root
	root = Node(1)
	root.left = Node(2)
	root.right = Node(3)
	root.left.left = Node(4)
	root.left.right = Node(5)
	root.right.left = Node(6)
	root.right.right = Node(7)

	# Function call
	allTraversal(root)

	# This code is contributed by mohit kumar 29.

```

## Breath First Search

### Level Order Traversal

```
class Node:
    def __init__(self, value):
        self.data = value
        self.left = None
        self.right = None

# Iterative method to perform level order traversal
def level_order(root):
    if root is None:
        return []

    # Create an empty queue for level order traversal
    q = []
    res = []

    # Enqueue Root
    q.append(root)
    curr_level = 0

    while q:
        len_q = len(q)
        res.append([])

        for _ in range(len_q):
            # Add front of queue and remove it from queue
            node = q.pop(0)
            res[curr_level].append(node.data)

            # Enqueue left child
            if node.left is not None:
                q.append(node.left)

            # Enqueue right child
            if node.right is not None:
                q.append(node.right)
        curr_level += 1
    return res

if __name__ == '__main__':
    #      5
    #     / \
    #   12   13
    #   /  \    \
    #  7    14   2
    # /  \   /  \  / \
    #17 23 27  3  8  11

    root = Node(5)
    root.left = Node(12)
    root.right = Node(13)

    root.left.left = Node(7)
    root.left.right = Node(14)

    root.right.right = Node(2)

    root.left.left.left = Node(17)
    root.left.left.right = Node(23)

    root.left.right.left = Node(27)
    root.left.right.right = Node(3)

    root.right.right.left = Node(8)
    root.right.right.right = Node(11)

    # Perform level order traversal and get the result
    res = level_order(root)

    # Print the result in the required format
    for level in res:
        print('[', end='')
        print(', '.join(map(str, level)), end='')
        print('] ', end='')
```

### Zig Zag Traversal

We create a flag to decide the direction of insertion

[Leetcode](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

```
from collections import deque

class Node:
    def __init__(self, value):
        self.data = value
        self.left = None
        self.right = None

# Iterative method to perform level order traversal
def zig_zag_level_order(root):

    res = []
    q = deque([root] if root else [])
    left_to_right = True

    while q:
        size = len(q)
        level = []

        for i in range(size):
            node = q.popleft()
            level.append(node.data)

            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)

        if not left_to_right:
            level = reversed(level)
        res.append(level)

        left_to_right = not left_to_right

    return res

if __name__ == '__main__':
    #      5
    #     / \
    #   12   13
    #   /  \    \
    #  7    14   2
    # /  \   /  \  / \
    #17 23 27  3  8  11

    root = Node(5)
    root.left = Node(12)
    root.right = Node(13)

    root.left.left = Node(7)
    root.left.right = Node(14)

    root.right.right = Node(2)

    root.left.left.left = Node(17)
    root.left.left.right = Node(23)

    root.left.right.left = Node(27)
    root.left.right.right = Node(3)

    root.right.right.left = Node(8)
    root.right.right.right = Node(11)

    # Perform level order traversal and get the result
    res = zig_zag_level_order(root)

    # Print the result in the required format
    for level in res:
        print('[', end='')
        print(', '.join(map(str, level)), end='')
        print('] ', end='')
```

### Vertical Order Traversal

LeetCode 314 (Paid)

```
from collections import deque

class Node:
    def __init__(self, value):
        self.data = value
        self.left = None
        self.right = None

# Iterative method to perform level order traversal
def vertical_order(root):

    res = []
    q = deque([root] if root else [])
    left_to_right = True

    while q:
        size = len(q)
        level = []

        for i in range(size):
            node = q.popleft()
            level.append(node.data)

            if node.left:
                q.append(node.left)
            if node.right:
                q.append(node.right)

        if not left_to_right:
            level = reversed(level)
        res.append(level)

        left_to_right = not left_to_right

    return res

if __name__ == '__main__':
    #      5
    #     / \
    #   12   13
    #   /  \    \
    #  7    14   2
    # /  \   /  \  / \
    #17 23 27  3  8  11

    root = Node(5)
    root.left = Node(12)
    root.right = Node(13)

    root.left.left = Node(7)
    root.left.right = Node(14)

    root.right.right = Node(2)

    root.left.left.left = Node(17)
    root.left.left.right = Node(23)

    root.left.right.left = Node(27)
    root.left.right.right = Node(3)

    root.right.right.left = Node(8)
    root.right.right.right = Node(11)

    # Perform level order traversal and get the result
    res = vertical_order(root)

    # Print the result in the required format
    for level in res:
        print('[', end='')
        print(', '.join(map(str, level)), end='')
        print('] ', end='')
```
