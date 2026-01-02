Tree:             1
          / | \
         2  3  4
        /\
        5  6

BFS order: 1 → 2 → 3 → 4 → 5 → 6
DFS order: 1 → 2 → 5 → 6 → 3 → 4


**Depth-First Search (DFS)**

**Recursive:**

```python
def dfs(graph, node, visited):
    visited.add(node)
    print(node)  # process node
    
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

# usage
visited = set()
dfs(graph, start, visited)
```

**Iterative (using stack):**

```python
def dfs(graph, start):
    visited = set()
    stack = [start]
    
    while stack:
        node = stack.pop()
        
        if node not in visited:
            visited.add(node)
            print(node)  # process node
            
            for neighbor in graph[node]:
                stack.append(neighbor)
```

**DFS on a grid:**

```python
def dfs_grid(grid, r, c, visited):
    rows, cols = len(grid), len(grid[0])
    
    if r < 0 or r >= rows or c < 0 or c >= cols:
        return
    if (r, c) in visited:
        return
    
    visited.add((r, c))
    
    dfs_grid(grid, r + 1, c, visited)
    dfs_grid(grid, r - 1, c, visited)
    dfs_grid(grid, r, c + 1, visited)
    dfs_grid(grid, r, c - 1, visited)
```

**Time:** O(V + E) **Space:** O(V)