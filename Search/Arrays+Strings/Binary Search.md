**Binary Search**

Works on sorted arrays. Cut the search space in half each time.

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
	    mid = (left + right) // 2
	    if arr[mid] == target:
		    return mid
		elif arr[mid] < target:
			left = mid + 1
		else:
			right = mid - 1
	
	return -1
```

**Time:** O(log n) **Space:** O(1)

**Common variations:**

- Find first occurrence of target
- Find last occurrence of target
- Search in rotated sorted array
- Find insertion position
- Binary search on answer (minimize/maximize something)