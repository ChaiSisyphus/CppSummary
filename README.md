# CppSummary
### 返回空容器本身
``` 
如果返回容器结果为空， 可以直接返回{}即可  
vector<int> spiralOrder (vector<vector<int>>& matrix) {
	if(matrix.size() == 0 || matrix[0].size() == 0) {
		return {};
	}
}  
```
***
