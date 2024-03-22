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


----------------------------------------------------------------


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

#### Singly Linked Lists
In a singly linked list, each node contains a single link field pointing to the next node. This structure allows for efficient traversal in one direction, from the head of the list to the end.

Traversal: Efficient in one direction due to the single link in each node.

Insertion/Deletion at the beginning: O(1) time complexity, as it involves changing the head pointer and the next pointer of the newly inserted node.

Insertion/Deletion at the end or middle: O(n) time complexity, as it requires traversing the list to find the position for insertion or deletion.

Sample List: 1 -> 2 -> 3 -> 4 -> None

Problem Statement 1: Reverse a singly linked list.

```bash
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def reverse_linked_list(head):
    previous = None
    current = head
    while current:
        next_node = current.next
        current.next = previous
        previous = current
        current = next_node
    return previous
```

Problem Statement 2: Find the middle of a singly linked list.

```bash
def find_middle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
    return slow.data
```

#### Doubly Linked Lists
A doubly linked list extends the singly linked list by including a second link field in each node. This second link points to the previous node, allowing for efficient traversal in both directions.

Traversal: Efficient in both directions due to the presence of next and prev links in each node.

Insertion/Deletion: More flexible than singly linked lists, as nodes can easily be removed or added from both ends and the middle with references to both previous and next nodes, which allows for O(1) time complexity if the node reference is known.

Sample List: None <- 1 <-> 2 <-> 3 -> None

Problem Statement 1: Implement a function to insert a new node at the beginning of a doubly linked list.

```bash
class DoublyNode:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

def insert_at_beginning(head, data):
    new_node = DoublyNode(data)
    new_node.next = head
    if head:
        head.prev = new_node
    head = new_node
    return head
```

Problem Statement 2: Remove a node from the end of a doubly linked list.

```bash
def remove_from_end(head):
    if not head or not head.next:
        return None
    current = head
    while current.next:
        current = current.next
    current.prev.next = None
    return head
```

#### Circular Linked Lists
A circular linked list is a variation where the last node points back to the first node, creating a circular loop. This can be implemented as either singly or doubly circular linked lists.

Traversal: Like circular linked lists but with the ability to move both forwards and backwards.

Insertion/Deletion: Offers the greatest flexibility for insertion and deletion operations at any point in the list with O(1) time complexity, provided you have a reference to the node of interest. The circular nature requires maintaining the integrity of the list's loop structure.

Traversal: Can traverse the entire list starting from any node, as it forms a loop.

Insertion/Deletion: Similar to singly linked lists but with the additional consideration that the last node points back to the first node. This requires ensuring the circular structure is maintained after operations.


Problem Statement 1: Check if a linked list is circular.

```bash
def is_circular_linked_list(head):
    if not head:
        return False
    current = head.next
    while current is not None and current != head:
        current = current.next
    return current == head
```

Problem Statement 2: Count the number of nodes in a circular linked list.

```bash
def count_nodes(head):
    if not head:
        return 0
    current = head
    count = 1
    while current.next != head:
        count += 1
        current = current.next
    return count
```

#### Doubly Circular Linked Lists
Similar to the singly circular linked list, but each node has two links, connecting it to both the next and the previous nodes, and the last node links back to the first node, creating a circular loop.


Sample List: None <- 1 <-> 2 <-> 3 <-> 1 -> None (circular)

Problem Statement 1: Implement a function to delete a node from a doubly circular linked list

```bash
def delete_node(head, key):
    if not head:
        return None
    current = head
    previous = None
    while True:
        if current.data == key:
            if current == head and current.next == head:
                head = None
                return head
            elif current == head:
                prev = head.prev
                head = head.next
                head.prev = prev
                prev.next = head
            else:
                previous.next = current.next
                current.next.prev = previous
            return head
        previous = current
        current = current.next
        if current == head:
            break
    return head
```

Problem Statement 2: Insert a new node at the end of a doubly circular linked list.

```bash
def insert_at_end(head, data):
    new_node = DoublyNode(data)
    if not head:
        new_node.next = new_node.prev = new_node
        return new_node
    tail = head.prev
    tail.next = new_node
    new_node.prev = tail
    new_node.next = head
    head.prev = new_node
    return head
```



--------------------------------------------------------------------------------



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



-------------------------------------------------------------------------------------------------


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


--------------------------------------------------------------------------------------------



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
