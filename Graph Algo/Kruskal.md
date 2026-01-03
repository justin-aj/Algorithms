**What it does:**

Connects all nodes with minimum total edge weight, without cycles.

---

**How it works:**

1. Sort all edges by weight
2. Pick smallest edge
3. If it doesn't form a cycle, add it
4. Repeat until all nodes connected

---

**Kruskal's with clear variable names:**

```python
def kruskal(nodes, edges):
    # edges = [(weight, node1, node2), ...]
    edges.sort()
    
    # Each node is its own parent initially
    parent = {node: node for node in nodes}
    rank = {node: 0 for node in nodes}
    
    def find_root(node):
        if parent[node] != node:
            parent[node] = find_root(parent[node])  # Path compression
        return parent[node]
    
    def connect(node1, node2):
        root1 = find_root(node1)
        root2 = find_root(node2)
        
        # Same root = already connected = would form cycle
        if root1 == root2:
            return False
        
        # Union by rank (attach smaller tree to larger)
        if rank[root1] < rank[root2]:
            parent[root1] = root2
        elif rank[root1] > rank[root2]:
            parent[root2] = root1
        else:
            parent[root2] = root1
            rank[root1] += 1
        
        return True
    
    mst = []
    total_weight = 0
    
    for weight, node1, node2 in edges:
        if connect(node1, node2):
            mst.append((node1, node2, weight))
            total_weight += weight
    
    return mst, total_weight


# Graph
nodes = ['A', 'B', 'C', 'D']
edges = [
    (4, 'A', 'B'),
    (2, 'A', 'C'),
    (3, 'A', 'D'),
    (1, 'C', 'D'),
    (5, 'B', 'D')
]

mst, total = kruskal(nodes, edges)
print(f"MST edges: {mst}")
print(f"Total weight: {total}")
```

---

**Step-by-step trace:**

```
Graph:
    A ---4--- B
    |  \      |
    2   3     5
    |    \    |
    C ---1--- D

Edges sorted: [(1,C,D), (2,A,C), (3,A,D), (4,A,B), (5,B,D)]

Initial parent: {A:A, B:B, C:C, D:D}
```

---

**Step 1: Edge (C, D, weight=1)**

```
find_root(C) = C
find_root(D) = D
C != D → connect them ✓

parent: {A:A, B:B, C:C, D:C}
mst: [(C, D, 1)]
```

---

**Step 2: Edge (A, C, weight=2)**

```
find_root(A) = A
find_root(C) = C
A != C → connect them ✓

parent: {A:A, B:B, C:A, D:C}
mst: [(C, D, 1), (A, C, 2)]
```

---

**Step 3: Edge (A, D, weight=3)**

```
find_root(A) = A
find_root(D) = find_root(C) = A
A == A → CYCLE! Skip ❌

parent: unchanged
mst: unchanged
```

---

**Step 4: Edge (A, B, weight=4)**

```
find_root(A) = A
find_root(B) = B
A != B → connect them ✓

parent: {A:A, B:A, C:A, D:C}
mst: [(C, D, 1), (A, C, 2), (A, B, 4)]
```

---

**Step 5: Edge (B, D, weight=5)**

```
find_root(B) = A
find_root(D) = A
A == A → CYCLE! Skip ❌
```

---

**Final result:**

```
MST:
    A ---4--- B
    |         
    2         
    |         
    C ---1--- D

MST edges: [(C, D, 1), (A, C, 2), (A, B, 4)]
Total weight: 1 + 2 + 4 = 7
```

---

**Output:**

```
MST edges: [('C', 'D', 1), ('A', 'C', 2), ('A', 'B', 4)]
Total weight: 7
```

---

**Time complexity:** O(E log E)

- Sorting edges = O(E log E)
- Union-Find operations = O(E × α(V)) ≈ O(E)

---

**Dijkstra vs Kruskal:**

||Dijkstra|Kruskal|
|---|---|---|
|Finds|Shortest paths|Minimum spanning tree|
|From|Single source|Entire graph|
|Uses|Min heap|Sorting + Union Find|
|Output|Distances|Tree edges|

---
