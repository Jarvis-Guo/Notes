## Content

## 1. History and Standards

UNIX的显著特征之一：由多个组织共同开发推进其演进，也因此UNIX中有很多新颖的特性，但同时一个应用能够在所有其实现版本上运行的难度也增加了，可谓集思广益又集思广“异”

两个主流对UNIX一词的定义

第一个UNIX实现是由贝尔实验室的Ken Thompson使用汇编语言编写的，其中的一些特性（如树状文件系统、使用shell解析命令、非结构的字节流式文件）继承自MULTICS项目。而UNIX的命名也是相对于该项目名的一个双关

Ken Thompson的同事Dennis Ritchie随后设计并实现了C语言，并伴随着不断演进，UNIX逐渐可以由C语言进行重写，这也使随后系统移植到不同硬件架构上成为可能（原因是什么？？）

C语言及其派生语言C++在系统编程语言中十分流行，适合系统层面应用编程（具体根因是什么呢？？跟操作系统同源？？）

AT&T面向大学发布UNIX版本大大推进了操作系统的发展以及UNIX本身的名气

发布第七版后，UNIX逐渐分为两大变体BSD和System V

Ken Thompson回到母校UCB作为visiting professor带领学生为UNIX增加了许多新的特性和工具，包括C shell，vi编辑器，BFFS，虚拟内存管理等等，这也就有了BSD（Berkeley Software Distribution）

UCB发布的4.2版本BSD很有意义，它包括了完整的TCP/IP实现

System V是AT&T解体后推出的UNIX发行版中的一个重要版本，其中也继承了部分BSD的特性，例如网络功能等。个人理解System V为商用的UNIX操作系统，授权给供应商作为它们自己系统（如SunOS，Solaris等）的底座

当时这种授权的商业模式导致各供应商的产品之间绝缘，每个公司所生产的一个或多个计算机芯片架构只支持自己发行的系统，造成用户被锁死在一个品牌上，切换设备或系统代价很高，因此也推动了可移植UNIX系统的发展
## 2. Fundamental Concepts
