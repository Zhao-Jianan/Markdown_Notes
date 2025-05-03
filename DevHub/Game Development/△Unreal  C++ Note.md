# UE C++
## C++概念
C++是一种静态类型的、编译式的、通用、大小写敏感的不规则编程语言，支持面向过程，面向对象和泛型编程

扩充和完善了C语言，任何合法的C程序都是合法C++程序

### 面向对象程序设计
3大特征：封装、继承、多态
4大特征：封装、继承、抽象、多态

### 标准库
标准C++由三个重要的组成部分
1. 核心语言: 提供构件块，包含变量 数据类型和常量等等
2. C++标准库 ：提供大量的函数 用于操作字符串 操作文件等
3. 标准模板库（STL）用于操作数据结构的函数

**ANSI编码标准：为了实现不同平台下编译的通用性**

```
#include <iostream> //引入头文件 iostream 输入输出流
using namespace std;//使用std命名空间
int main()//程序入口 main函数 后台自动调用
{ 
}
```

### 数据类型的归类和使用
编程语言进行编程时，需要使用各种不同的变量来存储数据

变量保留的是它所存储的内存位置，创建一个变量，就是在内存中保留一定的空间

常用数据类型 字符型 宽字符型 整型 浮点型 双浮点型 布尔型等等

#### 基本内置类型
| 数据类型  | 说明                   |
|:-----------|:----------------------|
| `bool`      | 布尔型，表示真或假       |
| `char`      | 字符型，存储单个字符     |
| `int`       | 整型，存储整数值         |
| `float`     | 浮点型，单精度浮点数     |
| `double`    | 双精度浮点型             |
| `void`      | 无类型，通常用于函数无返回值 |
| `wchar_t`   | 宽字符型，支持多字节字符   |

不同的数据类型 所占据的内存大小是不同的 能存储的取值范围不同

一个字节 是8位二进制
1个字节等于8位的原因：因为8位能够涵盖所有的字符编码

int占4个字节 所以一共是32位二进制
sizeof函数 可以得到具体类型的所占内存大小
```
cout <<sizeof(int)<< endl;//4 int占4个字节
cout <<sizeof(bool) << endl;//1 bool占1个字节
cout <<sizeof(char) << endl;//1 char占1个字节
cout << sizeof(float) << endl;//4 float占4个字节
cout << sizeof(double) << endl;//8 double占8个字节
```

int a=100;--------在内存中开辟了4个字节空间 存储一个整数变量 变量名是a 存储的值是100


**在同一个作用域范围内 不能出现同名变量**

所有数据类型都有其最大值和最小值
int的最大值2147483647 最小值-2147483648

计算机只识别二进制
数据类型的取值范围是由二进制决定的


## 二进制和十六进制
十进制 逢十进位
二进制 逢二进位
十六进制 逢十六进位
int=4byte 1byte=8bit 所以一个int共占用32位二进制
1的二进制表示 00000000 00000000 00000000 00000001


**0开头的是八进制数**
**0x开头的是十六进制数**

### 十进制转二进制
找最近的2的N次幂

例1
256  ---- 100000000

例2
```
176
=128+48
=128+32+16
=2(7)+2(5)+2(4)
10000000 2(7)
 100000 2(5)
 10000 2(4)
--------------------
 10110000
```

### 二进制转十进制
```
1001001110
=2(9)+2(6)+2(3)+2(2)+2(1)
14 1110 e
15 1111 f
16 10000 10
=512+64+8+4+2
=590
```

### 十六进制和二进制的关系
二进制的1111 是十六进制的F 十进制的15
所以满足以下规律:
- 二进制转十六进制四转一 遵循8421法则
十六进制转二进制是一转四

例
```
1001011011101111 转十六进制 四转一
1001 0110 1110 1111
=0x96EF
10010 转十六进制 四转一
0001 0010 
=0x12
例
0x1FA5 转二进制 1转4
=0001 1111 1010 0101
```

### 负数的二进制问题
在计算机的二进制存储机制中把最高（左边）位置的0或1 代表正和负

| 符号 | 二进制表示                             | 说明   |
|:------|:---------------------------------------|:--------|
| 正数  | `00000000 00000000 10000000 00000001` | 最高位为 `0`，表示正数 |
| 负数  | `10000000 00000000 10000000 00000001` | 最高位为 `1`，表示负数（补码形式） |

负数的二进制的计算方式：**正数二进制取反加一**

-1的二进制
先得到1的二进制结果
00000000 00000000 00000000 00000001
所以用二进制表示int的最大值
01111111 11111111 11111111 11111111 转换得到的十进制结果是2147483647 （2的31次 方-1）

二进制的int的最小值
1000000 0000000 0000000 00000000 转换得到的十进制结果是-2147483648 （-2的
31次方）

char占1个字节
最大值
01111111 127
最小值
10000000 -128

unsigned和signed
unsigned int
无符号的整型最大值
11111111 11111111 11111111 11111111 
无符号的整型最小值
### 补码计算过程示例

| 操作步骤 | 二进制结果                           | 说明       |
|:------------|:-------------------------------------|:------------|
| 原码（0）     | `00000000 00000000 00000000 00000000` | 原数为 0     |
| 取反         | `11111111 11111111 11111111 11111111` | 所有位取反   |
| 加一         | `00000000 00000000 00000000 00000000` | 结果回到 0（补码加法溢出舍弃进位） |

---

| 操作步骤 | 二进制结果                           | 说明       |
|:------------|:-------------------------------------|:------------|
| 原码（-1）    | `11111111 11111111 11111111 11111110` | 原数为 -1 的反码 |
| 加一         | `11111111 11111111 11111111 11111111` | 得到 -1 的补码 |



所以用二进制表示int的最大值
01111111 11111111 11111111 11111111 转换得到的十进制结果是2147483647 （2的31次 方-1）
二进制的int的最小值
1000000 0000000 0000000 00000000 转换得到的十进制结果是-2147483648 （-2的
31次方）

char占1个字节
最大值
01111111 127
最小值
10000000 -128


### unsigned和signed
unsigned int
无符号的整型最大值
11111111 11111111 11111111 11111111 
无符号的整型最小值
0000000 0000000 0000000 00000000
unsigned char
无符号的char最大值
11111111 255
无符号的char最小值
00000000 0

### 位运算
位运算是二进制的基础数学运算，程序中的所有计算，本质上都是二进制的计算
#### 常用位运算符及规则

| 符号   | 含义   | 运算规则 |
|:--------|:--------|:------------------------------------------------|
| `&`     | 与      | 两个位都是 `1` 时，结果为 `1`，否则为 `0` |
| `\|`    | 或      | 只要有一个位是 `1`，结果为 `1` |
| `^`     | 异或    | 两个位不同（0 和 1 或 1 和 0）时，结果为 `1` |
| `~`     | 取反    | 将所有位上的 `0` 和 `1` 取反 |
| `<<`    | 左移    | 所有位向左移动若干位，高位丢弃，低位补 `0` |
|         |         | 十进制左移前需转二进制，`X << Y` 等于 `X × (2^Y)` |
| `>>`    | 右移    | 所有位向右移动若干位，正数高位补 `0`，负数高位补 `1`，低位丢弃 |
|         |         | 十进制右移前需转二进制，`X >> Y` 等于 `X ÷ (2^Y)`，取整（舍弃小数部分） |



#### 一些位运算规律
1.判断一个数是奇数还是偶数（取决于二进制最低位是0还是1）可以使用方法：
X&1  结果是0则X为偶数，结果为1则X为奇数

2.交换a和b的值


$$
a=a^b;
b=a^b;
a=a^b;
$$


规律：两个数的异或结果，再异或其中一个数，得另一个数

3.计算2的X次方
```
1<<X
```
结果是2的(X+1)次方


## UE4中的容器
### TArray
UE4中的数组，元素类型是存储在数组中的对象类型。TArray被称为同质容器。换言之，其所有元素均完全为相同类型。单个TArray中不能存储不同类型的元素

**Tarray为数值类型。与其他内置类型的处理方式相同。其设计时未考虑扩展问题，因此在实际操作中不使用新建（new）和删除（delete）创建或销毁TArray实例。元素也为数值类型，为容器所拥有**

TArray被销毁时其中的元素也将被销毁。若在另一TArray中创建TArray变量，其元素将复制到新变量中，且不会共享状态

#### 语法
##### 创建数组
语法：
```
TArray<数据类型>数组名
```
**由于无指定分配器，因此 TArray 将采用基于堆的默认分配器。此时尚未分配内存**

##### 填充数组
填充数组方法有很多
###### 方法1-----Init
使用Init函数，可以将大量元素副本填入数组
例
```
IntArray.Init(10, 5);
// IntArray == [10,10,10,10,10]
```
###### 方法2-----Add/Emplace
使用Add和Emplace函数用于在数组末尾新建对象

*蓝图中有Add方法*

例
```
TArray<FString> StrArr;
StrArr.Add    (TEXT("Hello"));
StrArr.Emplace(TEXT("World"));
// StrArr == ["Hello","World"]
```
Add和Emplace的区别：
- Add（或Push）将元素类型的实例复制（或移动）到数组中
- Emplace使用给定参数构建元素类型的新实例
因此在 TArray<FString> 中，Add将用字符串文字创建临时FString，然后将该临时 FString 的内容移至容器内的新 FString 中；而Emplace将用字符串文字直接新建FString。最终结果相同，但Emplace可避免创建临时文件

总结：
Emplace 优于 Add，因此其可避免在调用点创建无需临时变量，并将此类变量复制或移动到容器中。根据经验，可将 Add 用于浅显类型，将 Emplace 用于其他类型。Emplace 的效率始终高于 Add，但 Add 的可读性可能更好

###### 方法3-----Append
使用Append可以一次性添加其他TArray中的多个元素，或者指向常规C数组的指针及该数组的大小
例
```
FString Arr[] = { TEXT("of"), TEXT("Tomorrow") };
StrArr.Append(Arr, ARRAY_COUNT(Arr));
// StrArr == ["Hello","World","of","Tomorrow"]
```
###### 方法4-----AddUnique
仅在数组中没有这个新元素时，AddUnique才会向容器添加新元素

*蓝图中有AddUnique方法*

```
StrArr.AddUnique(TEXT("!"));
// StrArr == ["Hello","World","of","Tomorrow","!"]

StrArr.AddUnique(TEXT("!"));
// StrArr is unchanged as "!" is already an element
```

###### 方法5-----Insert
Insert将在给定索引处添加单个元素或元素数组的副本

*蓝图中有AddUnique方法*

```
StrArr.Insert(TEXT("Brave"), 1);
// StrArr == ["Hello","Brave","World","of","Tomorrow","!"]
```

###### 方法6-----SetNum
SetNum函数可直接设置数组元素的数量。如新数量大于当前数量，则使用元素类型的默认构造函数新建元素
```
StrArr.SetNum(8);
// StrArr == ["Hello","Brave","World","of","Tomorrow","!","",""]
```

##### 迭代遍历
###### 方法1-----使用C++的范围（ranged-for）功能
一般都使用这个方法
例1：
```
for(const Fstring& val:StrArr)
{
   UKismetSystemLibrary::PrintString(this,val);
}
```
例2：
```
FString JoinedStr;
for (auto& Str :StrArr)
{
    JoinedStr += Str;
    JoinedStr += TEXT(" ");
}
// JoinedStr == "Hello Brave World of Tomorrow !"
```
###### 方法2-----使用基于索引的常规迭代
```
for (int32 Index = 0; Index != StrArr.Num(); ++Index)
{
    JoinedStr += StrArr[Index];
    JoinedStr += TEXT(" ");
}
```
###### 方法3-----使用数组迭代器类型控制迭代
函数 CreateIterator 和 CreateConstIterator 可分别用于元素的读写和只读访问

例1：
```
for (TArray<FString>::TConstIterator It = StrArr.CreateConstIterator(); It; ++It)
{
    UKismetSystemLibrary::PrintString(this,*It);
}
```

例2：
```
for (auto It = StrArr.CreateConstIterator(); It; ++It)
{
    JoinedStr += *It;
    JoinedStr += TEXT(" ");
}
```

##### 排序
###### Sort
调用 Sort 函数即可对数组进行排序

