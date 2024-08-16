## Overview
- Used for obtaining the shortest path between any two nodes on a graph
- Makes use of a queue (FIFO) which stores possible paths to take
- No recursion needed, a while-loop will suffice
- Time: $O(V + E)$
- Space: $O(V)$
- Note that if you want to retrace the path that you've made, it's often useful to make a parent matrix, which stores the direction taken to reach each node. After reaching the end node, the path can be retraced using this matrix

## Applications
- Checking if a graph is bipartite
	- Color head node 1, and each adjacent node with 2
	- If at any point we find a neighboring node with the same color as the head, then the graph cannot be bipartite
- One useful variation of a BFS is a multi-source BFS, which is useful when there are multiple starting points, as the name suggests. Implementation is fairly simple, and only requires adding your additional sources to the queue before the main while-loop

## Implementation
```cpp
#include <iostream>
#include <queue>
#include <vector>

using namespace std;

// Function to perform Breadth First Search on a graph
// represented using adjacency list
void bfs(vector<vector<int> >& adjList, int startNode,
         vector<bool>& visited)
{
    // Create a queue for BFS
    queue<int> q;

    // Mark the current node as visited and enqueue it
    visited[startNode] = true;
    q.push(startNode);

    // Iterate over the queue
    while (!q.empty()) {
        // Dequeue a vertex from queue and print it
        int currentNode = q.front();
        q.pop();
        cout << currentNode << " ";

        // Get all adjacent vertices of the dequeued vertex
        // currentNode If an adjacent has not been visited,
        // then mark it visited and enqueue it
        for (int neighbor : adjList[currentNode]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

```

## Practice Problems:
- CSES: Labyrinth
- CSES: Building Teams