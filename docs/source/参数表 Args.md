# 参数表 Args
## 头文件
```c
#include "dataArgs.h"
```
## 概述

1. Args参数表API是以 args_ 为前缀的一系列函数。
1. Args参数表API是使用面向对象的思想设计的，这些函数的第一个入口参数都是被操作参数表的指针。
1. Args参数表使用**键值对(Map)**数据模型，或称为**字典(Dist）**。
1. 一个参数表内可以包含**任意个**参数，每个参数使用**参数名（键）**索引。
1. 索引得到的参数可以是**基本数据类型(int, float, pointer, string)**或者**泛型**参数(Arg)。
1. Args参数表支持**动态**地**增加、删除、修改、查找**参数。
1. Args参数表**不支持嵌套**（和PikaObj属性的主要区别）。
## 数据类型
参数表的数据类型是Args。
```c
typedef Link Args;
```
参数表内部基于链表（Link）实现。
**注意不要直接访问Args内部的链表**，请使用Args API访问Args。以获得**最大的向后兼容性**。

## 参数表的新建和销毁

1. 新建参数表，从堆中新建一个参数表，返回参数表的指针。**注意新建的参数表需要手动销毁来回收内存。不断新建参数表但不销毁会导致内存泄漏。**

[注意] 为避免内存泄漏，请在 [docker 开发环境](https://pikadoc.readthedocs.io/zh/latest/get-start_linux.html) 下进行开发，确保充足的单元测试和内存检查。

```c
Args* New_args(Args* args);
```
新建参数表传入的参数是一个预留的辅助参数表，通常情况下填NULL即可。

2. 销毁参数表。当一个参数表被销毁时，参数表**内部的所有参数也会被自动销毁**。
```c
void args_deinit(Args* self);
```
传入参数表的指针，销毁参数表。
## 增删改查API
这一部分API提供了对参数表的增删改查。
### 基本类型的增删改查
Args参数表支持**整形、浮点型、指针、字串**四种基本类型的参数。使用set和get方法即可读写一个参数表内的参数。

Args参数表是**动态**的，因此可以随时为参数表新增新的参数。

基本类型属性的API有如下这些，和对象的参数API相似，但**不支持嵌套**：
```c
/* set API */
int32_t args_setInt(Args* self, char* name, int64_t int64In);
int32_t args_setFloat(Args* self, char* name, float argFloat);
int32_t args_setPtr(Args* self, char* name, void* argPointer);
int32_t args_setStr(Args* self, char* name, char* strIn);

/* get API */
int64_t args_getInt(Args* self, char* name);
float args_getFloat(Args* self, char* name);
void* args_getPtr(Args* self, char* name);
char* args_getStr(Args* self, char* name);
```
基本类型属性的命名方式为args_set[Type]和args_get[Type]。

1. 第一个输入参数为要操作的参数表指针。
1. 第二个输入参数为参数名
1. set方法的第三个输入参数为写入的参数值，get方法的返回值为读取的参数值。
1. set方法的返回值为错误码，为0表示无错误发生。
### 泛型参数
args支持泛型参数，同样提供set方法和get方法。输入参数和返回值与基本类型相似。
args_getType可以获得参数的类型。
```c
int32_t args_setArg(Args* self, Arg* arg);
Arg* args_getArg(Args* self, char* name);
ArgType args_getType(Args* self, char* name);
```
泛型参数在使用时需要转换为基本类型。

使用以下API可以判断泛型参数的当前类型。
```c
ArgType arg_getType(Arg* self);
```
使用以下的API可以将泛型参数转换为基本类型。
```c
int64_t arg_getInt(Arg* self);
float arg_getFloat(Arg* self);
void* arg_getPtr(Arg* self);
char* arg_getStr(Arg* self);
```
### 参数管理

1. 使用参数名哈希或者参数名判断一个参数是否存在，返回值为1表示存在，使用times33算法获得参数名哈希。
```c
int32_t args_isArgExist_hash(Args* self, Hash nameHash);
int32_t args_isArgExist(Args* self, char* name);
Hash hash_time33(char* str);
```

2. 使用泛型参数的指针删除一个参数
```c
int32_t args_removeArg(Args* self, Arg* argNow);
```
返回值为错误码，为0表示成功。
## 参数表的遍历
可以使用下面的API遍历一个参数表。

1. 第一个入口参数是参数表的指针。
1. 第二个参数是遍历参数时的回调函数的函数指针
1. 第三个参数是辅助的参数表，用来传递辅助参数，在不使用辅助参数时，第三个输入参数可以填NULL。
```c
int32_t args_foreach(Args* self,
                     int32_t (*eachHandle)(Arg* argEach, Args* handleArgs),
                     Args* handleArgs);
```
