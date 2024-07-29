## Overview
- The Disjoint Set Union (DSU), also known as Union Find, is a data structure that deals with elements that are divided among multiple sets. It is commonly used in graph problems with queries about connected components. The DSU supports two operations: `find(a)` and `union(a, b)`
- `find(a)`: Given some arbitrary element $a$, the DSU returns the set it belongs to. This is done through a representative element, which as the name suggests, represents the entire set. Calling `find()` on the representative element returns itself
	- Time: 
		- Worst case $O(n)$ 
		- Amortized $O(\log n)$ with path compression
		- Amortized $O(\alpha (n))$ with path compression and union by rank. $\alpha (n)$ is the inverse Ackermann function and grows very slow (basically constant)
	- Space: $O(n)$
- `union(a, b)`:  Given two elements $a$ and $b$, the union operation joins the two sets that they belong to. This operation is where we employ optimizations like path compression and union by rank. The union operation uses the find operation internally, so their time and space complexities are the same.
## Applications
- Checking if a vertex belongs to a connected component:
	- This is a pretty straightforward use of the `find()` operation
## Implementation
```cpp
int parent[N];
int set_size[N];

int find_set(int v) {
    if (v == parent[v])
        return v;
    return parent[v] = find_set(parent[v]); // path compression
}
    
void make_set(int v) {
    parent[v] = v;
    set_size[v] = 1;
}

void union_sets(int a, int b) {
    a = find_set(a);
    b = find_set(b);
    if (a != b) {
        if (set_size[a] < set_size[b]) // union by rank
            swap(a, b);
        parent[b] = a;
        set_size[a] += set_size[b];
    }
}
```