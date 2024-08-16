## Overview
- Used for obtaining a path between two nodes on a graph. Typically runs faster than BFS, but path may not be optimal
- Time: $O(V+E)$
- Space: $O(V+E)$
## Applications
- Detecting a cycle in a graph:
	- If one of the edges of the current vertex points to an already visited vertex, then there is a cycle
	- Note that this doesn't include the previously traversed node of the vertex, as two-vertex connected components are acyclic
	- Note that if you want to print out this cycle, your DFS must return a vertex within the cycle

- Counting connected components in a graph:
	- Run a DFS over all vertices of the graph
	- If the start of the DFS isn't already visited, then it is a new component
	
```cpp
// C++ program to print DFS traversal from
// a given vertex in a  given graph
#include <bits/stdc++.h>
using namespace std;

// Graph class represents a directed graph
// using adjacency list representation
class Graph {
public:
    map<int, bool> visited;
    map<int, list<int> > adj;

    // Function to add an edge to graph
    void addEdge(int v, int w);

    // DFS traversal of the vertices
    // reachable from v
    void DFS(int v);
};

void Graph::addEdge(int v, int w)
{
    // Add w to v’s list.
    adj[v].push_back(w);
}

void Graph::DFS(int v)
{
    // Mark the current node as visited and
    // print it
    visited[v] = true;
    cout << v << " ";

    // Recur for all the vertices adjacent
    // to this vertex
    list<int>::iterator i;
    for (i = adj[v].begin(); i != adj[v].end(); ++i)
        if (!visited[*i])
            DFS(*i);
}

```

## Practice Problems:
- CSES: Building Roads
- CSES: Round Trip