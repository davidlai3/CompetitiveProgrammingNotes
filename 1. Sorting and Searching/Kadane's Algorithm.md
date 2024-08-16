## Overview
- Kadane's algorithm is used to find the maximum subarray sum from a given array 
	- Of course, this array must contain negatives or else the maximum subarray would just be the entire array
- The main intuition behind Kadane's algorithm is that we discard any subarrays with negative sum, while preserving any subarrays that have a positive time
- Time: $O(n)$
- Space: $O(1)$

## Implementation
- There are two basic variations, depending on the rules of your subarray:
	1. Subarray may contain no elements, for a total sum of 0
	2. Subarray must contain at least one element
- Variation 1:
```cpp
void sol() {
	int n; cin >> n;
	vector<int> a(n);
	for (int i = 0; i < n; i++) cin >> a[i];

	int max_sum = 0;
	int cur_sum = 0;
	for (int x : a) {
		cur_sum += x;
		if (cur_sum > max_sum) {
			max_sum = cur_sum;
		}
		if (cur_sum < 0) {
			cur_sum = 0;
		}
	}
 
	cout << max_sum << endl;
}

```
- Variation 2:
```cpp
void sol() {
	int n; cin >> n;
	vector<ll> a(n);
	for (int i = 0; i < n; i++) cin >> a[i];

	ll max_sum = -INT_MAX;
	ll cur_sum = 0;
	for (int x : a) {
		if (cur_sum < 0) {
			cur_sum = 0;
		}
		cur_sum += x;
		if (cur_sum > max_sum) {
			max_sum = cur_sum;
		}
	}
 
	cout << max_sum << endl;
}
```