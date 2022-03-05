# 串口下载 Python 脚本 运行文件

串口下载 Python 脚本和交互式运行非常类似，仍然是使用 obj_run 内核 API 进行脚本的运行。和交互式运行不同的是，下载 Python 脚本还需要对python脚本进行**存储**。
​

obj_run 支持运行字符串形式的 Python 脚本，因此无论以那种方式存储，只要最后给 obj_run 传入 Python 脚本的字符串即可。所以可以的存储方式有：**flash 直接存储、文件系统、外部存储器**等。


PikaScript 支持运行 Python 脚本源码，和解析后的 Pika 字节码。
## 1. 存储 Python 源码
存储 Python 源码很简单，将串口接收到的 Python 脚本字符串完整写入 Flash 即可。启动时不使用pikaScriptInit() 函数，而是手动创建 pikaMain 根对象，再使用 obj_run(pikaMain, code) 运行脚本，code 代表的是存储好的 python 源码。


具体代码案例可以参考：

1. [https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/main.c](https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/main.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/pika_config.c](https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/main.c)
1. [https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/pika_config.h](https://gitee.com/Lyon1998/pikascript/blob/master/package/STM32G030Booter/main.c)
## 2. 存储Pika字节码
（待完善）
具体代码案例可以参考：

1. package/STM32G030Booter/main.c
1. package/STM32G030Booter/pika_config.c
1. package/STM32G030Booter/pika_config.h
