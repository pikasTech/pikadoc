# 串口下载 Python 脚本 运行文件

串口下载 Python 脚本和交互式运行非常类似，仍然是使用 `obj_run` 内核 API 进行脚本的运行。和交互式运行不同的是，下载 Python 脚本还需要对python脚本进行 **存储**。


`obj_run` 支持运行字符串形式的 Python 脚本，因此无论以哪种方式存储，只要最后给 `obj_run` 传入 Python 脚本的字符串即可。所以可以的存储方式有：**flash 直接存储、文件系统、外部存储器** 等。

PikaScript 支持运行 Python 脚本源码，和解析后的 Pika 字节码。

## 存储 Python 源码

存储 Python 源码很简单，将串口接收到的 Python 脚本字符串完整写入 Flash 即可。启动时不使用 `pikaScriptInit()` 函数，而是手动创建 `pikaMain` 根对象，再使用 `obj_run(pikaMain, code)` 运行脚本，`code` 代表的是存储好的 `python` 源码。

具体代码案例可以参考：

1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/main.c](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/main.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/pika_config.c](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/pika_config.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/pika_bsp.h](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g070cb/Booter/pika_bsp.h)

## 存储Pika字节码

具体代码案例可以参考：

1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/main.c](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/main.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/pika_config.c](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/pika_config.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/pika_bsp.h](https://gitee.com/Lyon1998/pikascript/blob/master/bsp/stm32g030c8/Booter/pika_bsp.h)

## 使用文件系统运行文件

当 MCU 已经移植了文件系统，那么可以使用文件 API 直接运行 Python 脚本文件。

[注意]：需要内核版本 >= v1.10.0

需要通过重写 WEAK 函数对接以下文件系统的文件 API：

``` C
/* fopen */
PIKA_WEAK FILE* __platform_fopen(const char* filename, const char* modes);

/* fclose */
PIKA_WEAK int __platform_fclose(FILE* stream);

/* fwrite */
PIKA_WEAK size_t __platform_fwrite(const void* ptr,
                                   size_t size,
                                   size_t n,
                                   FILE* stream);

/* fread */
PIKA_WEAK size_t __platform_fread(void* ptr,
                                  size_t size,
                                  size_t n,
                                  FILE* stream);
```

使用 `pikaVM_runSingleFile` 即可运行一个单独的 Python 文件 (不能 import 其他文件)。

函数原型：

``` C
VMParameters* pikaVM_runSingleFile(PikaObj* self, char* filename);
```

使用 `pikaVM_runFile` 可运行 Python 文件及其 `import` 的文件。需要在运行的 Python 文件的同级路径下新建一个 `pikascript-api` 文件夹，用于存放中间文件。

函数原型：

``` C
VMParameters* pikaVM_runFile(PikaObj* self, char* file_name);
```
