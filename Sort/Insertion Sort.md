![[Pasted image 20260102143052.png]]

**Insertion Sort**

Pick an element, insert it in its correct position in the sorted portion.

```python
def insertion_sort(arr):
    n = len(arr)
    
    for i in range(1, n):
        key = arr[i]
        j = i - 1
        
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        
        arr[j + 1] = key
    
    return arr
```

**How it works:**

```
[5, 3, 8, 1]
    ^         key=3, shift 5 right → [5, 5, 8, 1] → insert 3 → [3, 5, 8, 1]

[3, 5, 8, 1]
       ^      key=8, nothing to shift → [3, 5, 8, 1]

[3, 5, 8, 1]
          ^   key=1, shift 8,5,3 right → insert 1 → [1, 3, 5, 8]

Done.
```

**Time:** O(n²) **Space:** O(1)

**Why it's useful:**

- Great for nearly sorted data — becomes O(n)
- Good for small arrays
- Used in hybrid sorts (like Timsort uses it for small chunks)