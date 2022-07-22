# Content

[Part I C++基础](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#part-i-c%E5%9F%BA%E7%A1%80)

&nbsp;&nbsp;&nbsp;&nbsp;[Chapter2 变量和类型](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#chapter2-%E5%8F%98%E9%87%8F%E5%92%8C%E7%B1%BB%E5%9E%8B)

&nbsp;&nbsp;&nbsp;&nbsp;[Chapter3 字符串、向量和数组](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#chapter3-%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%90%91%E9%87%8F%E5%92%8C%E6%95%B0%E7%BB%84)

# Part I C++基础

## Chapter2 变量和类型
### 2.1 基本内置类型
&nbsp;&nbsp;&nbsp;&nbsp;C++基本数据类型--算术类型（整型、浮点型、布尔、字符）和空类型
  
#### 2.1.1 算术类型
&nbsp;&nbsp;&nbsp;&nbsp;算术类型又分为两类--
  
 - 整型（包括布尔与字符型）

| Type | Minimum Length | Description |
| ----- | :---: | :---: |
| short | 16 | - |
| int   | 16 | - |
| long  | 32 | - |
| long&nbsp;long | 64 | C++11中新引入的类型 |
| char  | 8 | 一个char的空间应确保可以存放机器基本字符集中任意字符对应的数值，即一个char与一个机器字节大小一致 |
| wchar_t | 16 | wchar_t是宽字符，用于确保可以存放机器最大扩展字符集 |
| char16_t | 16 | Unicode字符类型 |
| char32_t | 32 | Unicode字符类型 |
  
 - 浮点型

| Type | Minimum Length | Description |
| ----- | :---: | :---: |
| float | 32 | - |
| double | 64 | - |
| long&nbsp;double | 96or128 | - |

&nbsp;&nbsp;&nbsp;&nbsp;**带符号与无符号类型**

&nbsp;&nbsp;&nbsp;&nbsp;以上的算术类型都是默认的带符号类型，在这些类型名前添加unsigned就可以得到无符号类型

&nbsp;&nbsp;&nbsp;&nbsp;与整型不同，字符型被分为char、signed char和unsigned char，需要注意的是：尽管有三种字符型，但表现形式仍是只有两种，且char与signed char并不一样，char的表现形式具体是由编译器决定的


&nbsp;&nbsp;&nbsp;&nbsp;**类型选择建议：**
  
1. 当明确知晓数值不可能为负时，选用无符号
2. 如果使用整型执行整数运算而数值可能超过了int的表示范围，选用long long，因为short太短而long一般和int有一样的尺寸
3. 在算术表达式中不要使用char或bool，因为char在不同机器上的有无符号是不同的，很容易出问题
4. 执行浮点数运算选用double，因为float通常精度不足且二者的计算代价相差无几，甚至可能双精度比单精度运算还快；但long double一般是没有必要的，精度没有普遍的需求且运行耗时较高


#### 2.1.2 类型转换

&nbsp;&nbsp;&nbsp;&nbsp;对象的类型定义了对象能包含的数据和能参与的运算，其中一种运算被大多数类型支持，即将对象从一种类型_转换_为另一种_相关_类型；（***类型转换是一种运算***）

&nbsp;&nbsp;&nbsp;&nbsp;当在程序的某处我们使用了一种类型而其实对象应该取另一种类型时，程序会_自动进行类型转换_；因此有必要知道当给某种类型的对象强行赋了另一种类型的值时，具体会发生什么：

&nbsp;&nbsp;&nbsp;&nbsp;类型所能表示的值的范围决定了实际的转换过程：

1. 非布尔类型的值赋给布尔类型，为0则结果为false，否则为true，布尔赋给非布尔类型同理，true会被转换为1
2. 浮点数赋给整数类型时，进行近似处理，仅保留浮点数小数点前的部分
3. 整数赋给浮点数时，小数部分计0；若大小超过浮点数类型容量，则可能损失精度
4. 当给无符号数赋一个超出范围的值时，结果是初始值对可表示数值总数取模后的余数；例如把-1赋给unsigned char类型，实际结果为255
5. 当赋给带符号类型一个超出范围的值时，结果时未确定的

&nbsp;&nbsp;&nbsp;&nbsp;***要尽量避免无法预知和依赖于实现环境的行为，保证程序的可移植性***

&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;**含有无符号类型的表达式**

&nbsp;&nbsp;&nbsp;&nbsp;当表达式中同时出现无符号和有符号数时，***带符号类型会自动转换为无符号类型***，尤其为负数时，同上第4条

&nbsp;&nbsp;&nbsp;&nbsp;再次重复：***无符号数不会小于0***，因此在某些循环中，看似循环变量i不会小于0，但不意味着可以放心将它定义为unsigned int，因为当i为0时，i再次减1会成为负数，但因为无符号数不会小于0，实际值一定是大于0的，最终导致无限循环

&nbsp;&nbsp;&nbsp;&nbsp;因此，切忌混用带符号与无符号类型

#### 2.1.3 字面值常量

&nbsp;&nbsp;&nbsp;&nbsp;每个字面值常量都对应一种数据类型，字面值常量的形式和值决定了它的数据类型

&nbsp;&nbsp;&nbsp;&nbsp;**整型和浮点型字面值**

&nbsp;&nbsp;&nbsp;&nbsp;整型字面值可以写作十进制、八进制或十六进制的形式，八进制以0开头，十六进制以0x开头；

&nbsp;&nbsp;&nbsp;&nbsp;整型字面值的数据类型由其值和符号决定：

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;十进制字面值默认是带符号的（但不会是负数，_负号并不在字面值之内_，作用仅仅是对字面值取负），类型为int、long、long long中尺寸最小的；

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;八进制和十六进制字面值是六种有无符号整型类型中尺寸最小的；

&nbsp;&nbsp;&nbsp;&nbsp;浮点数字面值默认类型是double

&nbsp;&nbsp;&nbsp;&nbsp;**字符和字符串字面值**

&nbsp;&nbsp;&nbsp;&nbsp;由单引号括起来的一个字符称为char型字面值，双引号括起来的是字符串型字面值

&nbsp;&nbsp;&nbsp;&nbsp;如果两个字符串字面值位置紧邻且仅由空格、缩进和换行符分隔，则它们实际上是一个整体，_适应长字符串多行书写_

```
std:cout << "a really, really long string literal "
            "that spans two lines" << std:endl;
```

&nbsp;&nbsp;&nbsp;&nbsp;**指定字面值类型**

&nbsp;&nbsp;&nbsp;&nbsp;通过添加前缀和后缀，可以改变整型、浮点型和字符型字面值的默认类型

字符和字符串字面值
| 前缀 | 含义 | 类型 |
| :---: | :---: | :---: |
| u | Unicode16字符 | char16_t |
| U | Unicode32字符 | char32_t |
| L | 宽字符 | wchar_t |
| u8 | UTF-8 | char |

整型字面值
| 后缀 | 最小匹配类型 |
| :---: | :---: |
| u/U | unsigned |
| l/L | long |
| ll/LL | long long |

浮点型字面值
| 后缀 | 类型 |
| :---: | :---: |
| f/F | float |
| l/L | long double |

### 2.2 变量

#### 2.2.1 变量定义

&nbsp;&nbsp;&nbsp;&nbsp;变量定义的基本形式是，类型说明符 + 一个或多个变量名组成的列表；定义时还可以为一个或多个变量赋初值

> 遵循大多数人的习惯用法，即认为对象是具有某种数据类型的内存空间，我们使用对象这个词时，并不严格区分是类还是内置类型，也不区分是否命名或是否只读

&nbsp;&nbsp;&nbsp;&nbsp;**初始值**

&nbsp;&nbsp;&nbsp;&nbsp;当对象***在创建时***获得了一个特定的值，我们说这个对象被初始化了；

&nbsp;&nbsp;&nbsp;&nbsp;且在同一条定义语句中，可以用先定义的变量值去初始化后定义的其他变量

```
double price = 109.99, discount = price * 0.16;
```

&nbsp;&nbsp;&nbsp;&nbsp;在C++中，初始化是一个异常复杂的问题，对于使用等号=来初始化变量的方式容易让人认为初始化是赋值的一种，然而***初始化和赋值是两个完全不同的操作***；初始化的含义是创建变量时赋予其一个初始值，而赋值的含义是把对象当前值擦除，以一个新的值来替代

&nbsp;&nbsp;&nbsp;&nbsp;**列表初始化**

&nbsp;&nbsp;&nbsp;&nbsp;无论是初始化对象还是为对象赋新值的时候，都可以使用一组由花括号括起来的初始值，这种形式被称为列表初始化；

&nbsp;&nbsp;&nbsp;&nbsp;当用于内置类型的变量时，列表初始化有一个重要的特点：如果使用列表初始化且初始值存在丢失信息的风险，则编译器将报错

```
long double = ld = 3.1415926536
int a{ld}, b = {ld};  // 错误：转换未执行，因为存在丢失信息风险
int c(ld), d = id;    // 正确：转换执行，且确实丢失了部分值
```

&nbsp;&nbsp;&nbsp;&nbsp;**默认初始化**

&nbsp;&nbsp;&nbsp;&nbsp;如果定义变量时没有指定初始值，则变量被默认初始化，即被赋予了默认值，而默认值到底是什么由变量类型决定，且定义变量的位置也会有所影响



#### 2.2.2 变量声明和定义的关系

## Chapter3 字符串、向量和数组
