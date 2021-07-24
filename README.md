# CppSummary
### 返回空容器本省
``` 
vector<int> spiralOrder (vector<vector<int>>& matrix) {
	if(matrix.size() == 0 || matrix[0].size() == 0) {
		return {};
	}
```
