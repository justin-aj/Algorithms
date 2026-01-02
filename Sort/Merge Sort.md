![[Pasted image 20260102142729.png]]

**Merge Sort**

Divide array in half, sort each half, merge them back.

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    
    return result
```

**How it works:**

```
[5, 3, 8, 1]
    /    \
 [5,3]  [8,1]
  / \    / \
[5] [3] [8] [1]
  \ /    \ /
 [3,5]  [1,8]
    \    /
 [1,3,5,8]
```

**Time:** O(n log n) — always **Space:** O(n)

**Why it's important:**

- Guaranteed O(n log n), no worst case
- Stable sort
- Great for linked lists
- Divide and conquer pattern (common in interviews)