## Overview
- Given a sorted collection of elements, binary search allows us to find whether or not an element exists in $O(\log n)$ time
- Very flexible implementation and open to many variations


## Implementation

Classic Implementation
- In this implementation, if the target does not exist in the array, the left pointer points to the index where the target would be
```cpp
int binary_search(vector<int> nums, int target):
	int l = 0, r = nums.size() - 1;

	while l <= r:
		int mid = (l+r) >> 1;
		if (target == nums[mid])
			return;
		elif (target > nums[mid])
			left = mid+1;
		else: 
			right = mid-1;

	return -1;
```

Decreasing then Increasing (Bitonic)
```cpp
int minimal(int a[], int n)
{
    int lo = 0, hi = n - 1;
 
    // Do a binary search
    while (lo < hi) {
 
        // Find the mid element
        int mid = (lo + hi) >> 1;
 
        // Check for break point
        if (a[mid] < a[mid + 1]) {
            hi = mid;
        }
        else {
            lo = mid + 1;
        }
    }
 
    // Return the index
    return lo;
}
```