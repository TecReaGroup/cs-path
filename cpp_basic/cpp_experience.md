# C++

## Comment（注释）

1. 单行注释：`// comment`
2. 多行注释：`/* comment */`

## IO-I

简介：

1. 键盘缓冲区：如果用户在按回车之前输入了过多字符，其他字符会保留在键盘缓冲区中，等待后续调用读取，注意缓存区中`"\n"`换行符的处理
2. 输入返回判断：
   1. cin, getline(): 可以直接作为判断条件 `if (cin >> s)//ctrl + z 终端表示输入结束(而不是Enter)`
   2. scanf: 返回读取到的合法元素数量，读完或者出错返回值EOF `if (scanf("%c", &c) != EOF) //EOF == -1`
   3. getchar: 返回读取到的字符ASCII码值，读完或者出错返回值EOF

### scanf

1. double: 以科学计数法表示，所以相对于long long类型可以接受更大的数，但存在精度损失（常用于阶乘和幂运算数据类型）
2. scanf返回值: “所输入的数据与格式字符串中匹配次数.”返回已成功赋值的数据项数；出错时则返回EOF.（注：EOF(End Of File)是一个预定义的常量，等于-1.）。常用方式（循环读取输入）：

```c++
while(scanf("%d %d",&a, &b) != EOF){
        //pass
    }  
```

scanf参数类型说明
![scanf](.\photos\scanf.png "scanf")

### getline

syntax: `getline(cin, s);`

### cin

syntax: `cin >> variable //以空格划分，分别读取`

### getchar

syntax: `c = getchar();`

## IO-O

### printf

1. printf .nf: 会对最后一项四舍五入
2. printf %nd: 保留n位数多余用空格补充（右对齐）; 左对齐：%-nd。如果参数过长，以参数长度为准，不会进行截断

![printf](.\photos\printf.png "printf")

### cout

`cout << ans;`

## vector(容器)

## memset

1. syntax：`memset(array, initial_value, sizeof_array)`

## sort

1. syntax: `sort(array_header_adress, array_tail_adress, compare_function) //a < b reurn true -> order sorting (default); a > b return true -> reverse sorting`
2. stable_sort: 排序稳定性：sort函数不保证排序的稳定性，也就是说，如果两个字符串的长度相同，它们在排序后的相对顺序可能会改变。如果你需要保持相同长度的字符串的原始顺序，你可以使用stable_sort函数代替sort函数。

## map

Example：

```c++
        map<char, char> mapping = {
        {'A', 'X'}, {'B', 'Y'}, {'C', 'Z'}, {'D', 'A'}, {'E', 'B'}, {'F', 'C'},
        {'G', 'D'}, {'H', 'E'}, {'I', 'F'}, {'J', 'G'}, {'K', 'H'}, {'L', 'I'},
        {'M', 'J'}, {'N', 'K'}, {'O', 'L'}, {'P', 'M'}, {'Q', 'N'}, {'R', 'O'},
        {'S', 'P'}, {'T', 'Q'}, {'U', 'R'}, {'V', 'S'}, {'W', 'T'}, {'X', 'U'},
        {'Y', 'V'}, {'Z', 'W'}
    };
    mapping["C"]
```

## string

### string输入

1. scanf //%nd 表示读取n个字符的数字
2. cin
3. getline
4. getchar
5. 汉字输入：一个汉字在UTF-8编码中占三个字节，所以每个汉字需取出前三个字节。

```c++
string line;
        getline(cin, line);
        cout << line.substr(0, 3);
```

### 常用函数

1. strcpy(s1, s2);
   复制字符串 s2 到字符串 s1。
2. strcat(s1, s2);
   连接字符串 s2 到字符串 s1 的末尾。连接字符串也可以用 + 号，例如:
   string str1 = "runoob";
   string str2 = "google";
   string str = str1 + str2;
3. strlen(s1);
   返回字符串 s1 的长度。
4. strcmp(s1, s2);
   如果 s1 和 s2 是相同的，则返回 0；如果 s1<s2 则返回值小于 0；如果 s1>s2 则返回值大于 0。
5. strchr(s1, ch);
   返回一个指针，指向字符串 s1 中字符 ch 的第一次出现的位置。
6. strstr(s1, s2);
7. reverse(temp2.begin(), temp2.end());
   返回一个指针，指向字符串 s1 中字符串 s2 的第一次出现的位置。

### 常用演示代码

```c++
// 复制 str1 到 str3
str3 = str1;
cout << "str3 : " << str3 << endl;

// 连接 str1 和 str2
str3 = str1 + str2;
cout << "str1 + str2 : " << str3 << endl;

// 连接后，str3 的总长度
len = str3.size();
cout << "str3.size() :  " << len << endl;

// find: string中find()返回值是字母在母串中的下标位置。如果没有找到，那么会返回一个特别的标记npos，一般写作string::npos
string::size_type idx;
idx=a.find(b);
idx == string::npos //未找到匹配字符串

//for遍历字符串（数组同理）
for (char c : s) //复制一个s字符串再进行遍历操作
for (char& c : s) //直接引用原字符串进行遍历操作

//删除字符串部分内容erase
str.erase(开始位置, 删除的字符串长度)

//compare
a > b: 依次比较a，b字符串的字符ascii码大小
```

## swap(交换元素)

syntax: `swap(parameter1, parmeter2);`

## Pointer item(指针)

& 取址符
*指针

1. type* argument 指针
2. *argument 指针值

## Ternary arithmetic(三目运算)

a = b > c ? 1 : 2 //如果b>c则a=1，不然a=2

## Remeber

1. 循环，迭代末尾注意变量初始化 or 循环块内定义局部变量
2. 注意边界条件，题目要求不清楚时进行合理猜测
3. getline读取数据后,缓存区内可能还存在"\n"
