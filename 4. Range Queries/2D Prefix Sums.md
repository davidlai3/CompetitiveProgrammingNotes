```cpp
void prefixSum(vector<vector<int>> mat, int n) {  
	//vertical prefixsum  
	for (int j = 0; j < n; j++) {  
		for (int i = 1; i < n; i++) {  
			mat[i][j] += mat[i-1][j];  
		}  
	}  
	//horizontal prefixsum  
	for (int i = 0; i < n; i++) {  
		for (int j = 1; j < n; j++) {  
			mat[i][j] += mat[i][j-1];  
		}  
	}  
}
```