可以使用二元谓词实现不同的排序规则
```
StrArr.Sort([](const FString& A, const FString& B) {
    return A.Len() < B.Len();
});
// StrArr == ["!","of","Hello","Brave","World","Tomorrow"]
```
**Sort不稳定，等值元素的相对排序无法保证**

###### HeapSort
无论是否使用二元谓词，均可用于执行堆排序。使用HeapSort函数与否，取决于特定数据与Sort函数相比时的排序效率

**HeapSort不稳定，等值元素的相对排序无法保证**

###### StableSort
StableSort用于在排序后保证等值元素的相对顺序
```
StrArr.StableSort([](const FString& A, const FString& B) {
    return A.Len() < B.Len();
});
// StrArr == ["!","of","Brave","Hello","World","Tomorrow"]
```

##### 查询
###### Num
使用 Num 函数可查询数组保存的元素数量
```
int32 Count = StrArr.Num();
```

###### GetData
如需直接访问数组内存（如确定C类API的互操作性），可使用GetData函数将指针返回到数组中的元素。仅在数组存在且未执行更改数组的操作时，此指针方有效。仅StrPtr的首个Num指数才可被解除引用
例：
```
FString* StrPtr = StrArr.GetData();
```

###### GetTypeSize
查询容器的大小，相当于sizeof

*蓝图中有对应的Length方法*
```
uint32 ElementSize = StrArr.GetTypeSize();
// ElementSize == sizeof(FString)
```
###### 运算符[]
根据索引获取数组中的元素

###### IsValidIndex
返回一个布尔值，判断传入的索引是否有效

###### Last
从数组末端反向索引，索引默认为0

###### Top
返回数组的最后一个值，Top不接受索引
```
FString ElemEnd  = StrArr.Last();
FString ElemEnd0 = StrArr.Last(0);
FString ElemEnd1 = StrArr.Last(1);
FString ElemTop  = StrArr.Top();
// ElemEnd  == "Tomorrow"
// ElemEnd0 == "Tomorrow"
// ElemEnd1 == "World"
// ElemTop  == "Tomorrow"
```
###### Contains
■蓝图中有对应的Contains Item方法
返回一个布尔值，判断数组是否包含特定元素
```
bool bHello = StrArr.Contains(TEXT("Hello"));
```
###### ContainsByPredicate
返回一个布尔值，判断数组是否包含与特定谓词匹配的元素
```
bool bLen5 = StrArr.ContainsByPredicate([](const FString& Str){
    return Str.Len() == 5;
});
```
###### Find
查找元素是否存在，存在会返回索引,如果有重复，返回第一个索引。同时函数会返回布尔值，未找到元素，将返回特殊 INDEX_NONE 值
*蓝图中有Find Item方法*
```
int32 Index;
if (StrArr.Find(TEXT("Hello"), Index))
{
    // Index == 3
}
```

###### FindLast
如果有重复的元素，会返回重复元素的最后一个索引

###### IndexOfByKey
IndexOfByKey适用于存在运算符==(ElementType, KeyType)的键类型。IndexOfByKey将返回找到的首个元素的索引；如未找到元素，则返回INDEX_NONE

###### IndexOfByPredicate
IndexOfByPredicate函数用于查找与特定谓词匹配的首个元素的索引；如未找到，同样返回特殊INDEX_NONE值

###### FindByKey
FindByKey与IndexOfByKey相似，将元素和任意对象进行对比，但返回指向所找到元素的指针。如未找到元素，则返回nullptr
```
auto* OfPtr  = StrArr.FindByKey(TEXT("of")));
auto* ThePtr = StrArr.FindByKey(TEXT("the")));
// OfPtr  == &StrArr[1]
// ThePtr == nullptr
```
###### FindByPredicate
FindByPredicate 的使用方式和 IndexOfByPredicate 相似，不同点是返回指针而非索引
```
auto* Len5Ptr = StrArr.FindByPredicate([](const FString& Str){
    return Str.Len() == 5;
});
auto* Len6Ptr = StrArr.FindByPredicate([](const FString& Str){
    return Str.Len() == 6;
});
// Len5Ptr == &StrArr[2]
// Len6Ptr == nullptr
```

###### FilterByPredicate
可获取与特定谓词匹配的元素数组
```
auto Filter = StrArray.FilterByPredicate([](const FString& Str){
    return !Str.IsEmpty() && Str[0] < TEXT('M');
});
```
##### 移除
###### Remove
用于移除数组中所有与提供的值相同的元素

*蓝图中有对应的Remove Item方法*
###### RemoveSingle
用于移除数组中所有与提供的值相同的第一个元素
###### RemoveAt
按提供的索引移除元素，无效索引将会出错，会直接导致游戏崩溃

*蓝图中有对应的Remove Index方法*
###### RemoveAll
移除与谓词匹配的元素
```
ValArr.RemoveAll([](int32 Val) {
    return Val % 3 == 0;
});
// ValArr == [10,5,25]
```
**在所有这些情况中，由于数组中不能出现空位，因此移除元素时其后的元素向前移动**
###### RemoveSwap
Remove的剩余元素不排序版本，因为剩余元素不用向前移动，所以会节省这部分开销，但是不能保证剩余元素的排序是符合需求的
###### RemoveAtSwap
RemoveAt的剩余元素不排序版本，因为剩余元素不用向前移动，所以会节省这部分开销，但是不能保证剩余元素的排序是符合需求的
###### RemoveAllSwap
RemoveAll的剩余元素不排序版本，因为剩余元素不用向前移动，所以会节省这部分开销，但是不能保证剩余元素的排序是符合需求的

###### Empty
移除数组中所有元素

*蓝图中有对应的Clear方法*


##### 运算符
###### +=
+=可以替代Append，对数组进行串联

###### MoveTemp
移动，将一个数组中的元素移动到另一个数组，移动后源数组必定为空，如果新数组原来有元素，会覆盖原有元素
```
ValArr3 = MoveTemp(ValArr4);
// ValArr3 == [5,2,3,1,2,3]
// ValArr4 == []
```

###### ==和!=
使用 运算符== 和 运算符!= 可对数组进行比较。元素的排序很重要：只有元素的顺序和数量相同时，两个数组才被视为相同

### TMap
TMap容器将数据存储为键值对 ```TPair<KeyType, ValueType>``` ，只将键用于存储和获取
映射有两种类型：TMap 和 TMultiMap。两者之间的不同点是，TMap 中的键是唯一的，而TMultiMap可存储多个相同的键。在 TMap 中添加新的键值时，若所用的键与原有的对相同，新对将替换原有的对。在TMultiMap中，容器可以同时存储新对和原有的对
在 TMap 中，键值对被视为映射的元素类型，相当于每一对都是个体对象。在本文中，元素就意味着键值对，而各个组件就被称作元素的键或元素的值。元素类型实际上是 ```TPair<KeyType, ElementType>``` ，但很少需要直接引用 TPair 类型
和 TArray 一样，TMap 也是同质容器，就是说它所有元素的类型都应完全相同。TMap 也是值类型，支持通常的复制、赋值和析构函数运算，以及它的元素的强所有权。在映射被销毁时，它的元素都会被销毁。键和值也必须为值类型。

TMap 是散列容器，这意味着键类型必须支持 GetTypeHash 函数，并提供 运算符== 来比较各个键是否等值

TMap 也可使用任选分配器来控制内存分配行为。但不同于 TArray，这些是集合分配器，而不是 FHeapAllocator 和 TInlineAllocator 之类的标准UE4分配器。集合分配器（ TSetAllocator 类）定义映射应使用的散列桶数量，以及应使用哪个标准UE4分配器来存储散列和元素。

KeyFuncs 是最后一个 TMap 模板参数，该参数告知映射如何从元素类型获取键，如何比较两个键是否相等，以及如何对键进行散列计算。这些参数有默认值，它们只会返回对键的引用，使用 运算符== 确定相等性，并调用非成员 GetTypeHash 函数进行散列计算。如果您的键类型支持这些函数，可使用它作为映射键，不需要提供自定义 KeyFuncs

与 TArray 不同的是，内存中 TMap 元素的相对排序既不可靠也不稳定，对这些元素进行迭代很可能会使它们返回的顺序和它们添加的顺序有所不同。这些元素也不太可能在内存中连续排列。映射的支持数据结构是稀疏数组，这种数组可有效支持元素之间的空位。当元素从映射中被移除时，稀疏数组中就会出现空位。将新的元素添加到数组可填补这些空位。但是，即便 TMap 不会打乱元素来填补空位，指向映射元素的指针仍然可能失效，因为如果存储器被填满，又添加了新的元素，整个存储可能会重新分配
#### 语法
##### 创建
```
TMap<键的数据类型,值的数据类型> 映射名;
```
##### 填充
###### Add
填充映射的标准方法是调用带一个键和值的Add函数

*蓝图中有对应的Add方法*
```
FruitMap.Add(5, TEXT("Banana"));
FruitMap.Add(2, TEXT("Grapefruit"));
FruitMap.Add(7, TEXT("Pineapple"));
// FruitMap == [
//  { Key:5, Value:"Banana"     },
//  { Key:2, Value:"Grapefruit" },
//  { Key:7, Value:"Pineapple"  }
// ]
```
**此处的元素按插入顺序排列，但不保证这些元素在内存中实际保留此排序。如果是新的映射，可能会保留插入排序，但插入和删除的次数越多，新元素不出现在末尾的可能性就越大**

Add 函数可接受不带值的键。调用此重载后的 Add 时，值将被默认构建

###### Emplace
和 TArray 一样，还可使用 Emplace 代替 Add，防止插入映射时创建临时文件

Emplace会直接将键和值传递给了各自的构造函数。这对键实际上没有影响，但避免了为该值创建临时数据。与 TArray 不同的是，只能通过单一参数构造函数将元素安放到映射中

###### Append
将一个映射的所有元素移至另一个映射，如果目标映射有键和源映射相同，会被覆盖

##### 迭代
###### 方法1-----使用C++的范围（ranged-for）功能
TMaps 的迭代类似于 TArrays。可使用C++的设置范围功能，注意元素类型是 TPair


###### 方法2-----使用迭代器类型控制迭代

##### 查询
###### Num
调用 Num 函数即可查询映射中保存的元素数量
*蓝图中有对应的Length方法*

###### Contains
要确定映射是否包含特定键，可调用Contains函数
*蓝图中有对应的Contains方法*
```
bool bHas7 = FruitMap.Contains(7);
bool bHas8 = FruitMap.Contains(8);
// bHas7 == true
// bHas8 == false
```
###### 运算符[]

###### Find
如果映射包含该键，Find 将返回指向元素数值的指针。如果映射不包含该键，则返回null。在常量映射上调用 Find，返回的指针也将为常量

*蓝图中有对应的Find方法*

###### FindOrAdd
如果映射包含该键，Find 将返回指向元素数值的指针。如果映射不包含该键，将创建给定的新元素或默认构建创建新元素
因为可以修改映射，所以仅适用于非常量映射

###### FindRef
FindRef会返回与给定键关联的值副本；若映射中未找到给定键，则返回默认构建值
FindRef不会创建新元素，因此既可用于常量映射，也可用于非常量映射

###### FindKey
FindKey函数执行逆向查找，通过值查找，返回指向与所提供值配对的第一个键的指针。搜索映射中不存在的值将返回空指针

按值查找比按键查找慢（线性时间）。这是因为映射按键排序，而非按值排序。此外，如果映射有多个具有相同值的键，FindKey可返回其中任一键

###### GenerateKeyArray
使用所有键的副本来填充数组。会在填充前清空所传递的数组，因此产生的元素数量始终等于映射中的元素数量

*蓝图中有对应的Keys方法*

###### GenerateValueArray
使用所有值的副本来填充数组。会在填充前清空所传递的数组，因此产生的元素数量始终等于映射中的元素数量

*蓝图中有对应的Values方法*

##### 移除
###### Remove
提供要移除元素的键。返回值是被移除元素的数量。如果映射不包含与键匹配的元素，则返回值为0

###### FindAndRemoveChecked
用于从映射移除元素并返回其值。名称的"已检查"部分表示若键不存在，映射将调用check（UE4中等同于assert）

###### RemoveAndCopyValue
返回值是布尔类型，作用与Remove相似，不同点是会将已移除元素的值复制到引用参数。如果映射中不存在指定的键，则输出参数将保持不变，函数将返回false

