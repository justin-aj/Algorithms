
The heap gets the largest element at the top and then the next loop basically swaps it and again heapify it.

**Heap Sort without heapq:**

```python
def heap_sort(arr):
    n = len(arr)
    
    # Build max heap - gets the largest element at the top
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    
    # Extract max one by one - swap largest and first element and heapify again
    for i in range(n - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(arr, i, 0)
    
    return arr

def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    
    if left < n and arr[left] > arr[largest]:
        largest = left
    
    if right < n and arr[right] > arr[largest]:
        largest = right
    
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)
```

This is the simplest version without using any library.

**Time:** O(n log n) **Space:** O(1)

**1. What is a Heap?**

A heap is a complete binary tree stored in an array.

**Max heap:** Parent is always larger than children.

```
Array: [8, 5, 6, 3, 1, 2]

As tree:
        8
       / \
      5   6
     /\   /
    3  1 2

Parent of i: (i - 1) // 2
Left child of i: 2 * i + 1
Right child of i: 2 * i + 2
```

---

**2. What is Heapify?**

Heapify fixes a single node to maintain heap property. It pushes a node down if it's smaller than its children.

```python
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    
    if left < n and arr[left] > arr[largest]:
        largest = left
    
    if right < n and arr[right] > arr[largest]:
        largest = right
    
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)
```

**Example:**

```
Before heapify(arr, 6, 0):

        1          ← i=0, too small
       / \
      5   6
     /\   /
    3  2 4

Compare: 1 vs 5 vs 6 → 6 is largest → swap

        6
       / \
      5   1    ← now fix this
     /\   /
    3  2 4

Compare: 1 vs 4 → 4 is largest → swap

        6
       / \
      5   4
     /\   /
    3  2 1

Done.
```

---

**3. Building the Heap**

Start from last non-leaf node, heapify each.

```python
for i in range(n // 2 - 1, -1, -1):
    heapify(arr, n, i)
```

**Why `n // 2 - 1`?**

Leaf nodes don't need heapifying. Last non-leaf is at `n // 2 - 1`.

**Example with [5, 3, 8, 1]:**

```
n = 4
n // 2 - 1 = 1

Start:
        5
       / \
      3   8
     /
    1

i=1: heapify node 3
     3 > 1? Yes, no swap needed

i=0: heapify node 5
     5 vs 3 vs 8 → 8 largest → swap

        8
       / \
      3   5
     /
    1

Max heap built.
```

---

**4. Sorting from the Heap**

Now we extract max (root) one by one.

```python
for i in range(n - 1, 0, -1):
    arr[0], arr[i] = arr[i], arr[0]   # swap max to end
    heapify(arr, i, 0)                 # fix the heap
```

**Step by step:**

```
[8, 3, 5, 1]   heap size = 4

Swap 8 and 1:
[1, 3, 5, 8]   heap size = 3 (8 is sorted)

Heapify:
[5, 3, 1, 8]

Swap 5 and 1:
[1, 3, 5, 8]   heap size = 2 (5,8 sorted)

Heapify:
[3, 1, 5, 8]

Swap 3 and 1:
[1, 3, 5, 8]   heap size = 1 (all sorted)

Done: [1, 3, 5, 8]
```

---

**Full Code:**

```python
def heap_sort(arr):
    n = len(arr)
    
    # Build max heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    
    # Extract max one by one
    for i in range(n - 1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(arr, i, 0)
    
    return arr

def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    
    if left < n and arr[left] > arr[largest]:
        largest = left
    
    if right < n and arr[right] > arr[largest]:
        largest = right
    
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)
```

**Summary:**

1. Heap = tree in array, parent > children
2. Heapify = push node down to fix heap
3. Build heap from bottom up
4. Swap root to end, shrink heap, repeat

Makes sense now?