# C 模块可变参数

C 模块支持可变参数，使用 `*xxx` 的输入参数即可，在 C 层会将任意个数的参数打包进 `PikaTuple` 数据类型中，使用 `tuple_getSize()` 可以获得可变参数的个数，使用 `tuple_getArg()` 可以根据可变参数的位置得到 `arg`。同样支持 `tuple_get<Type>` api，直接得到指定类型的值。


[注意] 

- 需要内核版本 `>= v1.10.0`

- 如何可变参数和位置参数同时存在，则可变参数必须放在位置参数的后面

示例：

``` python
# test.pyi
def vals(a:int, *val):...
```

``` C
// test.c
void test_vals(PikaObj* self, int a, PikaTuple* val){
    printf("a: %d\n", a);
    for(int i =0; i< tuple_getSize(val); i++){
        Arg* arg_i = tuple_getArg(val, i);
        printf("val[%d]: %d\n", i, arg_getInt(arg_i));
    }
}
```

输出结果:

```python
>>> test.vals(1, 2, 3, 4)
a: 1
val[0]: 2
val[1]: 3
val[2]: 4
>>>
```

# C 模块关键词参数

C 模块支持关键词参数，使用 `**xxx` 的输入参数即可，在 C 层会将任意个数的参数打包进 `PikaDict` 数据类型中，使用 `dict_getArg()` 可以根据关键词得到 `arg`。同样支持 `dict_get<Type>()` api, 直接得到指定类型的值。


[注意] 

- 需要内核版本 `>= v1.10.7`

- 关键词参数必须放在位置参数和可变参数的后面

示例：

``` python
# test.pyi
def keys(a:int, **keys):...
```

``` C
// test.c
void test_keys(PikaObj* self, int a, PikaDict* keys){
    printf("a: %d\n", a);
    printf("keys['b']: %d\n", i, dict_getInt(keys, "b"));
    printf("keys['c']: %d\n", i, dict_getInt(keys, "c"));
}
```

输出结果:

```python
>>> test.keys(1, b=2, c=3)
a: 1
keys['b']: 2
keys['c']: 3
>>>
```

# C 模块返回 List/Dict

## List

``` python
# test.pyi
def test_list()->list:...
```

``` C
// test.c
#include "PikaStdData_List.h"
PikaObj* test_test_list(PikaObj* self){
    /* 创建 list 对象 */
    PikaObj* list = newNormalObj(New_PikaStdData_List);
    /* 初始化 list */
    PikaStdData_List___init__(list);
    /* 用 arg_new<type> 的 api 创建 arg */
    Arg* str_arg1 = arg_newStr("aaa");
    /* 添加到 list 对象 */
    PikaStdData_List_append(list, str_arg1);
    /* 销毁 arg */
    arg_deinit(str_arg1);
    /* 返回列表 */
    return list;
}
```

## Dict

注意：需要内核版本 `>= v1.10.8`

``` python
# test.pyi
def test_dict()->dict:...
```

``` C
// test.c
#include "PikaStdData_Dict.h"
PikaObj* test_test_dict(PikaObj* self){
    PikaObj* dict = newNormalObj(New_PikaStdData_Dict);
    PikaStdData_Dict___init__(dict);
    Arg* para1 = arg_newInt(1);
    Arg* para2 = arg_newInt(2);
    PikaStdData_Dict_set(dict, "para1", para1);
    PikaStdData_Dict_set(dict, "para2", para2);
    arg_deinit(para1);
    arg_deinit(para2);
    return dict;
}
```

# C 模块常量

C 模块支持在类中或模块中加入常量，可以使用 `val:type` 的语法，这些常量需要在初始化时赋值，因此需要定义 `__init__()` 方法，例如：

```python
class cJSON:
    cJSON_Invalid: int
    cJSON_False: int
    def __init__(self):...
    ...
```

```c
void pika_cjson_cJSON___init__(PikaObj* self) {
    /* const value */
    obj_setInt(self, "cJSON_Invalid", cJSON_Invalid);
    obj_setInt(self, "cJSON_False", cJSON_False);
	...
}
```

这些常量可以不创建对象直接使用，即当作类属性来使用。

```python
print(cJSON.cJSON_Invalid)
```

需要注意的是，PikaScript 的类属性是只读的，对类属性的所有修改都是无效的。

# C 模块初始化

直接在 .pyi 中定义 `__init__()` 函数即可执行模块初始化，在模块载入时会触发执行，PikaScript 具有模块延时加载机制，`import` 不会直接触发模块加载，仅仅在第一次真正使用模块时，才会触发加载。

例如:

```python
# test.pyi
def __init__():...
def hello():...
```

``` c
//test.c
void test___init__(PikaObj* self){
    printf("now loading module test...\n");
}

void test_hello(PikaObj* self){
    printf("hello!\n");
};
```

``` python
# main.py
import test
print('before run test.hello()')
test.hello()
print('after run test.hello()')
```

输出：

```
before run test.hello()
now loading module test...
hello!
after run test.hello()
```

