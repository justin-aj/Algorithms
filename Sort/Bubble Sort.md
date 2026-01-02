![[Pasted image 20260102132635.png]]

**Bubble Sort**

Compare adjacent elements, swap if out of order. Repeat until sorted.

```python
def bubble_sort(arr):
    n = len(arr)
    
    for i in range(n):
        for j in range(n - 1 - i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    
    return arr
```

**Optimized version** (stops early if already sorted):

```python
def bubble_sort(arr):
    n = len(arr)
    
    for i in range(n):
        swapped = False
        
        for j in range(n - 1 - i):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        
        if not swapped:
            break
    
    return arr
```

**How it works:**

```
[5, 3, 8, 1]
 ^  ^        → swap → [3, 5, 8, 1]
    ^  ^     → no swap
       ^  ^  → swap → [3, 5, 1, 8]

... repeat until sorted
```

**Time:** O(n²) **Space:** O(1)

Largest element "bubbles up" to the end each pass.