###### Empty
可将映射中的所有元素移除，Empty可采用参数指示映射中保留的slack量

###### Reset
将映射中的所有元素移除,重置映射容器

##### 排序
TMap 可以进行排序。排序后，迭代映射会以排序的顺序显示元素，但下次修改映射时，排序可能会发生变化。排序是不稳定的，因此等值元素在MultiMap中可能以任何顺序出现
###### KeySort
映射使用二元谓词，按键进行排序

###### ValueSort
映射使用二元谓词，按值进行排序

##### 运算符
###### MoveTemp
把一个映射中的键值对移动到另一个映射中，在移动后，源映射必定为空



### TSet
TSet是一种快速容器类，用于在排序不重要的情况下存储唯一元素。在大多数情况下，只需要一种参数——元素类型。但是，TSet可配置各种模板参数来改变其行为，使其更全面。除了可指定从DefaultKeyFuncs的派生结构体来提供散列功能，还可允许集合中的多个键拥有相同的值。它和其它容器类一样，可设置自定义内存分配器来存储数据

和TArray一样，TSet是同质容器，其所有元素均完全为相同类型。TSet也是值类型，支持常规复制、赋值和析构函数操作，以及其元素较强的所有权。TSet被销毁时，其元素也将被销毁。键类型也必须是值类型

TSet使用散列，即如果给出了KeyFuncs模板参数，该参数会告知集合如何从某个元素确定键，如何比较两个键是否相等，如何对键进行散列，以及是否允许重复键。它们默认只返回对键的引用，使用运算符==对比相等性，使用非成员函数 GetTypeHash 进行散列。默认情况下，集合中不允许有重复的键。如果键类型支持这些函数，则可以将其用作集合键，无需提供自定义KeyFuncs。要写入自定义 KeyFuncs，可扩展 DefaultKeyFuncs 结构体

TSet可通过任选分配器控制内存分配行为。标准虚幻引擎4（UE4）分配器（如 FHeapAllocator 和 TInlineAllocator）不能用作TSet的分配器。实际上，TSet 使用集合分配器，该分配器可定义集合中使用的散列桶数量以及用于存储元素的标准UE4分配器

与TArray不同的是，内存中TSet元素的相对排序既不可靠也不稳定，对这些元素进行迭代很可能会使它们返回的顺序和它们添加的顺序有所不同。这些元素也不太可能在内存中连续排列。集合中的后台数据结构是稀疏数组，即在数组中有空位。从集合中移除元素时，稀疏数组中会出现空位。将新的元素添加到阵列可填补这些空位。但是，即便TSet不会打乱元素来填补空位，指向集元素的指针仍然可能失效，因为如果存储器被填满，又添加了新的元素，整个存储可能会重新分配
#### 语法
##### 创建集合
```
TSet<数据类型> 集合名;
```
##### 填充集合
###### Add
填充集合的标准方法是使用 Add 函数并提供键（元素）

**此处的元素按插入顺序排列，但不保证这些元素在内存中实际保留此排序。如果是新集合，可能会保留插入排序，但插入和删除的次数越多，新元素不出现在末尾的可能性越大**

###### Emplace
可以代替Add，避免插入集合时创建临时文件

**与 TArray 不同的是，只能使用单一参数构造函数将元素放到集合中**

###### Append
合并的方式插入另一个集合中的所有元素

##### 迭代
###### 方法1-----使用C++的范围（ranged-for）功能
TMaps 的迭代类似于 TArrays。可使用C++的设置范围功能
```
for (auto& Elem :FruitSet)
{
    FPlatformMisc::LocalPrint(
        *FString::Printf(
            TEXT(" \"%s\"\n"),
            *Elem
        )
    );
}
```
###### 方法2-----使用迭代器类型控制迭代

##### 查询
###### Num
调用 Num 函数可查询集合中保存的元素数量

###### Contains
查询集合是否包含指定元素，返回一个布尔值

###### Find
查询集合是否包含指定元素，返回指向元素数值的指针。如果映射不包含该键，则返回null。对常量集合调用 Find ，返回的指针也将为常量

###### Array
Array函数会把集合中所有元素复制到一个数组中，返回值是数组

##### 移除
###### Remove
Remove函数可按索引移除元素，但仅建议在通过元素迭代时使用：Remove函数会返回已删除元素的数量。如果给定的键未包含在集合中，则会返回0。如果TSet支持重复的键，Remove将移除所有匹配元素

###### Empty
可将集合中的所有元素移除，Empty可采用参数指示集合中保留的slack量

###### Reset
可将集合中的所有元素移除

##### 排序
TSet可以排序。排序后，迭代集合会以排序的顺序显示元素，但下次修改集合时，排序可能会发生变化。由于排序不稳定，可能按任何顺序显示集合中支持重复键的等效元素
###### Sort
Sort函数使用指定排序顺序的二元谓词
```
FruitSet.Sort([](const FString& A, const FString& B) {
    return A > B; // sort by reverse-alphabetical order
});
// FruitSet == [ "Pear", "Orange", "Melon", "Mango", "Kiwi", "Grapefruit" ] (order is temporarily guaranteed)

FruitSet.Sort([](const FString& A, const FString& B) {
    return A.Len() < B.Len(); // sort strings by length, shortest to longest
});
// FruitSet == [ "Pear", "Kiwi", "Melon", "Mango", "Orange", "Grapefruit" ] (order is temporarily guaranteed)
```
##### 运算符
和TArray一样，TSet是常规值类型，可通过标准复制构造函数或赋值运算符进行复制。因为集合严格拥有其元素，复制集合的操作是深层的，所以新集合将拥有其自身的元素副本


##### slack
###### Reserve
在添加元素之前预分配内存
**预先分配slack会导致以倒序添加新元素。与数组不同，集合不维护元素排序，处理集合的代码不能指望元素排序稳定或可预测**



## 游戏性类
虚幻引擎中每个游戏性类由一个类头文件（.h）和一个类源文件（.cpp）构成。类头包含类和类成员（如变量和函数）的声明，而在类源文件中通过 实现 属于类的函数来定义类的功能

虚幻引擎中的类拥有一个标准化的命名方案，通过首字母或前缀即可立即明了其为哪种类

### 基本语法
#### 前缀
##### A
从可生成的游戏性对象的基础类进行延伸。它们是Actor，可直接生成到世界场景中
##### U
从所有游戏性对象的基础类进行延伸。它们无法被实例到世界场景中，必须从属于Actor。总体而言，它们是与组件相似的对象

#### 类头
虚幻引擎中的游戏性类通常拥有单独且唯一的类头文件。通常这些文件的命名与其中定义的类相匹配，减去 A 或 U 前缀，并使用 .h 文件扩展名。因此，AActor 类的类头文件命名为 Actor.h。虽然 Epic 代码遵循这些规则，但当前引擎中类名称和源文件名之间不存在正式关系。

游戏性类的类头文件使用标准 C++ 语法，并结合专门的宏，以简化类、变量和函数的声明过程。

在每个游戏性类头文件的顶端，需要包含生成的头文件（自动创建）。因此在 ClassName.h 的顶端必须出现以下行：
```
#include "ClassName.generated.h"
```
#### 类声明
类声明定义类的名称、其继承的类，以及其继承的函数和变量。类声明还将定义通过 类说明符 和元数据要求的其他引擎和编辑器特定行为。

