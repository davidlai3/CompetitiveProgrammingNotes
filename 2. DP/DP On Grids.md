## Overview
- When it comes to counting grid paths or performing queries on grids, sometimes it's helpful to use a DP. This is especially true if our movement is limited (e.g. we can only move down and right), as DP proves to be faster than conventional algorithms like Dijkstra's or backtracking.
- Time: $O(n^2)$ memoized
- Space: $O(n^2)$

## Implementation:
- The function below counts grid paths starting from the top left and ending at the bottom right
```cpp
int dp[N][N];
char mt[N][N];

// returns the number of paths to get to mt[i][j]
int calc(int i, int j) {
	if (i < 0 || j < 0) return 0;
	if (mt[i][j] == '*') return 0;
	if (i == 0 && j == 0) return 1;
	if (dp[i][j] != INT_MAX) return dp[i][j];
	return dp[i][j] = (calc(i-1, j) + calc(i, j-1)) % MOD;
}
    
void sol() {
	int n; cin >> n;
	for (int i = 0; i < n; i++) {
		for (int j = 0; j < n; j++) {
			cin >> mt[i][j];
		}
	}

	for (int i = 0; i < n; i++) {
		fill_n(dp[i], n, INT_MAX);
	}
	cout << calc(n-1, n-1) << endl;
}
```
## Problems
- CSES: Grid Paths
- LeetCode #64: Minimum Sum Path