## Overview
- Sometimes, we may be asked to find the maximum/minimum value of an array after being given a list of intervals where the array is modified. An example of this could be customers in a restaurant for time interval $[a, b)$, where we're asked to find the time with the most customers
- A naive solution solves this in $O(n*m)$ time, where n is the total time and m is the number of intervals. This solution physically updates the array for every interval.

- However, we can do better using a [[Prefix Sum]]. By updating an array where the interval begins and where the interval ends, we can calculate the prefix sum of the array to find the actual value of the original array at any time. This reduces our time complexity to $O(\text{max}(n, m))$, or $O(n\log n)$, depending on the parameters of the problem.
- Space: $(O(n))$

## Implementation
```cpp
void sol() {
	int n; cin >> n;
	vector<ii> times;
	for (int i = 0; i < n; i++) {
		int a, b; cin >> a >> b;
		ii start = mp(a, 1);
		ii end = mp(b, -1);
		times.pb(start);
		times.pb(end);
	}

	sort(times.begin(), times.end());

	int cur_people = 0;
	int max_people = 0;
	for (auto i : times) {
		cur_people += i.snd;
		max_people = max(max_people, cur_people);
	}

	cout << max_people << endl;
}
```