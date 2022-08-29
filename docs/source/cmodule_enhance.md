# C 模块可变参数

C 模块支持可变参数，使用 `*xxx` 的输入参数即可，在 C 层会将任意个数的参数打包进 `PikaTuple` 数据类型中，使用 `tuple_getSize()` 可以获得可变参数的个数，使用 `tuple_getArg()` 可以根据可变参数的位置得到 `arg`。


[注意] 

- 需要内核版本 `>= v1.10.0`

- 可变参数必须放在位置参数的后面

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

直接在 .pyi 中定义 `__init()__` 函数即可执行模块初始化，在模块载入时会触发执执行，PikaScript 具有模块延时加载机制，`import` 不会直接触发模块加载，仅仅在第一次真正使用模块时，才会触发加载。

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
```

