# Data Structures and Algorithms (DSA) Overview

Data Structures and Algorithms (DSA) are fundamental concepts in computer science that enable efficient data management and operations. Here's a brief overview of main DSA topics with Python examples:

### 1. Data Structures
Data structures are ways of organizing and storing data so that they can be accessed and worked with efficiently.

#### Arrays
Arrays are collections of elements identified by index or key.

```bash
# Creating an array in Python (using a list)
arr = [1, 2, 3, 4, 5]
print(arr[2])  # Accessing the third element
```

#### Linked Lists
Linked lists consist of nodes where each node contains data and a reference to the next node in the sequence.

```bash
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

# Creating a simple linked list
head = Node(1)
head.next = Node(2)
```

#### Stacks
Stacks are linear data structures which follow a particular order in which the operations are performed (LIFO - Last In First Out).

```bash
stack = []
# Push
stack.append(1)
stack.append(2)
# Pop
print(stack.pop())
```

#### Queues
Queues are linear structures which follow a particular order in which the operations are performed (FIFO - First In First Out).

```bash
from collections import deque
queue = deque()

# Enqueue
queue.append(1)
queue.append(2)

# Dequeue
print(queue.popleft())
```

#### Trees
Trees represent hierarchical structures with a root value and subtrees of children with a parent node.

```bash
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

# Creating a simple binary tree
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
```

#### Hash Tables
Hash tables store key-value pairs. They are efficient for lookup operations.

```bash
# Creating a hash table in Python (using a dictionary)
hash_table = {'key1': 'value1', 'key2': 'value2'}
print(hash_table['key1'])  # Accessing a value
```

### 2. Algorithms
Algorithms are sequences of steps or instructions designed to perform specific tasks.

#### Sorting
Bubble Sort, Quick Sort, Merge Sort: Algorithms for arranging elements in a list in a certain order.

```bash
# Quick sort example
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

#### Searching
Binary Search: Efficient algorithm for finding an item from a sorted list of items.

```bash
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1
```

#### Graph Algorithms
Dijkstra’s Algorithm, Breadth-First Search (BFS), Depth-First Search (DFS): Algorithms for traversing or searching tree or graph data structures.

```bash
# BFS example
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    while queue:
        vertex = queue.popleft()
        if vertex not in visited:
            visited.add(vertex)
            queue.extend(graph[vertex] - visited)
    return visited
```
