Go through each element one by one until you find the target.

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

**Time:** O(n) **Space:** O(1)

That's it. Works on unsorted data, no special conditions needed.

It's rarely asked as a standalone question — but it shows up inside other problems when you need to scan through something.