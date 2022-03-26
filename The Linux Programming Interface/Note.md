## Content

[Part I](https://github.com/Jarvis-Guo/Notes/blob/main/The%20Linux%20Programming%20Interface/Note.md#part-i-%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E4%B8%8Eunixlinux%E5%9F%BA%E7%A1%80)

## Part I 操作系统与UNIX/Linux基础

### 1. History and Standards
Linux是类UNIX操作系统的一种，想学习Linux必须了解UNIX的历史。首先声明UNIX一词的含义，主要有两种主流的定义，一种是指能够通过单一UNIX规范的官方测试并获得The Open Group授权使用UNIX冠名的操作系统；另一种是指与经典UNIX系统相似的操作系统

最初的UNIX实现是由贝尔实验室的Ken Thompson使用汇编语言编写的，其中的一些特性（如树状文件系统、使用shell解析命令、非结构的字节流式文件）继承自AT&T与MIT和GE合作的操作系统项目MULTICS（Multiplexed Information and Computing Service），而UNIX的命名也是相对于该项目名的一个双关

Ken Thompson的同事Dennis Ritchie（也是UNIX共同开发者之一）随后设计并实现了C语言，并伴随着不断演进，UNIX逐渐可以由C语言进行重写，这也使随后系统移植到不同硬件架构上成为可能；而C语言及其派生语言C++在系统编程语言中十分流行，适合系统层面应用编程（_具体原因可以深究_）。从设计目标角度来讲，不像用于数学计算的FORTRAN语言，或是用于处理面向记录的数据流的商业系统语言COBOL，C语言就是为UNIX内核与相关软件设计的一种高级语言

1969年至1979年之间，UNIX经历了多个版本的发布，其名声也开始流传，尤其伴随上文两位大神的论文《The UNIX Time-Sharing System》发布。在这个阶段，AT&T拥有政府授权的电话系统行业垄断，其中的条款包括禁止销售软件，也意味着不能将UNIX作为产品销售。因此，AT&T对外只面向大学发布UNIX版本，例如相关文档和内核源码，计算机系的学生和教授便有机会学习甚至进行修改，这也大大推进了操作系统的发展以及UNIX本身的知名度

在UNIX发布第七版后，UNIX逐渐形成两个分支：BSD和System V。

在1975到1976学年，Ken Thompson回到母校UCB作为visiting professor带领研究生为UNIX增加了许多新的特性和工具，包括C shell，vi编辑器，BFFS，虚拟内存管理等等，最终便以BSD（Berkeley Software Distribution）的名义对外发布各个版本。其中UCB的CSRG发布的4.2BSD很有意义，因为它首次包括了完整的TCP/IP实现。

而System V是AT&T解体后推出的UNIX发行版中的一个重要版本，其中也继承了部分BSD的特性，例如网络功能等。个人理解System V为商用的UNIX操作系统，授权给供应商作为它们自己系统（如SunOS，Solaris等）的底座

当时这种授权的商业模式导致各供应商的产品之间绝缘，每个公司所生产的一个或多个计算机芯片架构只支持自己发行的系统，造成用户被锁死在一个品牌上，切换设备或系统代价很高，因此也推动了可移植UNIX系统的发展

顺便提到UNIX的显著特征之一：它由多个组织共同开发推进其发展，也因此可以看到UNIX中有很多新颖的特性，但同时使一个应用能够在所有其实现版本上运行的难度也增加了，可谓集思广益又集思广“异”

### 2. Fundamental Concepts

## Part II 文件系统

## Part III 信号、进程与线程
