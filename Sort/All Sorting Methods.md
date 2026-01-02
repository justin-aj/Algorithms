**Sorting Algorithms**

**The main ones:**

| Algorithm      | Time (avg) | Time (worst) | Space    | Stable |
| -------------- | ---------- | ------------ | -------- | ------ |
| Bubble Sort    | O(n²)      | O(n²)        | O(1)     | Yes    |
| Selection Sort | O(n²)      | O(n²)        | O(1)     | No     |
| Insertion Sort | O(n²)      | O(n²)        | O(1)     | Yes    |
| Merge Sort     | O(n log n) | O(n log n)   | O(n)     | Yes    |
| Quick Sort     | O(n log n) | O(n²)        | O(log n) | No     |
| Heap Sort      | O(n log n) | O(n log n)   | O(1)     | No     |

**For interviews, focus on:**

1. **Merge Sort** — divide and conquer, stable, guaranteed O(n log n)
2. **Quick Sort** — fastest in practice, used by most languages
3. **Insertion Sort** — good for nearly sorted data

**Quick summary:**

- **Bubble** — swap adjacent elements, mostly for learning
- **Selection** — find min, put it first, repeat
- **Insertion** — build sorted array one element at a time
- **Merge** — split in half, sort each, merge back
- **Quick** — pick pivot, partition around it, recurse
- **Heap** — build heap, extract min/max repeatedly