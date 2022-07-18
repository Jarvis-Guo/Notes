## Content

[Part I C++基础](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#part-i-c%E5%9F%BA%E7%A1%80)

&nbsp;&nbsp;&nbsp;&nbsp;[Chapter2 变量和类型](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#chapter2-%E5%8F%98%E9%87%8F%E5%92%8C%E7%B1%BB%E5%9E%8B)

&nbsp;&nbsp;&nbsp;&nbsp;[Chapter3 字符串、向量和数组](https://github.com/Jarvis-Guo/Notes/blob/main/C++Primer/Note.md#chapter3-%E5%AD%97%E7%AC%A6%E4%B8%B2%E5%90%91%E9%87%8F%E5%92%8C%E6%95%B0%E7%BB%84)

## Part I C++基础

### Chapter2 变量和类型
#### 2.1 基本内置类型
&nbsp;&nbsp;&nbsp;&nbsp;C++基本数据类型--算术类型（整型、浮点型、布尔、字符）和空类型
  
##### 2.1.1 算术类型
&nbsp;&nbsp;&nbsp;&nbsp;算术类型又分为两类--
  
&nbsp;&nbsp;&nbsp;&nbsp;整型
  
&nbsp;&nbsp;&nbsp;&nbsp;浮点型
  


&nbsp;&nbsp;&nbsp;&nbsp;**带符号与无符号类型**
  
&nbsp;&nbsp;&nbsp;&nbsp;**类型选择建议：**
  
1. 当明确知晓数值不可能为负时，选用无符号
2. 如果使用整型执行整数运算而数值可能超过了int的表示范围，选用long long，因为short太短而long一般和int有一样的尺寸
3. 在算术表达式中不要使用char或bool，因为char在不同机器上的有无符号是不同的，很容易出问题
4. 执行浮点数运算选用double，因为float通常精度不足且二者的计算代价相差无几，甚至可能双精度比单精度运算还快；但long double一般是没有必要的，精度没有普遍的需求且运行耗时较高


##### 2.1.2 类型转换
  

### Chapter3 字符串、向量和数组
