**Complete code with graph setup:**

```python
import heapq

def dijkstra(graph, start):
    # Initialize all distances as infinity
    dist = {node: float('inf') for node in graph}
    dist[start] = 0
    
    # Min heap: (distance, node)
    heap = [(0, start)]
    
    while heap:
        d, node = heapq.heappop(heap)
        print(d, node, dist[node], dist)
        
        # Skip if we already found a better path
        if d > dist[node]:
            continue
        
        # Check all neighbors
        for neighbor, weight in graph[node]:
	        print("mid", d, weight, neighbor)
            new_dist = d + weight
            # A -> B = A -> B -> D -> B is also counted
            
            if new_dist < dist[neighbor]:
                dist[neighbor] = new_dist
                heapq.heappush(heap, (new_dist, neighbor))
    
    return dist


# Graph definition
# Each node maps to list of (neighbor, weight)
graph = {
    'A': [('B', 2), ('C', 4)],
    'B': [('A', 2), ('D', 1)],
    'C': [('A', 4), ('D', 3)],
    'D': [('B', 1), ('C', 3)]
}

# Run it
result = dijkstra(graph, 'A')
print(result)
```

---

**Output:**

```
{'A': 0, 'B': 2, 'C': 4, 'D': 3}
```

0 A 0 {'A': 0, 'B': inf, 'C': inf, 'D': inf}
mid 0 2 B
mid 0 4 C
2 B 2 {'A': 0, 'B': 2, 'C': 4, 'D': inf}
mid 2 2 A
mid 2 1 D
3 D 3 {'A': 0, 'B': 2, 'C': 4, 'D': 3}
**mid 3 1 B**
mid 3 3 C
4 C 4 {'A': 0, 'B': 2, 'C': 4, 'D': 3}
mid 4 4 A
mid 4 3 D
{'A': 0, 'B': 2, 'C': 4, 'D': 3}
---

**Graph structure explained:**

```
graph = {
    'A': [('B', 2), ('C', 4)],  # A connects to B (weight 2), C (weight 4)
    'B': [('A', 2), ('D', 1)],  # B connects to A (weight 2), D (weight 1)
    'C': [('A', 4), ('D', 3)],  # C connects to A (weight 4), D (weight 3)
    'D': [('B', 1), ('C', 3)]   # D connects to B (weight 1), C (weight 3)
}
```

---

**Visual:**

```
    A ---2--- B
    |         |
    4         1
    |         |
    C ---3--- D
```

---
