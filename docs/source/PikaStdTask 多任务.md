# PikaStdTask 多任务

PikaStdTask 多任务库提供了 Task （任务循环）的异步多任务功能。
## 安装

- 在 requestment.txt 中加入 PikaStdLib 的依赖，PikaStdLib 的版本号应当与内核的版本号相同。

```
PikaStdLib
```

- 运行 pikaPackage.exe

## class Task():
Task 类提供了任务循环功能，由 Task 类创建对象，即可创建一个任务循环。
### Task 类的方法
```python
import PikaStdData


class Task:
    calls = PikaStdData.List()

    def __init__(self):
        pass

    # regist a function to be called always
    def call_always(self, fun_todo: any):
        pass
    
    # regist a function to be called when fun_when() return 'True'
    def call_when(self, fun_todo: any, fun_when: any):
        pass

    # regist a function to be called periodically 
    def call_period_ms(self, fun_todo: any, period_ms: int):
        pass

    # run all registed function once
    def run_once(self):
        pass

    # run all registed function forever
    def run_forever(self):
        pass

    # run all registed function until time is up
    def run_until_ms(self, until_ms: int):
        pass

    # need be overried to supply the system tick
    def platformGetTick(self):
        pass

```
### 使用方法：

1. 使用 `call_xxx()` 方法指定调用的方式，并将要执行的函数注册进 task 对象中。
2. 使用 `run_xxx()` 方法指定任务循环执行的方式，并执行 `task` 对象中的所有函数。
3. 和时间相关的功能，如 `call_period_ms()` ，`run_until_ms()`需要提供系统时钟，提供的方式为新建一个继承自 `PikaStdTask`的类，然后重写`platformGetTick()`方法。
### 注意：

1. 所有被注册的函数应当是 **非阻塞** 的，否则会导致整个任务循环堵死。
2. 任务循环不是实时的。
### 用例：

- 新建继承自 `PikaStdTask`的类。
```python
# STM32G0.py
class Task(PikaStdTask.Task):
    # override
    def platformGetTick():
        pass
```

- 重写`platformGetTick()`方法。
```c
/* STM32G0_Task.c */

void STM32G0_Task_platformGetTick(PikaObj* self) {
    obj_setInt(self, "tick", HAL_GetTick());
}
```

- python 用例

``` python
import machine

import PikaStdLib

pin = machine.GPIO()
rgb = machine.RGB()
mem = PikaStdLib.MemChecker()

pin.setPin('PA8')
pin.setMode('out')
pin.enable()

rgb.init()
rgb.enable()

print('task demo')
print('mem used max:')
mem.max()


def rgb_task():
    rgb.flow()
    mem.now()


def led_task():
    if pin.read():
        pin.low()
    else:
        pin.high()


task = machine.Task()

task.call_period_ms(rgb_task, 50)
task.call_period_ms(led_task, 500)

task.run_forever()

```
