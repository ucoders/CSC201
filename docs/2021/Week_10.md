---
layout: page
title: CSC201 DSA
---

# Learning outcomes
1.   Explain concepts related to graphs
2.   Explain and compare common data structures for graphs
3.   Apply DFS and BFS in problem solving



# Readings

*   Chapter 14.1-14.3 of the textbook



# Workshop: Graphs (I)

## Discussion

*   **[R-14.16]** Let `G` be an undirected graph whose vertices are the integers 1 through 8, and let the adjacent vertices of each vertex be given by the table below:

| vertex | adjacent vertices |
| ------ | ----------------- |
| 1      | (2, 3, 4)         |
| 2      | (1, 3, 4)         |
| 3      | (1, 2, 4)         |
| 4      | (1, 2, 3, 6)      |
| 5      | (6, 7, 8)         |
| 6      | (4, 5, 7)         |
| 7      | (5, 6, 8)         |
| 8      | (5, 7)            |

Assume that, in a traversal of `G`, the adjacent vertices of a given vertex are returned in the same order as they are listed in the table above.
a. Draw `G`.
b. Give the sequence of vertices of `G` visited using a DFS traversal starting at vertex 1.
c. Give the sequence of vertices visited using a BFS traversal starting at vertex 1.

 

* **[R-14.3*]** Draw an adjacency matrix representation of the undirected graph shown in Figure 14.16.



*   **[R-14.4*]** Draw an adjacency list representation of the undirected graph shown in Figure 14.16.



*   **[R-14.11]** Would you use the adjacency matrix structure or the adjacency list structure in each of the following cases? Justify your choice.

a. The graph has 10,000 vertices and 20,000 edges, and it is important to use as little space as possible.

b. The graph has 10,000 vertices and 20,000,000 edges, and it is important to use as little space as possible.

c. You need to answer the query getEdge(u, v) as fast as possible, no matter how much space you use.



## Implementation

* **Task 2 assignment**.

