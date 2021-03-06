# 字串池 Strs
## 头文件
```c
#include "dataStrs.h"
```
## 概述

1. Strs字串池API是以 strs 为前缀的一系列函数。
1. 字串池为字符串提供提供**动态的内存空间**，支持**任意长度**的字符串，一个字串池能够存储**任意多个**字符串。
1. 提供**方便的内存管理**，在销毁字串池时，池内的所有字符串内存会被自动**批量销毁**。
1. 提供**安全的操作方式**，在使用strs API时，被引用的字符串**不会被修改**。所有修改在**新申请的内存区**产生。因此不会出现**悬空指针**，被引用的字符串**被篡改**之类的严重安全问题。
1. Strs字串池API是使用面向对象的思想设计的，这些函数的第一个入口参数都是被操作字串池的指针。
## 数据类型
Strs的数据类型是Args，内部维护一个参数表。
```c
typedef Link Args;
```
**注意不要直接访问字串池的参数表**，请使用Strs API访问Strs，以获得**内存安全性**和**最大的向后兼容性**。
