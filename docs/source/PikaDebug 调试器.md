# PikaDebug 调试器

PikaDebug 调试器模块提供了断点调试等功能。
## 安装

1. 在 requestment.txt 中加入 PikaStdLib 的依赖，PikaStdLib 的版本号应当与内核的版本号相同。
```
PikaStdLib==v1.3.5
```

2. 运行 pikaPackage.exe
## 类
### class Debuger():
Debuger 类提供了调试器功能，由 Debuger 类创建对象，即可创建一个调试器。
#### Debuger 类的方法
```c
class Debuger(TinyObj):
    def __init__():
        pass

    def set_trace():
        pass
    
```
`__init__()`方法是创建对象时执行的方法，用户不需要了解。`set_trace()`方法可以在代码中放置一个断点，代码执行至断点处时会停止，并开启`(pika-debug)`终端，用户可以在终端中输入命令（c : 继续运行、q : 结束调试)，或者 python 交互式调用 ( `printf(i)`、`i = 10`）。
​

用例：
```python
import PikaDebug

pkdb = PikaDebug.Debuger()

i = 0
while i < 10:
    i = i + 1
    print('i :' + str(i))
    # set a breakpoint here
    pkdb.set_trace()
```
命令示例：
n：（next）继续运行至下一个断点。
q：（quit）退出调试模式，并继续运行。
p：（print) 打印变量，`p i`表示打印变量 `i`。
交互式运行：直接执行交互式命令，如`print(i)`，`i = 2`等。
```bash
# 调试记录示例
i :1
(pika-debug) n
i :2
(pika-debug) n
i :3
(pika-debug) n
i :4
(pika-debug) p i
4
(pika-debug) print(i)
4
(pika-debug) i = 2
(pika-debug) n
i :3
(pika-debug) n
i :4
(pika-debug) i = 9
(pika-debug) n
i :10
(pika-debug) i = 2
(pika-debug) n
i :3
(pika-debug) q
i :4
i :5
i :6
i :7
i :8
i :9
i :10
```
