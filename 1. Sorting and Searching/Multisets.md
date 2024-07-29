## Overview
- Multisets are a type of sorted associative container similar to the set, with the exception that multiple elements can have the same value. The underlying data structure is typically a self-balancing binary search tree
- Operations:
	- `insert(x)`: $O(\log n)$
	- `clear()`: $O(n)$
	- `erase()`: O(\log n)
	- `upper_bound(x)`: $O(\log n)$
	- `lower_bound(x)`: $O(\log n)$