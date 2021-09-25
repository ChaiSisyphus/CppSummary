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
### c语言内存分配  
[1] 堆区 栈区 和 全局数据区(静态区)
[2] BSS(bss segment)段用来存放程序中未初始化的全局变量的一块内存区域, 属于静态内存分配
[3] 数据段(data segment) 用来存放程序中已经初始化的全局变量的一块内存区域, 属于静态内存分配  
[4] 代码段(code segment/ text segment) 用来存放程序执行代码的一块内存区域, 字符创常量也属于这部分
### 类的初始化过程  
[1] Class class; 会直接调用Class类的无参构造函数, 对所有成员变量和函数进行0初始化;在栈中开辟内存;  
[2] Class class = new Class(); "()"代表调用构造函数, 根据其中参数列表对应调用的构造函数;  
[3] static修改的成员变量只能在类外通过 int Class::a = 1;的形式进行初始化;  
[4] const修改的成员变量必须显式的进行初始化;  
[5] static const 修改的int类型可以直接在类内初始化;  
### final override const volatile register mutable等做标识符  
[1] 类似java的注释效果, final表示该函数不能再被重写, override表示函数为重写函数, const表示该函数不能修改类中其他的成员变脸
. 如果出现这些情况, 编译器就会报错.  
[2] const函数可以修改被mutable修饰的成员变量  
[3] volatile关键字表示停止编译器对执行的优化禁止指令重排, 并且直接从内存中读取变量的值, 直接绕过缓存和寄存器  
[4] register则让编译器尽可以的把变量的值存入寄存器中, 从而提高数据的读取效率  
### "::"作用域标识符  
### unordered_map适用方法
[1] 利用find()函数, 查看返回值是否为map.end()的迭代器数值, 如果不能根据键找到值就会返回迭代器的end()值;  
[2] 利用count()函数, 计算key值出现的次数, 结果只能为1或者0, 一次来判断map中是否存在该key值;  
### cin与cout的用法
	[1] 标准输入会放入缓冲区中, cin从缓冲区中读取数据, cin永远指向下一个要读的数据; 如果此时指向到空格,tab和或者换行符进行读取操作时, cin会跳过这些间隔符, 在进行读取操作, 但是get()函数并不会跳过这些间隔符;
	[2] cin 和 cout为istream和ostream的对象, 如果操作成功则返回cin和cout的地址, 如果操作失败则返回0;  
	[3]cin有get();方法, 可以获取当前读取的值, 使用cin.get() == '\0'用来判断, 是否读到了行的末尾;cin.get()方法不会丢弃掉换行符;
	[4]cin.getline();方法, 可以一次性读取一行数据, 将数据以char的形式放入容器中;  
### vector容器的begin, end front, back  
	[1] begin()和end()方法, 返回容器起始和终止位置的指针;front()和back()函数返回容器起始和终止位置的数据;  
### c++定义数组  
	[1] c++中定义数组变量必须使用常量定义数组的长度;  
	[2] c++使用new创建数组对象的时候, 可以使用变量进行创建, 如果数组为局部变量, 就必须使用memset函数对数组进行初始化; 因为按照c++的语言规则, 局部变量是不能够自己进行初始化的;   
### c++ 数组容器初始化
	[1] vector初始化: vector<vector<int>> array(3, vecotr<int>(3, 1)); 第一个初始化为3*3, 元素为1的容器;  
	[2] 不可以访问对vector没有赋值的索引进行访问;  
### 注意if(a = 1){}; 这样的语句也是可以运行的, 只是将a赋值为1, 然后判断a的值是否为0, 与if(a == 1){}; 相差深远, 所以一定要仔细仔细;  
### memset使用注意
	[1] memset以字节为单位进行内存覆盖, 如果定义的是int数组, 则计算覆盖长度为sizeof(int) * size;
### vector存储的位置 
	[1] vector创建的对象是在栈上存储的, 但是vector内存存储的数据确实在堆上存储的;  
### 二分法总结
	[1] 最好利用左右指针重合这一条件来进行查找, 因为整个排列数组可能不是满足整体有序的, 并且这样也能避免对边界条件的判断;  
	[2] while(left < right) 作循环结束条件;
	[3] mid=(left+right)/2; 若left/right都不加减一, 则left/right最终会相邻; 若mid=(left+right)/2, left=mid, right=mid-1;则左右指针重合在左指针处;
			       若mid=(left+right+1)/2, left=mid+1, right=mid;则左右指针重合在右指针处;
	[4] 与target相等时不能加减1, 要保证left/right始终与target重合; 
### 有符号数与无符号数之间转换  
	[1] 负数是以补码的形式存储的, 补码: 将整数取反之后加1; 补码转换会整数: 减1后取反; 如果无符号数转为了有符号数, 最高位符号位出现了负数, 则计算其真是数字的顺序:
			       除最高位代表负号外, 将其余位减1, 然后取反;  
### 指针
![image](https://user-images.githubusercontent.com/60838780/134754167-505aefbe-9646-4270-a7be-de302db1ef56.png)
