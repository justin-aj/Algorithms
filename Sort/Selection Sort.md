![[Pasted image 20260102142807.png]]

**Selection Sort**

Find the minimum element, swap it to the front. Repeat for the rest.

```python
def selection_sort(arr):
    n = len(arr)
    
    for i in range(n):
        min_idx = i
        
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    
    return arr
```

**How it works:**

```
[5, 3, 8, 1]
 ^        ^  → min is 1 → swap → [1, 3, 8, 5]

[1, 3, 8, 5]
    ^        → min is 3 → no swap → [1, 3, 8, 5]

[1, 3, 8, 5]
       ^  ^  → min is 5 → swap → [1, 3, 5, 8]

Done.
```

**Time:** O(n²) **Space:** O(1)

**vs Bubble Sort:**

- Selection sort does fewer swaps (one per pass)
- Bubble sort can stop early if sorted
- Both are O(n²), rarely used in practice