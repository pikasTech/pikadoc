# C 可变参数

C 模块支持可变参数，使用 `*xxx` 的输入参数即可，在 C 层会将任意个数的参数打包进 `PikaTuple` 数据类型中，使用 `tuple_getSize()` 可以获得可变参数的个数，使用 `tuple_getArg()` 可以根据可变参数的位置得到 `arg`。



[注意] 

- 需要内核版本 >= v1.10.0

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

