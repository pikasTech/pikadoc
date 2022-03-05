# Pika 对象 PikaObj
## 1. 头文件
```c
#include "PikaObj.h"
```
## 2. 概述

1. 对象API是以 **obj_** 为前缀的一系列函数。
1. 对象API提供了**在C中访问Python对象**的一系列接口。**在模块开发中使用频率最高。**
1. 对象API本身也是使用面向对象的思想设计的，这些函数的第一个入口参数都是被操作对象的指针。
1. 一个对象由属性和方法两个部分组成，因此对象API也分为属性和方法两个部分。
## 3. 数据类型
对象本身的数据类型是PikaObj，所有Python对象在C中访问时均使用这个数据类型。
```c
struct PikaObj_t {
    /* list */
    Args* list;
};
typedef struct PikaObj_t PikaObj;
```
PikaObj内部维护了一个参数表，参数表中包含了属性信息、类信息、方法信息等。
**注意不要直接访问PikaObj内部的参数表**，请使用对象API访问PikaObj。这是因为对象API作为对外接口，是长期稳定的，而内部实现则会随着内核代码的迭代经常变动，**直接操作PikaObj内部将极大损失后向兼容性。**
## 4. 对象属性API
这一部分API提供了对Python对象属性的访问。
### 基本类型的属性
PikaObj支持**整形、浮点型、指针、字串**四种基本类型的属性。使用set和get方法即可读写一个对象的属性。
​

PikaObj的对象是**动态**的，因此可以随时为对象新增新的属性（静态对象的属性在构造时确定）。
​

基本类型属性的API有如下这些：
```c
/* set API */
int32_t obj_setInt(PikaObj* self, char* argPath, int64_t val);
int32_t obj_setPtr(PikaObj* self, char* argPath, void* pointer);
int32_t obj_setFloat(PikaObj* self, char* argPath, float value);
int32_t obj_setStr(PikaObj* self, char* argPath, char* str);
/* get API */
void* obj_getPtr(PikaObj* self, char* argPath);
float obj_getFloat(PikaObj* self, char* argPath);
char* obj_getStr(PikaObj* self, char* argPath);
int64_t obj_getInt(PikaObj* self, char* argPath);
```
基本类型属性的命名方式为obj_set[Type]和obj_get[Type]。
​


1. 第一个输入参数为要操作的对象指针。
1. 第二个输入参数为属性名/属性地址。

PikaObj支持对象嵌套，可以访问子对象的属性，在访问子对象属性时，第二个参数为属性地址，在访问本对象的属性时，第二个值为属性名。
```c
// set an Int type arg, the arg name is "a".
obj_setInt(self, "a", 1);
// set an Int type arg for subObjcet , the arg path is "subObj.a".
obj_setInt(self, "subObj.a", 1);
```

3. set方法的第三个输入参数为写入的属性值，get方法的返回值为读取的属性值。
3. set方法的返回值为错误码，为0表示无错误发生。
### 泛型属性
PikaObj支持泛型属性，同样提供set方法和get方法。输入参数和返回值与基本类型相似。
```c
int32_t obj_setArg(PikaObj* self, char* argPath, Arg* arg);
Arg* obj_getArg(PikaObj* self, char* argPath);
```
泛型属性在使用时需要转换为基本类型。
​

使用以下API可以判断泛型属性的当前类型。
```c
ArgType arg_getType(Arg* self);
```
使用以下的API可以将泛型属性转换为基本类型。
```c
int64_t arg_getInt(Arg* self);
float arg_getFloat(Arg* self);
void* arg_getPtr(Arg* self);
char* arg_getStr(Arg* self);
```
### 属性管理

1. 判断一个属性是否存在，返回值为1表示存在。
```c
int32_t obj_isArgExist(PikaObj* self, char* argPath);
```

2. 删除一个属性
```c
int32_t obj_removeArg(PikaObj* self, char* argPath);
```
返回值为错误码，为0表示成功。
## 5. 对象方法API
对象方法API分为方法注册和方法调用两部分，**方法注册部分由预编译器代理**，模块开发者只需要使用方法调用API即可。
### 方法调用API
```c
void obj_run(PikaObj* self, char* cmd);
```
obj_run是一个万能的API，可以直接运行Python脚本，并且支持多行脚本。
第一个入口参数是对象的指针，第二个入口参数是字符串形式的Python脚本。
要注意的是，传入多行脚本时，应当传入完整的代码块。
## 6. 抛出异常
可以在模块中使用obj_setErrorCode抛出异常，用户可以自定义异常处理方法（继续运行或停止运行）。
抛出异常通常在C模块的方法中使用，传入当前方法的self对象指针即可，errCode设置为非零即可触发异常。
obj_setSysOut方法常配合obj_setErrorCode方法使用，用于提供调试信息，该调试信息会在异常触发时显示在终端。
```c
/* set Error Code, if the errCode is not 0, an exaption would be throw out */
void obj_setErrorCode(PikaObj* self, int32_t errCode);
/* print out exaption infomation */
void obj_setSysOut(PikaObj* self, char* str);
```
