## Overview
- Tarjan's Algorithm is an algorithm used for finding strongly connected components (SCCs) in a directed graph
	- An SCC of a directed graph is a maximal subgraph where every pair of vertices is mutually reachable. This means that for any two nodes $A$ and $B$ in the subgraph, there is a path from $A$ to $B$ and a path from $B$ to $A$.
	- The **condensation graph** of a directed graph is the graph where all SCCs are represented by their own vertices.