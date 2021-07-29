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
### unordered_set使用
【1】使用count()函数来对已存入的数据进行计数， 结果只能为1或者0， 在if中进行判断时，相当于contain效果  
【2】集合以其中元素作为索引目标，不再像其他容器一样使用下标进行索引，所有方法传入的参数都只为元素其中元素  
### c++中new创建的对象返回值返回值一定是一个地址  
### c++中对数组进行初始化  
【1】如果以变量进行定义，则定义在栈中，数组的长度必须固定，因此只能使用常量对数组进行初始化  
【2】想要动态定义数组的长度，则需要将数组定义在堆中，使用new关键字创建数组  
【3】建议直接使用vector容器进行定义  
``` 
int *test = new int[len];
delete test;
int **array = new int*[len];
for(int i = 0; i < len; i++) {
	array[i] = new int[len + 1];
}

for(int i = 0; i < len; i++) {
	delete[] array[i];
}
delete[] array;
```
注意数组使用结束后需要将内存进行释放  
