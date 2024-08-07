## Overview
- Bitmask DP is a dynamic programming technique that uses bit representations of numbers to represent visited nodes or elements of a set
- Commonly used with graphs
- Depending on the application, time and space complexities can vary:
- Time: At least $O(2^n \cdot n)$
- Space: At least $O(2^n)$
## Applications
- Counting Hamiltonian walks
## Steps (2D)
 - The recurrence for bitmask dp is typically: $$dp[S][i] = \sum_{x\in \text{adj}[i]} dp[S \backslash \{i\}][x] \text{ if } x \in S$$
- Note that $S \backslash \{i\}$ represents the set $S$ without the element $i$ in it
## Additional
- If we need to subtract two bitmasks that don't share any set bits, then we can use a xor operation to optimize
## Implementation
Consider CSES Problem: Hamiltonian Flights, which asks for the number of paths in a graph that start from vertex $1$ and end in vertex $n$, going though each of the vertices exactly once:
```cpp
const int N = 20;
    
// rows: paths that cover subset S
// cols: paths ending in i
int dp[1 << N][N];
    
void sol() {
	int n, m; cin >> n >> m;
	vector<vector<int>> rev_adj(n);
	for (int i = 0; i < m; i++) {
		int a, b; cin >> a >> b;
		rev_adj[b-1].pb(a-1);
	}
	dp[1][0] = 1;
	for (int s = 2; s < (1 << N); s++) {
		// Only consider subsets that contain the first city
		if ((s & 1) == 0) continue;
		// Only consider subsets that visit the destination last
		if ((s & (1 << (n-1))) && s != (1 << n) - 1) continue;

		for (int e = 0; e < n; e++) {
			// Only consider subsets that have visited the current end
			if ((s & (1 << e)) == 0) continue; 

			int prev = s - (1 << e);
			for (int v : rev_adj[e]) {
				// Only consider subsets that have visited the previous end
				if ((s & (1 << v)) == 0) continue;

				dp[s][e] += dp[prev][v];
				dp[s][e] %= MOD;
			}
		}
	}
	cout << dp[(1 << n) - 1][n-1] << endl;

}
```

## Practice Problems
- CSES: Elevator Rides (Hard af)