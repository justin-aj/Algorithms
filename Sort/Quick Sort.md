![[Pasted image 20260102143826.png]]

**Quick Sort**

Pick a pivot, partition array so smaller elements go left and larger go right, then recurse.

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[-1]
    left = []
    right = []
    
    for x in arr[:-1]:
        if x <= pivot:
            left.append(x)
        else:
            right.append(x)
    
    return quick_sort(left) + [pivot] + quick_sort(right)
```

**How it works:**

```
[5, 3, 8, 1]   pivot = 1

left = []      (nothing <= 1)
right = [5,3,8]

→ [] + [1] + quick_sort([5,3,8])

[5, 3, 8]   pivot = 8

left = [5, 3]
right = []

→ quick_sort([5,3]) + [8] + []

[5, 3]   pivot = 3

left = []
right = [5]

→ [] + [3] + [5] = [3, 5]

Final: [1, 3, 5, 8]
```

**Time:** O(n log n) average, O(n²) worst **Space:** O(n) for this version

**In-place version** (more efficient, commonly asked):

```python
def quick_sort(arr, low, high):
    if low < high:
        pivot_idx = partition(arr, low, high)
        quick_sort(arr, low, pivot_idx - 1)
        quick_sort(arr, pivot_idx + 1, high)

def partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    
    for j in range(low, high):
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1

# usage
quick_sort(arr, 0, len(arr) - 1)
```

**Time:** O(n log n) average, O(n²) worst **Space:** O(log n) — just recursion stack