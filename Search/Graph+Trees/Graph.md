Both are used. Depends on the situation.

**Dictionary (adjacency list)** — simple, quick, common in interviews and scripts

```python
graph = {
    0: [1, 2],
    1: [0, 3],
    2: [0],
    3: [1]
}
```

**Class-based** — more structure, used in production/larger codebases

```python
class Node:
    def __init__(self, val):
        self.val = val
        self.neighbors = []

# create nodes
a = Node('A')
b = Node('B')
c = Node('C')

# connect them
a.neighbors = [b, c]
b.neighbors = [a]
c.neighbors = [a]
```

**When to use what:**

|Adjacency list (dict)|Class-based|
|---|---|
|Interviews|Production code|
|Quick prototyping|When nodes have extra data|
|Simple graphs|Complex systems|

For interviews, dictionary is almost always fine. Interviewers expect it.