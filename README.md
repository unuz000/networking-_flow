# networking-_flow
# Ford–Fulkerson Algorithm – Max Flow & Minimum Cut

## 📘 Overview

The **Ford–Fulkerson algorithm** is a classic algorithm used to compute the **maximum flow** in a **flow network** — a directed graph where each edge has a capacity and each edge receives a flow.

After computing the maximum flow, we can also determine the **minimum cut**, which represents the smallest set of edges that, if removed, would disconnect the source from the sink.  
The total capacity of this minimum cut is equal to the maximum possible flow in the network (by the **Max-Flow Min-Cut Theorem**).

---

## 🧠 Concept

A **flow network** consists of:
- **Source (S):** The node from which flow originates.
- **Sink (T):** The node where flow terminates.
- **Edges:** Each edge `(u, v)` has a capacity indicating the maximum possible flow.

The algorithm repeatedly searches for a path from **source → sink** where more flow can be pushed (called an **augmenting path**) and adds as much flow as possible along that path.

This continues until **no more augmenting paths** exist.

---

## ⚙️ Algorithm Steps

1. Initialize all edge flows to 0.  
2. While there exists a path from source to sink with available capacity:
   - Find the path (using BFS or DFS).
   - Determine the **minimum residual capacity** (bottleneck capacity) along that path.
   - Update the flows along the path.
3. Once no more augmenting paths exist:
   - The **maximum flow** value is the total flow out of the source.
   - Run one more BFS from the source in the residual graph to identify the **minimum cut** edges.

---

## 🧩 Example Code

```python
test_graph = [
    [0, 16, 13, 0, 0, 0],
    [0, 0, 10, 12, 0, 0],
    [0, 4, 0, 0, 14, 0],
    [0, 0, 9, 0, 0, 20],
    [0, 0, 0, 7, 0, 4],
    [0, 0, 0, 0, 0, 0],
]

print(mincut(test_graph, source=0, sink=5))
# Output → [(1, 3), (4, 3), (4, 5)]
