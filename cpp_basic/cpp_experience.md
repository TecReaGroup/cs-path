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

## priority_queue

`priority_queue<type, vector_type, comparefunction> heap_name;`

```cpp
// 3D 接雨水

// 定义自定义数据结构
class CustomData {
public:
    int key;      // 第一个元素
    int value1;   // 第二个元素
    int value2;   // 第三个元素

    CustomData(int k, int v1, int v2) : key(k), value1(v1), value2(v2) {}

    // 重载小于操作符用于比较
    bool operator>(CustomData other) const {
        return this->key > other.key;
    }
};

// 自定义比较函数
struct Compare {
    bool operator()(CustomData lhs, CustomData rhs) {
        return lhs > rhs; // 使用重载的操作符
    }
};


class Solution {
 public:
    // 407. 接雨水 II
    int trapRainWater(vector<vector<int>>& heightMap) {
        vector<vector<char>> visited(200, vector<char>(200, 0));
        priority_queue<CustomData, vector<CustomData>, Compare> minHeap;
        int m = heightMap.size(), n = heightMap[0].size();
        for (int i = 0; i < m; i++) {
            minHeap.push(CustomData(heightMap[i][0], i, 0));
            minHeap.push(CustomData(heightMap[i][n - 1], i, n - 1));
            visited[i][0] = 1;
            visited[i][n - 1] = 1;
        }
        for (int i = 0; i < n; i++) {
            minHeap.push(CustomData(heightMap[0][i], 0, i));
            minHeap.push(CustomData(heightMap[m - 1][i], m - 1, i));
            visited[0][i] = 1;
            visited[m - 1][i] = 1;
        }

        int ans = 0;
        vector<vector<int>> directions = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        while (!minHeap.empty()) {
            CustomData data = minHeap.top();
            minHeap.pop();
            for (auto direction : directions) {
                int x = data.value1 + direction[0];
                int y = data.value2 + direction[1];
                if (x >= 0 && x < m && y >= 0 && y < n && !visited[x][y]) {
                    ans += max(0, data.key - heightMap[x][y]);
                    visited[x][y] = 1;
                    heightMap[x][y] = max(data.key, heightMap[x][y]);
                    minHeap.push(CustomData(heightMap[x][y], x, y));
                }
            }
        }

        return ans;
    }
};
```

syntax: `swap(parameter1, parmeter2);`

## Pointer item (指针)与迭代器

& 取址符
*指针

1. type* argument 指针
2. *argument 指针值

`std::distance`函数之所以能够处理指针，是因为在C++标准库中，指针被视为一种特殊类型的迭代器，即随机访问迭代器（Random Access Iterator）。迭代器是C++标准库中用来统一访问容器中元素的抽象概念，而指针符合迭代器的要求，因此可以用于迭代器的许多操作和算法中，包括`std::distance`函数。

### 迭代器概念

在C++标准库中，迭代器被分为几种类型，每种类型有不同的特性和用途：

1. **输入迭代器（Input Iterator）**：只能读取数据，支持单向遍历。
2. **输出迭代器（Output Iterator）**：只能写入数据，支持单向遍历。
3. **前向迭代器（Forward Iterator）**：可以读取和写入数据，支持单向遍历，并且可以多次遍历同一个序列。
4. **双向迭代器（Bidirectional Iterator）**：除了前向迭代器的功能，还可以反向遍历。
5. **随机访问迭代器（Random Access Iterator）**：除了双向迭代器的功能，还支持常数时间的跳跃访问，如指针算术操作。

指针满足随机访问迭代器的所有要求：

- 可以进行加法和减法操作（如`ptr + n`, `ptr - n`）。
- 可以进行比较操作（如`ptr1 < ptr2`, `ptr1 == ptr2`）。
- 可以进行解引用操作（如`*ptr`）。
- 可以进行偏移解引用操作（如`ptr[n]`）。

### `std::distance`函数

`std::distance`是一个标准库函数，用于计算两个迭代器之间的距离。其原型如下：

```cpp
template <class InputIterator>
typename std::iterator_traits<InputIterator>::difference_type
distance(InputIterator first, InputIterator last);
```

对于随机访问迭代器，`std::distance`可以在常数时间内计算两个迭代器之间的距离。对于其他类型的迭代器，`std::distance`可能需要线性时间。

由于指针是随机访问迭代器的一种，`std::distance`可以直接接受指针作为参数，并且能够高效地计算指针之间的距离。例如：

```cpp
#include <iostream>
#include <iterator>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int *begin = arr;
    int *end = arr + 5;

    std::cout << "Distance: " << std::distance(begin, end) << std::endl;
    return 0;
}
```

在这个例子中，`begin`和`end`都是指向数组元素的指针，`std::distance`计算并输出它们之间的距离。

### 结论

`std::distance`能够处理指针是因为指针在C++标准库中被视为随机访问迭代器的一种。因此，指针可以用于任何要求迭代器的算法和操作中，包括`std::distance`。这使得指针在与标准库算法和容器交互时非常方便和高效。

cpp中指针与数组的迭代器的区别:

- 数组指针: 数组指针指向数组的第一个元素. 通过指针, 可以访问数组中的各个元素. 数组指针本质上是一个普通指针, 用来指向数组中的某个元素.

```cpp
int arr[] = {1, 2, 3, 4, 5};
int *ptr = arr; // ptr指向arr的第一个元素

for (int i = 0; i < 5; ++i) {
    std::cout << *(ptr + i) << " "; // 通过指针访问数组元素
}
```

- 数组迭代器: 数组迭代器是一个更抽象的概念, 通常在标准模板库 (STL) 中使用. 迭代器是一种对象，它可以遍历容器中的元素. 数组迭代器在功能上类似于数组指针, 但它们被设计为与STL算法和容器一起使用.

```cpp
#include <iostream>
#include <algorithm>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    auto begin = std::begin(arr);
    auto end = std::end(arr);

    for (auto it = begin; it != end; ++it) {
        std::cout << *it << " "; // 通过迭代器访问数组元素
    }
}
```

- 区别:

  - 概念和使用范围：数组指针是一个低级概念，特指指向数组元素的指针，而迭代器是一个高级概念，适用于遍历容器中的元素。迭代器不仅适用于数组，还适用于其他STL容器（如std::vector, std::list等）。

  - 功能：迭代器通常提供更多的功能和类型安全性，例如支持不同的迭代器类别（输入迭代器、输出迭代器、前向迭代器、双向迭代器和随机访问迭代器），而数组指针则只提供基本的指针操作。

  - 与STL的兼容性：STL的许多算法和容器都设计为使用迭代器。虽然数组指针可以用作随机访问迭代器，但使用STL算法时，迭代器的接口和类型安全性使其更为优越。

  - 抽象级别：迭代器抽象级别更高，提供了一个统一的接口来遍历不同类型的容器，而数组指针则更具体，直接与内存地址和指针算术打交道。

- 总结: 数组指针是一个指向数组元素的指针，可以看作是一个简单的迭代器，但迭代器的概念更广泛，更加抽象，并提供了与STL算法和容器兼容的接口。

## Ternary arithmetic(三目运算)

a = b > c ? 1 : 2 //如果b>c则a=1，不然a=2

## Remeber

1. 循环，迭代末尾注意变量初始化 or 循环块内定义局部变量
2. 注意边界条件，题目要求不清楚时进行合理猜测
3. getline读取数据后,缓存区内可能还存在"\n"
