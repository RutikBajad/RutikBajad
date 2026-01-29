
---

# 🗺️ Graph Traversal Algorithms: BFS & DFS

This repository contains Python implementations of the two fundamental graph traversal algorithms: **Breadth-First Search (BFS)** and **Depth-First Search (DFS)**. These examples use a "City Map" represented as an adjacency list to demonstrate how each algorithm navigates through intersections and roads.

## 🏗️ The City Map (Graph Structure)

Both algorithms operate on the following graph, where keys are intersections and values are lists of connected neighbors:

```python
City_Map = {
    'A' : ['B' ,'C'],
    'B' : ['A', 'D', 'E'],
    'C' : ['A', 'F', 'G'],
    'D' : ['B'],
    'E' : ['B'],
    'F' : ['C'],
    'G' : ['C']
}

```

---

## 🌊 1. Breadth-First Search (BFS)

BFS explores the map **level-by-level**. It visits all immediate neighbors of the starting point before moving to the next "layer" of cities.

* **Mechanism:** Uses a **Queue** (First-In, First-Out).
* **Best For:** Finding the shortest path in unweighted graphs.
* **Traversal Order:** `A → B → C → D → E → F → G`

### BFS Implementation

```python
from collections import deque

def city_map_traversal_bfs(city_map, start):
    visited = set()
    queue = deque([start])
    
    while queue:
        intersection = queue.popleft()
        if intersection not in visited:
            print(intersection, end=" ")
            visited.add(intersection)
            for neighbor in city_map[intersection]:
                if neighbor not in visited:
                    queue.append(neighbor)

```

---

## 🌲 2. Depth-First Search (DFS)

DFS explores the map **branch-by-branch**. It dives as deep as possible down one path before backtracking to explore alternative routes.

* **Mechanism:** Uses **Recursion** (or a Stack).
* **Best For:** Pathfinding, topological sorting, and solving puzzles.
* **Traversal Order:** `A → B → D → E → C → F → G`

### DFS Implementation

```python
def city_map_traversal_dfs(city_map, start, visited=None):
    if visited is None:
        visited = set()

    print(start, end=" ")
    visited.add(start)

    for neighbor in city_map[start]:
        if neighbor not in visited:
            city_map_traversal_dfs(city_map, neighbor, visited)

```

---

## ⚖️ Comparison Summary

| Feature | BFS (Breadth-First) | DFS (Depth-First) |
| --- | --- | --- |
| **Data Structure** | Queue (FIFO) | Stack (LIFO) or Recursion |
| **Strategy** | Wide (Horizontal) | Deep (Vertical) |
| **Memory** | Higher for wide graphs | Higher for deep graphs |
| **Use Case** | Shortest path | Completeness/Exhaustive search |

---
