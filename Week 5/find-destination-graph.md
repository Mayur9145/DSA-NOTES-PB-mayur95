# Find the destination graph problem


[leetcode](https://leetcode.com/problems/find-if-path-exists-in-graph/submissions/1373713190/)

### Time and Space Complexity

- **Time Complexity:** O(V + E)
  - `V` represents the number of vertices (nodes) in the graph.
  - `E` represents the number of edges in the graph.
  - The time complexity is derived from the fact that each node and edge is processed exactly once during the breadth-first traversal.

- **Space Complexity:** O(V + E)
  - The space complexity accounts for:
    - The adjacency list, which stores all vertices and edges, requiring O(V + E) space.
    - The `visited` set, which stores up to O(V) nodes.
    - The `queue` used for traversal, which in the worst case can store up to O(V) nodes.



###  Python Code

```python
from collections import deque, defaultdict
from typing import List

class Solution:
    def bft(self, visited, graph, node, destination):
        queue = deque()

        visited.add(node)
        queue.append(node)  

        while queue:
            current_node = queue.popleft()  
            if current_node == destination: 
                return True

            for adjacent_node in graph[current_node]:
                if adjacent_node not in visited:
                    visited.add(adjacent_node)
                    queue.append(adjacent_node)  

        return False  

    def validPath(self, n: int, edges: List[List[int]], source: int, destination: int) -> bool:
        graph = defaultdict(list)
        for a, b in edges:
            graph[a].append(b)
            graph[b].append(a)

        visited = set()

        return self.bft(visited, graph, source, destination)
```


# Breadth-First Traversal for Valid Path in Graph

## Problem Statement

Given an undirected graph represented by `n` nodes and a list of edges, determine whether there is a valid path between two nodes, `source` and `destination`.

## Approach

### 1. Problem Breakdown

- **Graph Representation:** 
  - The problem provides a list of edges to represent the undirected graph. We need to convert this list into an adjacency list for easier traversal.

- **Traversal Method:**
  - Since the problem is to find if there is a valid path between the `source` and `destination`, we can use Breadth-First Traversal (BFT). BFT is ideal for this problem as it explores all nodes at the present "depth" before moving on to nodes at the next depth level, ensuring that if there's a path, it'll be found.

### 2. Implementation Steps

#### Step 1: Graph Construction

- Use a `defaultdict` from the `collections` module to construct the adjacency list.
- For every edge `(a, b)`, add `b` to the list of adjacent nodes for `a`, and `a` to the list of adjacent nodes for `b`.

#### Step 2: Breadth-First Traversal (BFT)

- **Initialization:**
  - Use a `deque` to act as the queue for managing the traversal order.
  - Use a `set` to keep track of visited nodes to avoid processing the same node multiple times.

- **Traversal Process:**
  - Start by marking the `source` node as visited and adding it to the queue.
  - While the queue is not empty:
    - Dequeue a node and check if it matches the `destination`. If it does, return `True` (path exists).
    - For each adjacent node, if it hasn't been visited, mark it as visited and enqueue it for further exploration.

- **Termination:**
  - If the queue is exhausted without finding the `destination`, return `False`.