类声明的语法如下所示：
```
UCLASS([specifier, specifier, ...], [meta(key=value, key=value, ...)])
class ClassName : public ParentName
{
    GENERATED_BODY()
}
```
声明包含一个类的标准 C++ 类声明。在标准声明之上，描述符（如类说明符和元数据）将被传递到 UCLASS 宏。它们用于创建被声明类的 UClass，它可被看作引擎对类的专有表达。此外， ```GENERATED_BODY()`` 宏必须被放置在类体的最前方。

#### 类说明符
声明类时，可以为声明添加类说明符，以控制类相对于引擎和编辑器的各个方面的行为

###### Abstract
Abstract说明符会将类声明为"抽象基类"，阻止用户向关卡中添加此类的Actor。对于单独存在时没有意义的类，此说明符非常有用。例如，ATriggerBase基类是抽象类，而ATriggerBox子类不是抽象类，可以放置在关卡中

###### AdvancedClassDisplay
AdvancedClassDisplay说明符强制类的所有属性仅在显示这些属性的"细节（Details）"面板的 ```["高级（Advanced）"部分](building-virtual-worlds/level-editor/Details#AdvancedProperties)``` 中显示。要覆盖单个属性上的此说明符，在该属性上使用SimpleDisplay说明符

###### AutoCollapseCategories=(Category1, Category2, ...)
AutoCollapseCategories说明符使父类上的 **AutoExpandCategories** 说明符的列出类别的效果无效

###### AutoExpandCategories=(Category1, Category2, ...)
为此类的对象指定应自动在虚幻编辑器属性窗口中展开的一个或多个类别。要自动展开未使用类别声明的变量，请使用声明变量的类的名称

###### Blueprintable
将此类公开为用于创建蓝图的可接受基类。默认为 NotBlueprintable ，除非继承时就并非如此。此说明符由子类继承。

###### BlueprintType
将此类公开为可用于蓝图中的变量的类型

###### ClassGroup=GroupName
指示在虚幻编辑器的Actor浏览器中启用组视图（Group View）时，Actor浏览器应在指定的GroupName中包含此类及此类的所有子类

###### CollapseCategories
指示此类的属性不应划分到虚幻编辑器属性窗口的类别中。此说明符会传播到子类，可由DontCollapseCategories说明符覆盖

###### Config=ConfigName
指示此类可在配置文件（.ini）中存储数据。如果存在任何使用 config 或 globalconfig 说明符声明的类属性，此说明符将使这些属性存储在指定的配置文件中。此说明符会传播到所有子类并且无法使此说明符无效，但是子类可通过重新声明config说明符，并提供不同的ConfigName来更改配置文件。常见的ConfigName 值是"Engine"、"Editor"、"Input"和"Game"

###### Const
此类中的所有属性和函数都是 const 并且导出为 const 。此说明符由子类继承

###### ConversionRoot
根转换，将子类限制为仅可沿层级向上转换为第一个根类的子类

###### CustomConstructor
阻止构造函数声明自动生成

###### DefaultToInstanced
此类的所有实例都被认为是"实例化的"。实例化的类（组件）将在构造时被复制。此说明符由子类继承
```
DependsOn=(ClassName1, ClassName2, ...)
```
列出的所有类将先于此类被编译。提供的类名必须指示同一个或前一个包中的类。可以使用单个 DependsOn 行（以逗号分隔）来标识多个依赖类，或者可以通过为每个类使用单独的 DependsOn 行来指定多个依赖类。当某个类使用在另一个类中声明的结构体或枚举时，这非常重要，因为编译器仅知道它已编译了类中的哪些部分

###### Deprecated
此类已弃用，序列化时将不保存此类的对象。此说明符由子类继承

###### DontAutoCollapseCategories=(Category, Category, ...)
使列出的类别的继承自父类的AutoCollapseCategories说明符无效

###### DontCollapseCategories
使继承自基类的 CollapseCatogories 说明符无效。

###### EditInlineNew
指示可以从虚幻编辑器"属性（Property）"窗口创建此类的对象，而非从现有资源引用。默认行为是仅可通过"属性（Property）"窗口指定对现有对象的引用。此说明符会传播到所有子类；子类可通过 NotEditInlineNew 说明符覆盖它

###### HideCategories=(Category1, Category2, ...)
列出一个或多个应该对用户完全隐藏的分类。要隐藏未使用类别声明的属性，请使用声明变量的类的名称。此说明符会传播到子类

###### HideDropdown
阻止此类在属性窗口组合框中显示

###### HideFunctions=(Category1, Category2, ...)
让指定分类中的所有函数都对用户完全隐藏

###### HideFunctions=FunctionName
将提到的函数对用户完全隐藏

###### Intrinsic
指示此类直接在C++中声明，无Unreal Header Tool生成的样板。不要在新类上使用此说明符

###### MinimalAPI
导致仅导出此类的类型信息，以供其他模块使用。可以以此类为目标进行强制转换，但此类的函数无法被调用（除了使用内联方法）。这可以缩短编译时间，因为没有针对无需从其他模块访问其所有函数的类导出一切

###### NoExport
指示此类的声明不应包含在由标头生成器自动生成的C++头文件中。必须在单独的头文件中手动定义该C++类声明。仅对本地类有效。不要对新类使用此说明符

###### NonTransient
使继承自基类的Transient说明符无效

###### NotBlueprintable
指定此类不是可用于创建蓝图的可接受基类。此为默认说明符，将由子类继承

###### NotPlaceable
使继承自基类的Placeable说明符无效。指示不可以在编辑器中将此类的对象放置到关卡、UI场景或蓝图中

###### PerObjectConfig
此类的配置信息将按对象存储，在.ini文件中，每个对象都有一个分段，根据对象命名，格式为[ObjectName ClassName] 。此说明符会传播到子类

###### Placeable
指示可在编辑器中创建此类，而且可将此类放置到关卡、UI场景或蓝图（取决于类类型）中。此标志会传播到所有子类；子类可使用NotPlaceable说明符覆盖此标志

###### ShowCategories=(Category1, Category2, ...)
使列出的类别的继承自基类的HideCategories说明符无效

###### ShowFunctions=(Category1, Category2, ...)
在属性查看器中显示列出的类别中的所有函数

###### ShowFunctions=FunctionName
在属性查看器中显示指定的函数

###### Transient
从不将属于此类的对象保存到磁盘。当与播放器或窗口等本质上不持久的特定种类的原生类配合使用时，它非常有用。此说明符会传播到子类，但是可由NonTransient说明符覆盖

###### Within=OuterClassName
此类的对象无法在 OuterClassName 对象的实例之外存在。这意味着，要创建此类的对象，需要提供OuterClassName的一个实例作为其Outer对象。

#### 元数据说明符
声明类、接口、结构体、列举、列举值、函数或属性时，可添加元数据说明符来控制其与引擎和编辑器各方面的相处方式。每一种类型的数据结构或成员都有自己的元数据说明符列表
###### BlueprintSpawnableComponent
如其存在，组件类可由蓝图生成

###### BlueprintThreadSafe
只在蓝图函数库上有效。此说明符将把此类中的函数在动画蓝图中的非游戏线程上标记为可调用

###### ChildCannotTick
用于Actor和组件类。如果本地类无法tick，那么基于此Actor或组件的蓝图生成类则无法tick，即使bCanBlueprintsTickByDefault为true也同样如此

###### ChildCanTick
用于Actor和组件类。如果本地类无法tick，那么可以覆盖基于此Actor或组件的蓝图生成类的 bCanEverTick 标签，即使 bCanBlueprintsTickByDefault 为false也同样如此。

###### DeprecatedNode
用于行为树节点，说明类已废弃，编译时将显示一条警告。

###### DeprecationMessage="Message Text"
如果类已废弃，尝试编译使用此类的蓝图时，其将被添加到标准废弃警告。

###### DisplayName="Blueprint Node Name"
此节点在蓝图中的命名将被此处提供的值所取代，而非代码生成的命名。

###### DontUseGenericSpawnObject
不使用蓝图中的Generic Create Object节点来生成类的一个对象。此说明符只有在用于既非Actor又非ActorComponent的BluprintType类时才有意义。

###### ExposedAsyncProxy
在 Async Task 节点中公开此类的一个代理对象

###### IgnoreCategoryKeywordsInSubclasses
用于让一个类的首个子类忽略所有继承的 ShowCategories 和 HideCategories 说明符

###### IsBlueprintBase="true/false"
说明此类是否为创建蓝图的一个可接受基类，与 UCLASS 说明符、Blueprintable 或 NotBlueprintable 相似

###### KismetHideOverrides="Event1, Event2, .."
不允许被覆盖的蓝图事件的列表

###### ProhibitedInterfaces="Interface1, Interface2, .."
列出与类不兼容的接口

###### RestrictedToClasses="Class1, Class2, .."
由蓝图函数库类使用，用于限制列表中命名类的用法

###### ShortToolTip="Short tooltip"
完整提示文本过长时使用的简短提示文本，例如父类选取器对话

###### ShowWorldContextPin
说明放置在此类拥有的图表中的蓝图节点必须显式其World情景引脚（即使其通常状态下为隐藏也同样如此），因为此类的对象无法被用作World情景

###### UsesHierarchy
说明类使用层级数据。用于实例化"细节"面板中的层级编辑功能

###### ToolTip="Hand-written tooltip"
覆盖从代码注释自动生成的提示文本

#### 类实现
所有的游戏性类必须使用 GENERATED_BODY 宏进行正常实现。该执行在定义类和其所有变量和函数的类头（.h）文件中完成。最佳方法是使类源和头文件的命名与实现的类相匹配，减去 A 或 U 前缀。因此，AActor 类的源文件命名为 Actor.cpp，其头文件命名为 Actor.h。对编辑器中"Add C++ Class"菜单选项创建的类而言，此操作将自动进行

源文件（.cpp）必须囊括包含 C++ 类声明的头文件（.h），C++ 类声明通常为自动生成，但也可手动生成（如有必要）。例如，AActor 类的 C++ 声明在 EngineClasses.h 头文件中自动生成。这意味着 Actor.cpp 文件必须包括 EngineClasses.h 文件或轮流包含的另一个文件。总体而言只包含游戏项目的头文件，其中包含了游戏项目中游戏性类的标头。以 AActor 和 EngineClasses.h 为例，其中包含了 EnginePrivate.h 标头，此标头则包含了 Engine.h - Engine 项目的头文件 - 而该头文件又包含 EngineClasses.h 头文件

如在类函数实现中引用其他类（包含一个该文件未将类函数包括在内），则可能还需要包含额外的文件

#### 类构造函数
UObjects 使用 Constructors 设置属性和其他变量的默认值，并执行其他必要的初值设定。类构造函数通常放置在类实现文件中，如 AActor::AActor 构造函数位于 Actor.cpp 中

**部分构造函数可能以每个模块为基础放置在一个特殊的"constructors"文件中。例如 AActor::AActor 构造函数可能存在于 EngineConstructors.cpp 中。这是自动转换过程的结果，从之前 DEFAULTS 块的使用到构造函数的使用。它们将随时间被移至其相应的类源文件**

##### 构造函数格式
UObject构建函数最基本的形式如下所示：
```
UMyObject::UMyObject()
{
    // 在此处初始化 Class Default Object 属性
}
```
该构造函数初始化类默认对象（CDO），CDO是类的新实例所基于的原版。此外还有一个次要构造函数，支持一个特殊的属性调整结构：
```
UMyObject::UMyObject(const FObjectInitializer& ObjectInitializer)
:Super(ObjectInitializer)
{
    // 在此处初始化 CDO 属性
}
```
虽然以上构造函数实际上并不执行任何初始化，但引擎已将所有字段初始化为零、NULL，或其默认构造函数实现的任意值。然而，写入构建函数的任意初始化代码将被应用至 CDO，因此将被复制到引擎中正确创建的对象新实例上，正如CreateNewObject 或 SpawnActor

被传入构造函数的 FObjectInitializer 参数除被标记为常数外，还可通过嵌入可变函数进行配置，以覆写属性和子对象。被创建的 UObject 将 受到这些变更的影响，这可用于变更注册属性或组件的数值
```
AUDKEmitterPool::AUDKEmitterPool(const FObjectInitializer& ObjectInitializer)
:Super(ObjectInitializer.DoNotCreateDefaultSubobject(TEXT("SomeComponent")).DoNotCreateDefaultSubobject(TEXT("SomeOtherComponent")))
{
    // 在此处初始化 CDO 属性
}
```
在上例中，超类将在其构建函数中创建名为"SomeComponent"和"SomeOtherComponent"的子对象，但由于 FObjectInitializer 的原因，该操作将不会执行


##### 构建函数静态属性和助手
为更复杂的数据类型设置数值（尤其是类引用、命名和资源引用）时，需要在构造函数中定义并实例化一个ConstructorStatics结构体，以保存所需的诸多属性数值。ConstructorStatics 结构体在构造函数首次运行时才会被创建。在随后的运行上它只会复制一个指针，使其处理速度极快。ConstructorStatics 被创建时，数值将被指定到结构体成员，以便稍后在构建函数上指定数值到实际属性时进行访问。

ContructorHelpers 是 ObjectBase.h 中定义的特殊命名空间。ObjectBase.h 包含用于执行构建函数特定常规操作的助手模板。例如为资源或类寻找引用、以及创建并寻找组件的助手模板


#### 资源引用
理想状态下，类中的资源引用并不存在。硬编码资源引用很脆弱，优选方法是使用蓝图配置资源属性。然而，仍然完全支持硬编码引用。不需要在每次构造对象时搜索资源，因此这些搜索只执行一次。一个静态结构体可确保只执行一次资源搜索

```ConstructorHelpers::FObjectFinder``` 通过 StaticLoadObject 为特定的 UObject 寻找引用。它常用于引用存储在内容包中的资源。如未找到对象， 则报告失败


#### 类引用
ConstructorHelpers::FClassFinder 为特定的 UClass 寻找引用。如类未找到，则报告失败
```
APylon::APylon(const class FObjectInitializer& ObjectInitializer)
:Super(ObjectInitializer)
{
    // 进行一次性初始化的结构
    static FClassFinder<UNavigationMeshBase> ClassFinder(TEXT("class'Engine.NavigationMeshBase'"));
    if (ClassFinder.Succeeded())
    {
        NavMeshClass = ClassFinder.Class;
    }
    else
    {
        NavMeshClass = nullptr;
    }
}
```
在许多情况下，可只使用 USomeClass::StaticClass()，绕开复杂的全部 ClassFinder。例如，在多数情况下均可使用以下方法：
```
NavMeshClass = UNavigationMeshBase::StaticClass();
```
对跨模块的引用而言，使用 ClassFinder 法较好

#### 组件和子对象
在构造函数中还可创建组件子对象并将其附着到 actor 的层级。生成一个 actor 时，将从 CDO 复制其组件。为确保组件固定被创建、被销毁和被正确地垃圾回收，构建函数中创建的每个组件的指针应被存储在拥有类的一个 UPROPERTY 中

通常没有必要对属于父类的组件进行修改。然而，在任何 USceneComponent（包括根组件）上调用 GetAttachParent、GetParentComponents、GetNumChildrenComponents、GetChildrenComponents 和 GetChildComponent 即可获得当前所有附着组件（包括父类创建的组件）的列表


## UFunction/函数
### 基本语法
#### 声明
UFunction是UE4反射系统可识别的C++函数。UObject或蓝图函数库可将成员函数声明为UFunction，方法是将UFUNCTION宏放在头文件中函数声明上方的行中。宏将支持函数说明符更改UE4解译和使用函数的方式

可利用函数说明符将UFunction对蓝图可视化脚本图表公开，以便开发者从蓝图资源调用或扩展UFunction，而无需更改C++代码
在类的默认属性中，UFunction可绑定到```[委托](programming-and-scripting/programming-language-implementation/delegates-and-lamba-functions-in-unreal-engine)```，从而能够执行一些操作（例如将操作与用户输入相关联）。它们还可以充当网络回调，这意味着当某个变量受网络更新影响时，用户可以将其用于接收通知并运行自定义代码。用户甚至可创建自己的控制台命令（通常也称 debug、configuration 或 cheat code 命令），并能在开发版本中从游戏控制台调用这些命令，或将拥有自定义功能的按钮添加到关卡编辑器中的游戏对象

#### 函数说明符
声明函数时，可以为声明添加 函数说明符，以控制函数相对于引擎和编辑器的各个方面的行为方式
###### BlueprintAuthorityOnly
如果在具有网络权限的机器上运行（服务器、专用服务器或单人游戏），此函数将仅从蓝图代码执行

###### BlueprintCallable
此函数可在蓝图或关卡蓝图图表中执行
函数以C++编写，可从蓝图图表中调用，但只能通过编辑C++代码进行修改或重写。以此类方式标记的函数通常具备供非程序员使用而编写的功能，但是不应对其进行修改，否则修改将毫无意义。数学函数便是此类函数的经典范例

###### BlueprintCosmetic
此函数为修饰性的，无法在专用服务器上运行

###### BlueprintImplementableEvent
此函数在蓝图或关卡蓝图图表中实现，而不是在C++中给出函数实现，但是在C++中可以调用
在C++ header(.h)文件中设置BlueprintImplementableEvent函数，但是函数的主体则在蓝图图表中完成编写，而非C++中。创建此类通常是为了使非程序员能够对无预期默认动作或标准行为的特殊情况创建自定义反应。在宇宙飞船游戏中，玩家飞船接触到能量升级时发生的事件便是这方面的范例

###### BlueprintNativeEvent
此函数旨在被蓝图覆盖掉，但是也具有默认原生实现。用于声明名称与主函数相同的附加函数，但是末尾添加了Implementation，是写入代码的位置。如果未找到任何蓝图覆盖，该自动生成的代码将调用Implementation方法。
BlueprintNativeEvent 函数与 BlueprintCallable 和 BlueprintImplementableEvent 函数的组合类似。其具备用C++中编程的默认行为，但此类行为可通过在蓝图图表中覆盖进行补充或替换。对此类代码编程时，C++代码固定使用命名末尾添加了_Implementation的虚函数。此为最为灵活的选项

操作方法：
1. 在UFUNCTION()中添加BlueprintNativeEvent说明符
2. 在函数声明的下方添加虚函数的声明
```
	UFUNCTION(BlueprintNativeEvent)
	返回类型 函数名();
	virtual 返回类型 函数名_Implementation();
```
3.把.cpp文件的函数实现改为
```
	返回类型 类名::函数名_Implementation()
	{
		函数实现;
	}
```

*如果在蓝图中写逻辑，默认覆盖C++中的函数逻辑，如果需要同时执行C++和蓝图中的逻辑，在蓝图对应的函数事件调用上右键选择Add Call to Parent Function*


###### BlueprintPure
此函数不对拥有它的对象产生任何影响，可在蓝图或关卡蓝图图表中执行

###### CallInEditor
可通过细节（Details）面板中的按钮在编辑器中的选定实例上调用此函数

###### Category = "TopCategory|SubCategory|Etc"
在蓝图编辑工具中显示时指定函数的类别。使用 | 运算符定义嵌套类别。

###### Client
此函数仅在拥有在其上调用此函数的对象的客户端上执行。用于声明名称与主函数相同的附加函数，但是末尾添加了Implementation。必要时，此自动生成的代码将调用Implementation方法

###### CustomThunk
UnrealHeaderTool代码生成器将不为此函数生成thunk，用户需要自己通过DECLARE_FUNCTION或DEFINE_FUNCTION宏来提供thunk

###### Exec
此函数可从游戏内控制台执行。仅在特定类中声明时，Exec命令才有效

###### NetMulticast
此函数将在服务器上本地执行，也将复制到所有客户端上，无论该Actor的NetOwner为何

###### Reliable
此函数将通过网络复制，并且一定会到达，即使出现带宽或网络错误。仅在与Client或Server配合使用时才有效

###### SealedEvent
无法在子类中覆盖此函数。SealedEvent关键词只能用于事件。对于非事件函数，要将它们声明为static或final，以密封它们

###### ServiceRequest
此函数为RPC（远程过程调用）服务请求。这意味着NetMulticast和Reliable

###### ServiceResponse
此函数为RPC服务响应。这意味着NetMulticast和Reliable。

###### Server
此函数仅在服务器上执行。用于声明名称与主函数相同的附加函数，但是末尾添加了_Implementation，是写入代码的位置。必要时，此自动生成的代码将调用 _Implementation 方法

###### Unreliable
此函数将通过网络复制，但是可能会因带宽限制或网络错误而失败。仅在与Client或Server配合使用时才有效

###### WithValidation
用于声明名称与主函数相同的附加函数，但是末尾需要添加_Validate。此函数使用相同的参数，但是会返回bool，以指示是否应继续调用主函数

#### 元数据说明符
声明类、接口、结构体、列举、列举值、函数或属性时，可添加元数据说明符来控制其与引擎和编辑器各方面的相处方式。每一种类型的数据结构或成员都有自己的元数据说明符列表
###### AdvancedDisplay="Parameter1, Parameter2, .."
以逗号分隔的参数列表将显示为高级引脚（需要UI扩展）

###### AdvancedDisplay=N
用一个数字替代N ，第N之后的所有参数将显示为高级引脚（需要UI扩展）。举例而言：'AdvancedDisplay=2' 将把前两个之外的所有参数标记为高级

###### ArrayParm="Parameter1, Parameter2, .."
说明BlueprintCallable函数应使用一个Call Array Function节点，且列出的参数应被视为通配符数组属性

###### ArrayTypeDependentParams="Parameter"
使用 ArrayParm 时，此说明符将指定一个参数，其将确定 ArrayParm 列表中所有参数的类型

###### AutoCreateRefTerm="Parameter1, Parameter2, .."
如列出参数（由引用传递）的引脚未连接，其将拥有一个自动创建的默认项。这是蓝图的一个便利功能，经常在数组引脚上使用

###### BlueprintAutocast
仅能由来自蓝图函数库的静态BlueprintPure函数使用。Cast节点将根据返回类型和函数首个参数的类型来自动添加

###### BlueprintInternalUseOnly
此函数是一个内部实现细节，用于实现另一个函数或节点。其从未直接在蓝图图表中公开

###### BlueprintProtected
此函数只能在蓝图中的拥有对象上调用。其无法在另一个实例上调用

###### CallableWithoutWorldContext
用于拥有一个 WorldContext 引脚的 BlueprintCallable 函数，说明函数可被调用，即使其类不实现 GetWorld 函数也同样如此

###### CommutativeAssociativeBinaryOperator
说明 BlueprintCallable 函数应使用Commutative Associative Binary节点。此节点缺少引脚命名，但拥有一个创建额外输入引脚的 添加引脚（Add Pin） 按钮

###### CompactNodeTitle="Name"
说明BlueprintCallable函数应在压缩显示模式中显示，并提供在该模式中显示的命名

###### CustomStructureParam="Parameter1, Parameter2, .."
列出的参数都会被视为通配符。此说明符需要 UFUNCTION-level specifier、CustomThunk，而它们又需要用户提供自定义的 exec 函数。在此函数中，可对参数类型进行检查，可基于这些参数类型执行合适的函数调用。永不应调用基础 UFUNCTION，出现错误时应进行断言或记录

**要声明自定义 exec 函数，使用语法 DECLARE_FUNCTION(execMyFunctionName)，MyFunctionName 为原函数命名

###### DefaultToSelf
用于 BlueprintCallable 函数，说明对象属性的命名默认值应为节点的自我情境

###### DeprecatedFunction
蓝图对此函数进行引用时将引起编译警告，告知用户函数已废弃。可使用 DeprecationMessage 元数据说明符添加到废弃警告消息（如提供说明如何替代已废弃的函数）。

###### DeprecationMessage="Message Text"
如果函数已废弃，尝试编译使用此函数的蓝图时，其将被添加到标准废弃警告

###### DevelopmentOnly
被标记为 DevelopmentOnly 的函数只会在Development模式中运行。这适用于调试输出之类的功能（但其不应存在于发布产品中）

###### DisplayName="Blueprint Node Name"
此节点在蓝图中的命名将被此处提供的值所取代，而非代码生成的命名

###### ExpandEnumAsExecs="Parameter"
用于 BlueprintCallable 函数，说明应为参数使用的 列举 中的每个条目创建一个输入执行引脚。命名参数必须是引擎通过 UENUM 标签识别的一个列举类型

###### HidePin="Parameter"
用于 BlueprintCallable 函数，说明参数引脚应从用户视图中隐藏。注意：使用此方式每个函数只能隐藏一个参数引脚

###### HideSelfPin
隐藏用于指出函数调用所处对象的self引脚。self引脚在与调用蓝图的类兼容的 BlueprintPure 函数上为自动隐藏状态。这通常与 DefaultToSelf 说明符共用

###### InternalUseParam="Parameter"
与 HidePin 相似，这将在用户视图中隐藏命名参数的引脚，只能用于一个函数的一个参数

###### KeyWords="Set Of Keywords"
指定在搜索此函数时可使用的一套关键词，例如合适放置节点在蓝图图表中调用函数

###### Latent
说明一个延迟操作。延迟操作拥有类型为 FLatentActionInfo 的一个参数，此参数由 LatentInfo 说明符命名

###### LatentInfo="Parameter"
用于延迟 BlueprintCallable 函数，说明哪个参数是LatentInfo参数

###### MaterialParameterCollectionFunction
用于 BlueprintCallable 函数，说明应使用材质覆盖节点

###### NativeBreakFunc
用于 BlueprintCallable 函数，说明函数应以标准Break Struct节点的方式进行显示

###### NotBlueprintThreadSafe
只在蓝图函数库中有效。此函数将被视为拥有类的整体 BlueprintThreadSafe 元数据的一个例外

###### ShortToolTip="Short tooltip"
完整提示文本过长时使用的简短提示文本，例如父类选取器对话

###### ToolTip="Hand-written tooltip
覆盖从代码注释自动生成的提示文本

###### UnsafeDuringActorConstruction
在Actor构造时调用此函数并非安全操作

###### WorldContext="Parameter"
由 BlueprintCallable 函数使用，说明哪个参数决定运算正在发生的World


#### 函数参数说明符
###### Out
声明由引用传递的参数，使函数对其进行修改

###### Optional
通过任选关键词可使部分函数参数变为任选，便于调用。任选参数的数值（调用方未指定）取决于函数。例如，SpawnActor 函数使用任选位置和旋转，默认为生成的 Actor 根组件的位置和旋转。添加 ```= [value]``` 参数可指定任选参数的默认值。例如：```function myFunc(optional int x = -1)``` 。在多数情况下，如无数值被传递到任选参数，将使用变量类型的默认值或零（例如 0、false、""、none）


## 游戏模块
正如引擎本身由一组模块构成一样，每个游戏也是由一个或多个游戏性模块构成的。这些模块类似于引擎以前的版本中的包的概念，它们都是一组相关类的容器。在虚幻引擎 4 中，由于游戏逻辑都可以通过 C++ 实现，所以模块实际上是 DLL 文件，而不再是包文件。（这里的"包文件"是指 UE3 中的 Package，Gameplay 相关的内容通常会被定义在 MyGame 的目录中，其中具有代码和脚本的实现，最终打包形成 MyGame.u 的形式。而 UE4 不再使用 .u 这类 Package 文件，而是使用更常规的模块化 DLL 文件。）

#### 模块创建
游戏模块至少要包含一个头文件 (.h)、一个 C++ 文件 (.cpp) 和一个编译文件 (*.Build.cs)
头文件必须位于模块目录的 Public 文件夹中，也就是 ```[GameName] \Source\ [ModuleName]\Public``` 目录。该文件包含了编译该模块中的类所需的所有头文件 - 包括模块自动生成的头文件
C++ 文件必须位于模块目录的 Private 文件夹中，也就是 ```[GameName]\Source[ModuleName]\Private``` 目录，用于注册及实现模块
IMPLEMENT_PRIMARY_GAME_MODULE 注册一个模块。其他模块可以使用另一个可选的 IMPLEMENT_GAME_MODULE 方法进行注册



## 元数据说明符
声明类、接口、结构体、列举、列举值、函数，或属性时，可添加 元数据说明符 来控制其与引擎和编辑器各方面的相处方式。每一种类型的数据结构或成员都有自己的元数据说明符列表

要添加元数据说明符，需使用单词 meta，后接说明符列表。如有必要，可以将它们的值添加到 UCLASS、UENUM、UINTERFACE、USTRUCT、UFUNCTION 或 UPROPERTY 宏
### 类元数据说明符
###### BlueprintSpawnableComponent
如其存在，组件类可由蓝图生成

###### BlueprintThreadSafe
只在蓝图函数库上有效。此说明符将把此类中的函数在动画蓝图中的非游戏线程上标记为可调用

###### ChildCannotTick
用于Actor和组件类。如果本地类无法tick，那么基于此Actor或组件的蓝图生成类则无法tick，即使bCanBlueprintsTickByDefault为true也同样如此

###### ChildCanTick
用于Actor和组件类。如果本地类无法tick，那么可以覆盖基于此Actor或组件的蓝图生成类的bCanEverTick标签，即使 bCanBlueprintsTickByDefault为false也同样如此

###### DeprecatedNode
用于行为树节点，说明类已废弃，编译时将显示一条警告

###### DeprecationMessage="Message Text"
如果类已废弃，尝试编译使用此类的蓝图时，其将被添加到标准废弃警告

###### DisplayName="Blueprint Node Name"
此节点在蓝图中的命名将被此处提供的值所取代，而非代码生成的命名

###### DontUseGenericSpawnObject
不使用蓝图中的Generic Create Object节点来生成类的一个对象。此说明符只有在用于既非Actor又非ActorComponent的BluprintType类时才有意义

###### ExposedAsyncProxy
在 Async Task 节点中公开此类的一个代理对象

###### IgnoreCategoryKeywordsInSubclasses
用于让一个类的首个子类忽略所有继承的 ShowCategories 和 HideCategories 说明符

###### IsBlueprintBase="true/false"
说明此类是否为创建蓝图的一个可接受基类，与 UCLASS 说明符、Blueprintable或NotBlueprintable相似

###### KismetHideOverrides="Event1, Event2, .."
不允许被覆盖的蓝图事件的列表

###### ProhibitedInterfaces="Interface1, Interface2, .."
列出与类不兼容的接口

###### RestrictedToClasses="Class1, Class2, .."
由蓝图函数库类使用，用于限制列表中命名类的用法

###### ShortToolTip="Short tooltip"
完整提示文本过长时使用的简短提示文本，例如父类选取器对话

###### ShowWorldContextPin
说明放置在此类拥有的图表中的蓝图节点必须显式其World情景引脚（即使其通常状态下为隐藏也同样如此），因为此类的对象无法被用作World情景

###### UsesHierarchy
说明类使用层级数据。用于实例化"细节"面板中的层级编辑功能

###### ToolTip="Hand-written tooltip"
覆盖从代码注释自动生成的提示文本

### 枚举元数据说明符
###### Bitflags/位标记
表示整数UPROPERTY变量（使用"位掩码"元数据说明符设置）可将此列举用作标记

###### Experimental/实验性
将此类型标记为试验性和不支持

###### ScriptName="Display Name"
将在编辑器中使用引证字符串作为此列举的命名，而非使用虚幻标头工具生成的默认命名

###### ToolTip="Hand-written tooltip"
覆盖在代码注释中自动生成的提示文本

### 枚举值UMeta元数据说明符
枚举中的各值含有元数据说明符。此类元数据说明符与其他元数据说明符稍有不同，其使用顶层关键字UMETA，且在修改的值之后（而非之前）进行指定
###### DisplayName="Enumerated Value Name"
此处提供的文本将使用该值命名，而非代码生成的命名

###### Hidden
在编辑器中不显示该值

###### ToolTip="Hand-written tooltip."
覆盖在代码注释中自动生成的提示文本

### 接口元数据说明符
###### CannotImplementInterfaceInBlueprint
除了仅限内部的函数，此接口可能不包含BlueprintImplementableEvent或BlueprintNativeEvent函数。如果其包含蓝图可调用函数（但不是在蓝图中定义），函数必须在原生代码中实现

### 结构体元数据说明符
###### HasNativeBreak="Module.Class.Function"
说明此结构体拥有一个自定义Break Struct节点。必须提供模块、类和函数命名

###### HasNativeMake="Module.Class.Function"
说明此结构体拥有一个自定义Break Struct节点。必须提供模块、类和函数命名

###### HiddenByDefault
Make Struct和Break Struct节点中的引脚默认为隐藏状态

###### ShortToolTip="Short tooltip"
完整提示文本过长时使用的简短提示文本，例如父类选取器对话

###### ToolTip="Hand-written tooltip"
覆盖从代码注释自动生成的提示文本

### 函数元数据说明符
###### AdvancedDisplay="Parameter1, Parameter2, .."
以逗号分隔的参数列表将显示为高级引脚（需要UI扩展）

###### AdvancedDisplay=N
用一个数字替代 N ，第N之后的所有参数将显示为高级引脚（需要UI扩展）。举例而言：'AdvancedDisplay=2' 将把前两个之外的所有参数标记为高级

###### ArrayParm="Parameter1, Parameter2, .."
说明 BlueprintCallable 函数应使用一个Call Array Function节点，且列出的参数应被视为通配符数组属性

###### ArrayTypeDependentParams="Parameter"
使用 ArrayParm 时，此说明符将指定一个参数，其将确定 ArrayParm 列表中所有参数的类型

###### AutoCreateRefTerm="Parameter1, Parameter2, .."
如列出参数（由引用传递）的引脚未连接，其将拥有一个自动创建的默认项。这是蓝图的一个便利功能，经常在数组引脚上使用

###### BlueprintAutocast
仅能由来自蓝图函数库的静态 BlueprintPure 函数使用。Cast节点将根据返回类型和函数首个参数的类型来自动添加

###### BlueprintInternalUseOnly
此函数是一个内部实现细节，用于实现另一个函数或节点。其从未直接在蓝图图表中公开

###### BlueprintProtected
此函数只能在蓝图中的拥有对象上调用。其无法在另一个实例上调用

###### CallableWithoutWorldContext
用于拥有一个 WorldContext 引脚的 BlueprintCallable 函数，说明函数可被调用，即使其类不实现 GetWorld 函数也同样如此

###### CommutativeAssociativeBinaryOperator
说明 BlueprintCallable 函数应使用Commutative Associative Binary节点。此节点缺少引脚命名，但拥有一个创建额外输入引脚的 添加引脚（Add Pin） 按钮

###### CompactNodeTitle="Name"
说明 BlueprintCallable 函数应在压缩显示模式中显示，并提供在该模式中显示的命名

###### CustomStructureParam="Parameter1, Parameter2, .."
列出的参数都会被视为通配符。此说明符需要 UFUNCTION-level specifier、CustomThunk，而它们又需要用户提供自定义的 exec 函数。在此函数中，可对参数类型进行检查，可基于这些参数类型执行合适的函数调用。永不应调用基础 UFUNCTION，出现错误时应进行断言或记录
**要声明自定义 exec 函数，使用语法 DECLARE_FUNCTION(execMyFunctionName)，MyFunctionName 为原函数命名

###### DefaultToSelf
用于 BlueprintCallable 函数，说明对象属性的命名默认值应为节点的自我情境

###### DeprecatedFunction
蓝图对此函数进行引用时将引起编译警告，告知用户函数已废弃。可使用 DeprecationMessage 元数据说明符添加到废弃警告消息（如提供说明如何替代已废弃的函数）

###### DeprecationMessage="Message Text"
如果函数已废弃，尝试编译使用此函数的蓝图时，其将被添加到标准废弃警告

###### DevelopmentOnly
被标记为 DevelopmentOnly 的函数只会在Development模式中运行。这适用于调试输出之类的功能（但其不应存在于发布产品中）

###### DisplayName="Blueprint Node Name"
此节点在蓝图中的命名将被此处提供的值所取代，而非代码生成的命名

###### ExpandEnumAsExecs="Parameter"
用于 BlueprintCallable 函数，说明应为参数使用的 列举 中的每个条目创建一个输入执行引脚。命名参数必须是引擎通过 UENUM 标签识别的一个列举类型

###### HidePin="Parameter"
用于 BlueprintCallable 函数，说明参数引脚应从用户视图中隐藏。注意：使用此方式每个函数只能隐藏一个参数引脚

###### HideSelfPin
隐藏用于指出函数调用所处对象的self引脚。self引脚在与调用蓝图的类兼容的 BlueprintPure 函数上为自动隐藏状态。这通常与 DefaultToSelf 说明符共用

###### InternalUseParam="Parameter"
与 HidePin 相似，这将在用户视图中隐藏命名参数的引脚，只能用于一个函数的一个参数

###### KeyWords="Set Of Keywords"
指定在搜索此函数时可使用的一套关键词，例如合适放置节点在蓝图图表中调用函数

###### Latent
说明一个延迟操作。延迟操作拥有类型为 FLatentActionInfo 的一个参数，此参数由 LatentInfo 说明符命名

###### LatentInfo="Parameter"
用于延迟 BlueprintCallable 函数，说明哪个参数是LatentInfo参数

###### MaterialParameterCollectionFunction
用于 BlueprintCallable 函数，说明应使用材质覆盖节点

###### NativeBreakFunc
用于 BlueprintCallable 函数，说明函数应以标准Break Struct节点的方式进行显示

###### NotBlueprintThreadSafe
只在蓝图函数库中有效。此函数将被视为拥有类的整体 BlueprintThreadSafe 元数据的一个例外

###### ShortToolTip="Short tooltip"
完整提示文本过长时使用的简短提示文本，例如父类选取器对话

###### ToolTip="Hand-written tooltip
覆盖从代码注释自动生成的提示文本

###### UnsafeDuringActorConstruction
在Actor构造时调用此函数并非安全操作

###### WorldContext="Parameter"
由 BlueprintCallable 函数使用，说明哪个参数决定运算正在发生的World

### 属性元数据说明符
###### AllowAbstract="true/false"
用于 Subclass 和 SoftClass 属性。说明抽象类属性是否应显示在类选取器中

###### AllowedClasses="Class1, Class2, .."
用于 FSoftObjectPath 属性。逗号分隔的列表，表明要显示在资源选取器中的资源类类型

###### AllowPreserveRatio
用于 Fvector 属性。在细节面板中显示此属性时将添加一个比率锁

###### ArrayClamp="ArrayProperty"
用于整数属性。将可在UI中输入的有效值锁定在0和命名数组属性的长度之间

###### AssetBundles
用于 SoftObjectPtr 或 SoftObjectPath 属性。主数据资源中使用的束列表命名，指定此引用属于哪个束的一部分

###### BlueprintBaseOnly
用于 Subclass 和 SoftClass 属性。说明蓝图类是否应显示在类选取器中

###### BlueprintCompilerGeneratedDefaults
属性默认项由蓝图编译器生成，CopyPropertiesForUnrelatedObjects 在编译后调用时将不会被复制

###### ClampMin="N"
用于浮点和整数属性。指定可在属性中输入的最小值 N

###### ClampMax="N"
用于浮点和整数属性。指定可在属性中输入的最大值 N

###### ConfigHierarchyEditable
此属性被序列化为一个配置（.ini）文件，可在配置层级中的任意处进行设置

###### ContentDir
由 FDirectoryPath 属性使用。说明将使用 Content 文件夹中的Slate风格目录选取器来选取路径

###### DisplayAfter="PropertyName"
在蓝图编辑器中，名为 PropertyName 的属性后即刻显示此属性。前提是两个属性属于同一类别，则忽略其在源代码中的顺序进行显示。如多个属性有相同的 DisplayAfter 值和相同的 DisplayPriority 值，将在指定属性之后，按照自身在标头文件中声明的顺序显示

###### DisplayName="Property Name"
此属性显示的命名，不显示代码生成的命名

###### DisplayPriority="N"
如两个属性有相同的 DisplayAfter 值，或属于同一类别且无 DisplayAfter 元标签，则此属性将决定其顺序。最高优先级值为1，表示 DisplayPriority 值为1的属性将在 DisplayProirity 值为2的属性之上显示。如多个属性有相同的 DisplayAfter 值，其将按照在标头文件中声明的顺序显示

###### DisplayThumbnail="true"
说明属性是一个资源类型，其应显示选中资源的缩略图

###### EditCondition="BooleanPropertyName"
对一个布尔属性进行命名，此属性用于说明此属性的编辑是否被禁用。将"!"放置在属性命名前可颠倒测试

###### EditFixedOrder
使排列的元素无法通过拖拽来重新排序
**EditCondition元标签不再仅限于单个布尔属性。它现在由完全成熟的算式解析器计算，意味着可以包含一个完整的C++表达式

###### ExactClass="true"
结合 AllowedClasses 用于 FSoftObjectPath 属性。说明是否只能使用 AllowedClasses 中指定的准确类，或子类是否同样有效

###### ExposeFunctionCategories="Category1, Category2, .."
在蓝图编辑器中编译一个函数列表时，指定其函数应被公开的类目的列表

###### ExposeOnSpawn="true"
指定此属性是否应在此类类型的一个Spawn Actor节点上公开

###### FilePathFilter="FileType"
由 FFilePath 属性使用。说明在文件选取器中显示的路径过滤器。常规值包括"uasset"和"umap"，但这些并非唯一可能的值

###### GetByRef
使该属性的"Get"蓝图节点返回对属性的常量引用，而不是其值的副本。只对稀疏类数据生效，只能在不存在 NoGetter 时使用

###### HideAlphaChannel
用于 Fcolor 和 FLinearColor 属性。说明详细显示属性控件时 Alpha 属性应为隐藏状态

###### HideViewOptions
用于 Subclass 和 SoftClass 属性。隐藏在类选取器中修改显示选项的功能

###### InlineEditConditionToggle
表示出布尔属性只内联显示为其他属性中的一个编辑条件切换，不应显示在其自身的行上

###### LongPackageName
由 FDirectoryPath 属性使用。将路径转换为一个长的包命名

###### MakeEditWidget
用于变换或旋转体属性，或变换/旋转体的排列。说明属性应在视口中公开为一个可移动控件

###### NoGetter
防止蓝图为该属性生成一个"get"节点。只对稀疏类数据生效

## 属性
### 核心数据类型
#### 整数
整数数据类型转换是"int"或"uint"后跟位大小
| 类型    | 位数 | 是否有符号 | 范围说明             |
|:---------|:------|:-------------|:----------------------|
| `uint8`  | 8    | 无符号      | 0 到 255               |
| `uint16` | 16   | 无符号      | 0 到 65,535            |
| `uint32` | 32   | 无符号      | 0 到 4,294,967,295     |
| `uint64` | 64   | 无符号      | 0 到 18,446,744,073,709,551,615 |
| `int8`   | 8    | 有符号      | -128 到 127            |
| `int16`  | 16   | 有符号      | -32,768 到 32,767      |
| `int32`  | 32   | 有符号      | -2,147,483,648 到 2,147,483,647 |
| `int64`  | 64   | 有符号      | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807 |

##### 作为位掩码
整数属性可以位掩码形式公开给编辑器。要将整数属性标记为位掩码，只需在meta分段中添加"bitmask"即可

#### 浮点类型
虚幻使用标准C++浮点类型、浮点和双精度，float会保留小数点后6位

#### 布尔类型
布尔类型可以使用C++ bool关键字表示或表示为位域

#### 字符串
在虚幻引擎中,“文字”类型其实是三种核心类型的字符串:FName，FText和 FString。这三种类型可以互相转换。当然还有TCHAR类型，只不过TCHAR不是虚幻引擎定义的字符串类。虚幻引擎把字符串进行细分,为的是加快访问速度,以及提供本地化支持
##### FString
FString是典型的"动态字符数组"字符串类型，FString是唯一提供修改操作的字符串类。同时也意味着FString的消耗要高于FName和FText。事实上，一般我们都使用FString来传递。尽管如此，Slate控件的文字参数往往是FText。这是为了强制要求本地化
##### FName
FName是对全局字符串表中不可变且不区分大小写的字符串的引用。相较于FString，它的大小更小，更能高效的传递，但更难以操控。简单而言,FName是无法被修改的字符串,大小写不敏感。从语义上讲,名字也应该是唯一的。不管同样的字符串出现了多少次,在字符串表里只被存储一次。而借助这个哈希表，从字符串到 FName的转换，以及根据Key查询FName会变得非常快速
##### FText
FText是指定用于处理本地化的更可靠的字符串表示，FText表示一个“被显示的字符串”。所有你希望“显示”的字符串都应该是FText,因为FText提供了内置的本地化支持,也通过一张查找表来支持运行时本地化。FText不提供任何的更改操作,对于被显示的字符串来说,“修改是一个非常不安全的操作
##### TCHAR
对于大多数情况下，虚幻依靠TCHAR类型来表示字符。TEXT()宏可用于表示TCHAR文字

### 类型转换
#### 转为字符串
| 方法                                                         | 功能描述                | 说明 |
|:--------------------------------------------------------------|:-------------------------|:-----------------------------------------------------------|
| `FString::FromInt(int Value)`                                  | 整型转字符串              | 直接将 `int` 类型转换为 `FString` |
| `FString::SanitizeFloat(float Value)`                          | 浮点型转字符串            | 将 `float` 类型转换为 `FString`，并去除无意义的小数位 |
| `UKismetStringLibrary::Conv_BoolToString(bool Value)`          | 布尔型转字符串            | 将 `bool` 转换为 `FString`，需包含头文件 `#include "Kismet/KismetStringLibrary.h"` |
| `FVector::ToString()`                                           | 向量转字符串              | 将 `FVector` 转换为字符串形式，如 `X=0.000 Y=0.000 Z=0.000` |



### 属性说明符
声明属性时，属性说明符 可被添加到声明，以控制属性与引擎和编辑器诸多方面的相处方式
###### AdvancedDisplay
属性将被放置在其出现的任意面板的高级（下拉）部分中

###### AssetRegistrySearchable
AssetRegistrySearchable 说明符说明此属性与其值将被自动添加到将此包含为成员变量的所有资源类实例的资源注册表。不可在结构体属性或参数上使用

###### BlueprintAssignable
只能与组播委托共用。公开属性在蓝图中指定

###### BlueprintAuthorityOnly
此属性必须为一个组播委托。在蓝图中，其只接受带 BlueprintAuthorityOnly 标签的事件

###### BlueprintCallable
仅用于组播委托。应公开属性在蓝图代码中调用

###### BlueprintGetter=GetterFunctionName
此属性指定一个自定义存取器函数。如此属性不带 BlueprintSetter 或 BlueprintReadWrite 标签，则其为隐式BlueprintReadOnly

###### BlueprintReadOnly
此属性可由蓝图读取，但不能被修改。此说明符与 BlueprintReadWrite 说明符不兼容

###### BlueprintReadWrite
可从蓝图读取或写入此属性。此说明符与 BlueprintReadOnly 说明符不兼容

###### BlueprintSetter=SetterFunctionName
此属性拥有一个自定义编译函数，被隐式标记为 BlueprintReadWrite。注意：必须对变异函数进行命名，并为相同类的一部分

###### Category="TopCategory|SubCategory|..."
指定在蓝图编辑工具中显示时的属性类别。使用 | 运算符定义嵌套类目

###### Config
此属性将被设为可配置。当前值可被存入与类相关的.ini文件中，创建后将被加载。无法在默认属性中给定一个值。暗示为BlueprintReadOnly

###### DuplicateTransient
说明在任意类型的复制中（复制/粘贴、二进制复制等），属性的值应被重设为类默认值

###### EditAnywhere
说明此属性可通过属性窗口在原型和实例上进行编辑。此说明符与所有"可见"说明符均不兼容
**组件因为都是指针，所以不要将组件指针设为EditAnywhere或者EditDefaultsOnly,只需要设置可见性即可，即VisibleAnywhere

###### EditDefaultsOnly
说明此属性可通过属性窗口进行编辑，但只能在原型上进行。此说明符与所有"可见"说明符均不兼容

###### EditFixedSize
只适用于动态数组。这能防止用户通过虚幻编辑器属性窗口修改数组长度

###### EditInline
允许用户在虚幻编辑器的属性查看器中编辑此属性所引用的Object的属性（只适用于Object引用，包括Object引用的数组）

###### EditInstanceOnly
说明此属性可通过属性窗口进行编辑，但只能在实例上进行，不能在原型上进行。此说明符与所有"可见"说明符均不兼容

###### Export
只适用于Object属性（或Object数组）。说明Object被复制时（例如复制/粘贴操作）指定到此属性的Object应整体导出为一个子Object块，而非只是输出Object引用本身

###### GlobalConfig
工作原理与 Config 相似，不同点是无法在子类中进行覆盖。无法在默认属性中对其给定一个值。暗示为 BlueprintReadOnly

###### Instanced
仅限Object（UCLASS）属性。此类的一个实例创建时，其将被给定一个Object的特殊副本，指定到默认项中的此属性。用于实例化类默认属性中定义的子Object。暗示为 EditInline 和 Export

###### Interp
说明值可随时间由Sequencer中的一个轨道驱动

###### Localized
此属性的值将拥有一个定义的本地化值。多用于字符串。暗示为 ReadOnly

###### Native
属性为本地：C++代码负责对其进行序列化并公开到垃圾回收

###### NoClear
阻止从编辑器将此Object引用设为空。隐藏编辑器中的清除（和浏览）按钮

###### NoExport
只适用于本地类。此属性不应包含在自动生成的类声明中

###### NonPIEDuplicateTransient
属性将在复制中被重设为默认值，除非其被复制用于PIE会话

###### NonTransactional
说明对此属性值的修改不会包含在编辑器的撤销/重新执行历史中

###### NotReplicated
跳过复制。这只会应用到服务请求函数中的结构体成员和参数

###### Replicated
属性应随网络进行复制

###### ReplicatedUsing=FunctionName
ReplicatedUsing说明符指定一个回调函数，其在属性通过网络更新时执行

###### RepRetry
只适用于结构体属性。如果此属性未能完全发送（举例而言：Object引用尚无法通过网络进行序列化），则重新尝试对其的复制。对简单引用而言，这是默认选择；但对结构体而言，这会产生带宽开销，并非优选项。因此在指定此标签之前其均为禁用状态

###### SaveGame
此说明符可简便地将域显式包含，用于属性关卡中的检查点/保存系统。应在作为游戏存档一部分的所有域上设置此标签，并使用代理归档器对其进行读写。

###### SerializeText
本地属性应被序列化为文本（ImportText、ExportText）

###### SkipSerialization
此属性不会被序列化，但仍能导出为一个文本格式（例如用于复制/粘贴操作）

###### SimpleDisplay
出现在 细节 面板中的可见或可编辑属性，无需打开"高级"部分即可见

###### TextExportTransient
此属性将不会导出为一个文本格式（因此其无法用于复制/粘贴操作）

###### Transient
属性为临时，意味着其无法被保存或加载。以此方法标记的属性将在加载时被零填充

###### VisibleAnywhere
说明此属性在所有属性窗口中可见，但无法被编辑。此说明符与"Edit"说明符不兼容

###### VisibleDefaultsOnly
说明此属性只在原型的属性窗口中可见（即在蓝图编辑器中），无法被编辑。此说明符与所有"Edit"说明符均不兼容

###### VisibleInstanceOnly
说明此属性只在实例的属性窗口中可见（在原型属性窗口中不可见），无法被编辑。此说明符与所有"Edit"说明符均不兼容

### 元数据说明符
声明类、接口、结构体、列举、列举值、函数，或属性时，可添加 元数据说明符 来控制其与引擎和编辑器各方面的相处方式。每一种类型的数据结构或成员都有自己的元数据说明符列表
###### AllowAbstract="true/false"
用于 Subclass 和 SoftClass 属性。说明抽象类属性是否应显示在类选取器中

###### AllowedClasses="Class1, Class2, .."
用于 FSoftObjectPath 属性。逗号分隔的列表，表明要显示在资源选取器中的资源类类型

###### AllowPreserveRatio
用于 Fvector 属性。在细节面板中显示此属性时将添加一个比率锁

###### ArrayClamp="ArrayProperty"
用于整数属性。将可在UI中输入的有效值锁定在0和命名数组属性的长度之间

###### AssetBundles
用于 SoftObjectPtr 或 SoftObjectPath 属性。主数据资源中使用的束列表命名，指定此引用属于哪个束的一部分

###### BlueprintBaseOnly
用于 Subclass 和 SoftClass 属性。说明蓝图类是否应显示在类选取器中

###### BlueprintCompilerGeneratedDefaults
属性默认项由蓝图编译器生成，CopyPropertiesForUnrelatedObjects 在编译后调用时将不会被复制

###### ClampMin="N"
用于浮点和整数属性。指定可在属性中输入的最小值 N

###### ClampMax="N"
用于浮点和整数属性。指定可在属性中输入的最大值 N

###### ConfigHierarchyEditable
此属性被序列化为一个配置（.ini）文件，可在配置层级中的任意处进行设置

###### ContentDir
由 FDirectoryPath 属性使用。说明将使用 Content 文件夹中的Slate风格目录选取器来选取路径

###### DisplayAfter="PropertyName"
在蓝图编辑器中，名为 PropertyName 的属性后即刻显示此属性。前提是两个属性属于同一类别，则忽略其在源代码中的顺序进行显示。如多个属性有相同的 DisplayAfter 值和相同的 DisplayPriority 值，将在指定属性之后，按照自身在标头文件中声明的顺序显示

###### DisplayName="Property Name"
此属性显示的命名，不显示代码生成的命名

###### DisplayPriority="N"
如两个属性有相同的 DisplayAfter 值，或属于同一类别且无 DisplayAfter 元标签，则此属性将决定其顺序。最高优先级值为1，表示 DisplayPriority 值为1的属性将在 DisplayProirity 值为2的属性之上显示。如多个属性有相同的 DisplayAfter 值，其将按照在标头文件中声明的顺序显示

###### DisplayThumbnail="true"
说明属性是一个资源类型，其应显示选中资源的缩略图

###### EditCondition="BooleanPropertyName"
对一个布尔属性进行命名，此属性用于说明此属性的编辑是否被禁用。将"!"放置在属性命名前可颠倒测试

###### EditFixedOrder
使排列的元素无法通过拖拽来重新排序
**EditCondition元标签不再仅限于单个布尔属性。它现在由完全成熟的算式解析器计算，意味着可以包含一个完整的C++表达式

###### ExactClass="true"
结合 AllowedClasses 用于 FSoftObjectPath 属性。说明是否只能使用 AllowedClasses 中指定的准确类，或子类是否同样有效

###### ExposeFunctionCategories="Category1, Category2, .."
在蓝图编辑器中编译一个函数列表时，指定其函数应被公开的类目的列表

###### ExposeOnSpawn="true"
指定此属性是否应在此类类型的一个Spawn Actor节点上公开

###### FilePathFilter="FileType"
由 FFilePath 属性使用。说明在文件选取器中显示的路径过滤器。常规值包括"uasset"和"umap"，但这些并非唯一可能的值

###### GetByRef
使该属性的"Get"蓝图节点返回对属性的常量引用，而不是其值的副本。只对稀疏类数据生效，只能在不存在 NoGetter 时使用

###### HideAlphaChannel
用于 Fcolor 和 FLinearColor 属性。说明详细显示属性控件时 Alpha 属性应为隐藏状态

###### HideViewOptions
用于 Subclass 和 SoftClass 属性。隐藏在类选取器中修改显示选项的功能

###### InlineEditConditionToggle
表示出布尔属性只内联显示为其他属性中的一个编辑条件切换，不应显示在其自身的行上

###### LongPackageName
由 FDirectoryPath 属性使用。将路径转换为一个长的包命名

###### MakeEditWidget
用于变换或旋转体属性，或变换/旋转体的排列。说明属性应在视口中公开为一个可移动控件

###### NoGetter
防止蓝图为该属性生成一个"get"节点。只对稀疏类数据生效


## 结构体
结构体（Struct）是一种数据结构，帮助组织和操作相关属性。在虚幻引擎中，结构体能够被引擎的反射系统识别，但不属于UObject生态圈的一部分。因此，创建它们要比在同样的数据布局中创建 UObject 更快，且支持UProperties，但无法被垃圾回收系统处理，也不能提供UFunctions

**注意，UStruct无法在类中使用**

要将一个结构体变成UStruct，需使用结构体定义上方的 USTRUCT 标签，并在定义的第一行中包含 GENERATED_BODY()







## 命名规则
###### F
纯C++类
###### U
继承自UObject，但不继承自Actor，以U开头的都是组件，只能依附于其他组件，不能单独放置到场景中
###### A
继承自Actor，可以放置在场景中
###### S
Slate控件相关类
###### H
HitResult相关类


## Gameplay框架
### Object
#### UObject
##### 提供功能
- GC垃圾回收
- Serialization/序列化
- Editable/编辑器可见
- Reflection/反射可见
- ClassDefaultObject(CDO)/原数据（MetaData）
配合UCLASS和CDO，可以为特定对象进行实例恢复
- UE构建是一个UObject的世界
#### 语法
###### #include"CoreMinimal.h"
对其他头文件的包含，包含一套来自UE4核心编程环境的普遍类型
###### UCLASS
为Uobject提供一个对UCLASS的引用，描述其基于虚幻的类型
可以在括号内填写参数，如Blueprintable
每个UCLASS保留一个“类默认对象”（Class Default Object,CDO）
可以通过GetClass()函数在任意时刻获取对象的UCLASS
###### GENERATED_BODY()
必须放在类的最上方，实现头文件中函数调用。同时实现字符串宏的调用，实现函数声明、注册友元、静态对象注册、UCLASS回调等
#### UClass
### Actor和Component
#### AActor
##### 提供功能
- Replication/网络复制
- Spawn/生成和销毁
- Tick
- TArray<AActor*>
- AActor* Owner
Actor可以互相嵌套，互为父子节点关系
#### Component
Actor需要默认的根组件USceneComponent* RootComponent
Actor只有拥有了根组件后，才具有transform属性
##### 提供功能
组件的两大核心功能
- Transform
- SceneComponent之间的嵌套
#### Actor和Component的关系
Actor是一个人，人的躯干是RootComponent，四肢和头是5个Component
移动控制Root，从而实现整体控制
actor只是一个容器 具体的行为由各个组件提供

**通过AttachToActor添加到另一个Actor的子节点
间接调用了RootComponent的AttchToComponent函数，实现父子节点关系的确定**

维护Actor父子节点关系都是靠Component来实现
组件依次派生慢慢出现了物理、材质、网格等功能 最终合成了一个最常见的根组件----
StaticMeshComponent
组件是对Actor的扩展，让Actor具备了独立解决问题的能力，也具备自主思想
#### UActorComponent
不可以嵌套，没有Transform属性，派生类有AIComponent、UMovementComponent等
#### USceneComponent
继承自UActorComponent，提供了嵌套功能，增加了Transform属性，Transform属性可以用来描述父子节点关系
Actor只有拥有了USceneComponent组件，才拥有变换属性，才可以在场景中拥有了位置、旋转、缩放等属性
派生类有UPrimitiveComponent、UChildActorComponents

### ULevel和UWorld
当场景中出现了大量的Actor，就需要一个类对Actor进行管理和组织，于是就出现了Level
因为每一个关卡不会无限制增大，所以一个游戏往往具有好多个level，那么就需要对level进行组织和管理，于是就出现了World
#### ULevel
ULevel继承于UObject，具备UObject的一切功能
ULevel包含一个ALevelScriptActor蓝图脚本，即关卡蓝图
#### UWorld
所有的关卡都需要管理,管理关卡的类叫做UWorld
UWorld区分了持久化关卡1个和 流送关卡n个,决定关卡的加载机制（1一开始运行就默认加载，2-运行时Streaming动态加载）
#### AInfo
存储属性、光照信息、物理数据等。记录着当前level的规则属性。记录了GameMode
#### AWorldSettiings
世界设置，继承于AInfo
Level是Actor的容器，可以通过蓝图脚本实现关卡逻辑，也可以设置和读取游戏模式
#### EWorldContext
世界上下文枚举，包括None、Game、Editor、PIE、Preview、Inactive
#### FWorldComtext
世界上下文类，保存着当前运行的world，可以实现一个world到另一个world的切换，一般openlevel也需要FWorldContext参数
### UEngine
游戏框架最顶端的类，包含两个子类UEditorEngine和UGameEngine
#### UEditorEngine
即UE编辑器，包含一个UWorld指针
#### UGameEngine
即游戏，包含一个单例GameInstance
Object->Actor+Component->Level->world->WorldContext->GameInstance->Engine
### Pawn
APawn继承于Actor
#### 提供功能
- 可被controller控制
- PhysicsCollision
- MovementInput响应 InputComponent输入组件
#### 派生类
#### DefaultPawn
默认包括 DefaultPawnMovementComponent和SphereCollisionComponent、StaticMeshComponent
#### SpectatorPawn
包括 USpectatorPawnMovementComponent(不带任何重力的漫游输入)
关闭了StaticMesh碰撞设置到了Spectator通道
#### Character
包含CharacterMovementComponent、CapsuleComponent、骨骼和蒙皮mesh

## 常用方法
### Actor的静态函数
继承自Actor的类都可直接调用
###### GetWorld()
缓存世界指针的Getter，会返回世界场景，如果参与者实际上没有在某个级别中生成，则将返回null

**游戏编程中一般不要用++，容易出现莫名其妙的bug，一般都用+=1**

### TSubclassOf
TSubclassOf是提供UClass类型安全性的模板类。例如在创建一个投射物类，允许设计者指定伤害类型。可以只创建一个UClass 类型的UPROPERTY，让设计者指定派生自UDamageType的类；或者可使用 TSubclassOf 模板强制要求此选择
#### 正常方式声明
可选择任意 UClass
```
/** type of damage */
UPROPERTY(EditDefaultsOnly, Category=Damage)
UClass* DamageType;
```
### 使用TSubclassOf声明
模板类告知编辑器的属性窗口只列出派生自 UDamageType 的类（作为属性选择）
```
/** type of damage */
UPROPERTY(EditDefaultsOnly, Category=Damage)
TSubclassOf<UDamageType> DamageType;
```
除 UPROPERTY 安全外，还能获得 C++ 层级上的类型安全。如尝试进行不兼容 TSubclassOf 类型的相互指定，将出现编译错误。尝试指定泛型 UClass 时，它将执行一个运行时检查，以确定它可执行指定。如运行时检查失败，结果数值为 nullptr
```
UClass* ClassA = UDamageType::StaticClass();
TSubclassOf<UDamageType> ClassB;
ClassB = ClassA; // Performs a runtime check
TSubclassOf<UDamageType_Lava> ClassC;
ClassB = ClassC; // Performs a compile time check
```

### FTimerManager
变量定时器
#### FTimerManager::SetTimer()
##### 参数
###### FTimerHandle &InOutHandle
句柄，句柄是唯一ID，可用于区分具有相同委托的计时器。一般需要在.h文件中定义
例：FTimerHandle MyTimerHandle;
###### UserClass *InObj
调用者，一般是自己调用，用this
###### FSimpleDelegate::TUObjectMethodDelegate_Const<UserClass>::FMethodPtr InTimerMethod
委托调用的函数，计时器计时的同时调用的委托函数
例：&MyActor::UpdateTimer

**委托调用的函数就是用函数指针调用的函数**

###### float InRate
执行的速率，即多少秒执行一次委托函数，单位是秒
###### bool InbLoop=false
如果为真，则一直保持以执行的速率循环执行，否则只执行一次
###### float InFirstDelay=(-1.0F)
循环计时器第一次执行前等待时间，如果小于0则执行


## Debug方法
### 输出字符串
#### 打印字符串到屏幕
与蓝图中的Print String节点功能类似
函数原型：
```
void UEngine::AddOnScreenDebugMessage(uint64 Key, float TimeToDisplay, FColor DisplayColor, const FString& DebugMessage, bool bNewerOnTop, const FVector2D& TextScale)
//Key-------------字符串索引，-1为新的字符串
//TimeToDisplay---显示时长
//DisplayColor----显示颜色
//DebugMessage----显示的字符串内容
//bNewerOnTop-----布尔值，真为在堆区开辟空间，假为在栈区开辟空间
//TextScale-------字体大小
```
例：
```
FString filePath;
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Green, FString::Printf(TEXT("DLL_Init")));
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Green, FString::Printf(TEXT("%s"), *filePath));
```
#### 输出字符串到日志
语法：
```
UE_LOG(Log类,Log类型,Log内容);
//Log类需要提前定义，如果没有提前定义，可以使用LogTemp
//Log类型分3种，Log、Warning、Error，区别是颜色不同，Log为灰色，Warning为黄色，Error为红色
//Log内容根据需要自行构建，常用符号
//（1）%s字符串(FString)
//（2）%d整型数据(int32)
//（3）%f浮点型数据(float)
```
例：
```
FString filePath
UE_LOG(LogTemp, Log, TEXT("%s"), *filePath);
UE_LOG(LogTemp, Error, TEXT("Hello,World!"));
```
#### Print String
蓝图中的Print String调用的是c++中的UKismetSystemLibrart::PrintString父函数，也可以直接在C++中使用
需要包含头文件
```
#include "Kismet/KismetSystemLibrary.h"
```
```
UKismetSystemLibrart::PrintString(this,TEXT("打印内容"));
```