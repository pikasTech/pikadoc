# 泛型参数 Arg

## 头文件

```c
#include "dataArg.h"
```

## 概述

1. arg 泛型参数API是以 arg_ 为前缀的一系列函数。
1. arg 中可以保存一个任意类型的值。
1. arg 支持的类型有：int，float，pointer, string, null, bytes。
1. arg 放入对象后，可以直接在 python 脚本中访问 arg 的值。

## 数据类型

泛型参数的数据类型是 Arg。

```c
typedef struct Arg Arg;
struct Arg {
    Arg* next;
    uint32_t size;
    uint8_t type;
    Hash name_hash;
    uint8_t content[];
};
```

泛型参数内部包括头部信息 ( size, type, name_hash )，数据体 (content)，和用于构成链表的指针 (next)。

**注意不要直接访问arg 内部的成员**，请使用arg  API访问arg 。以获得**最大的向后兼容性**。
​

## 泛型参数的新建和销毁

1. 新建泛型参数，从堆中新建一个泛型参数，返回泛型参数的指针。**注意新建的泛型参数需要手动销毁来回收内存。不断新建泛型参数但不销毁会导致内存泄漏。**

```c
Arg* arg_newInt(int val);
Arg* arg_newFloat(double val);
Arg* arg_newPtr(ArgType type, void* pointer);
Arg* arg_newStr(char* val);
Arg* arg_newNull(void);
Arg* arg_newBytes(uint8_t* src, size_t size);
```

新建 arg 传入的参数是 arg 的值。
​


2. 销毁泛型参数。

```c
void arg_deinit(arg* self);
```

传入泛型参数的指针，销毁泛型参数。

## 得到泛型参数的值

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
uint8_t* arg_getBytes(Arg* self);
size_t arg_getBytesSize(Arg* self);
```

## 重要注意事项

直接使用 arg_new\<Type\>() api **极易引起** 内存泄漏或悬垂引用，导致 **致命缺陷**。

请在 [docker 开发环境](https://pikadoc.readthedocs.io/zh/latest/get-start_linux.html) 下进行开发，确保充足的单元测试和内存检查。

## 案例

使用 arg 构建一个字符串列表

``` C
#include "PikaStdData_List.h"
...
    /* 创建 list 对象 */
    PikaObj* list = newNormalObj(New_PikaStdData_List);
    /* 初始化 list */
    PikaStdData_List___init__(list);
    /* 用 arg_new<type> 的 api 创建 arg */
    Arg* str_arg1 = arg_newStr("aaa");
    /* 添加到 list 对象 */
    PikaStdData_List_append(list, token_arg);
    /* 销毁 arg */
    arg_deinit(token_arg);
...
```

