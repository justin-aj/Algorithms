Tree:             1
          / | \
         2  3  4
        /\
        5  6

BFS order: 1 → 2 → 3 → 4 → 5 → 6
DFS order: 1 → 2 → 5 → 6 → 3 → 4

**Breadth-First Search (BFS)**

Explore level by level. Uses a queue.

```python
from collections import deque

def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    
    while queue:
        node = queue.popleft()
        print(node)  # process node
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

**Time:** O(V + E) **Space:** O(V)

**BFS on a grid:**

```python
def bfs_grid(grid, start_row, start_col):
    rows, cols = len(grid), len(grid[0])
    visited = set([(start_row, start_col)])
    queue = deque([(start_row, start_col)])
    
    directions = [(0,1), (0,-1), (1,0), (-1,0)]
    
    while queue:
        r, c = queue.popleft()
        
        for dr, dc in directions:
            nr, nc = r + dr, c + dc
            if 0 <= nr < rows and 0 <= nc < cols and (nr,nc) not in visited:
                visited.add((nr, nc))
                queue.append((nr, nc))
```

**Use BFS when:**

- Shortest path in unweighted graph
- Level order traversal
- Nearest something (rotten oranges, nearest gate)