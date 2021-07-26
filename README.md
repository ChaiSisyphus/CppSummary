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
### string类型与int类型之间相互转化  
```
int out = stoi(string); 能够将string类型转换为int类型  
string out = to_string(int); 能够将int类型转换为string类型  
```
