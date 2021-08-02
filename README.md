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
### java与c++中变量,引用,指针关系  
[1] java主要通过引用(指针常量)来访问数据, 因此数据分为基本数据类型与引用数据类型, 
并且在使用引用数据类型时, 只能通过引用进行间接操作, 因此存入容器和赋值时都是拿引用进行操作,不直接操作数据, 相当于指向
固定地址的指针, 因此需要不断创建新的对象, 来避免容器中或者多个变量指向同一个地址, 修改其中一个其余所有数据都会发生变化
[2] c++将数据类型进行拓展, 加入指针, 可以直接对数据内容和指向的地址进行修改, 并且只有new操作时才能创建对象, 同时返回一个
指针(java中返回一个引用). 同时也可以拿类创建变量, 如:string s; s就是string类型的变量, string *s = new string();
当定义为变量时, 直接操作数据本身, 比如vector<string>, 泛型定义的就是string变量类型, 加入容器中的就是string变量, 就不再需要
考虑, 变量相互影响的问题  
### c++返回地址问题
```
	vector<TreeNode> v1 = getPath(root, *p);
	TreeNode *result = new TreeNode(v1[p1 - 1]);
	return result;
```  
[1]vector这这里是一个局部变量, 其中元素也是一个局部变量, 因此想要返回其中元素的地址必须使用new来创建一个对象, 然后将内容拷贝复制过去.
不能直接返回地址, 因此函数结束运行后会出栈, 对应地址中的内容会发生变化
	
	
	
	
