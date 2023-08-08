# 事件回调机制

## 概述

PikaPython 内核中提供了事件回调机制，使得您可以在 C 的事件/中断中触发 Python 定义的回调函数。

> 注意
> 
> 需要内核版本不低于: `v1.12.5`

## 头文件

``` C
#include "PikaObj.h"
```

## 数据类型

```c
typedef PikaObj PikaEventListener;
```

事件回调机制主要依赖于 `PikaEventListener` 事件监听器。事件监听器会记录每个已注册的事件 ID。当信号发送至事件监听器时，事件监听器会根据事件 ID 调用相应的 Python 回调函数，并传递信号量。

## 事件模型

事件模型的核心是 `PikaEventListener` 事件监听器。

![](assets/image-20220619102931608.png)

`PikaEventListener` 的模型如上图所示

当您向事件监听器中注册事件后，它将在 `PikaEventListener` 内部记录一个事件项 `Event Item`，包括：

- Event ID 事件的唯一 ID
- Event Handler Object 事件对象，记录了事件项的全部信息
- Event CallBack 事件回调函数 ( Python 函数 )

当 `Event Signal` 事件信号到来时，事件监听器会匹配 `Event ID`，找到相应的事件项，然后将信号代码 Signal Code 传递给 Event CallBack，并触发回调函数

![](assets/image-20220619104053576.png)

## 事件机制的使用方式

### 创建事件监听器

在 C 中定义一个 PikaEventListener 的全局指针。

``` C
PikaEventListener* g_pika_user_listener;
```

### 在 C 模块中实现回调注册

在 `pyi` 中定义一个回调的注册函数

例如：

```python
# test.pyi
def setCallback(self, cb: any): ...
```

注意：

- 事件回调函数的类型注解是 `any`。

``` C
void test_setCallback(PikaObj* self, Arg* cb){
    /* 可以在注册时再初始化事件监听器 */
    if (NULL == g_pika_user_listener){
        pika_eventListener_init(&g_pika_user_listener);
    }
    /* 你需要通过某种方式来生成这个事件的 ID，后面要使用相同的 ID 来触发这个事件 */
    uint32_t eventId = ...;
    /* 将这个事件注册进监听器 */
    pika_eventListener_registEventCallback（g_pika_device_event_listener， eventId, cb);
}
```

### 在 Python 注册回调函数

- 定义一个回调函数 `callBack1`，接收一个输入参数 `signal`，`signal`能够接收传入的信号码。

[/examples/TemplateDevice/gpio_cb.py](https://gitee.com/Lyon1998/pikapython/blob/master/examples/TemplateDevice/gpio_cb.py)

``` python
import test

def callback1(signal):
	print('callback1, signal:', signal)

test.setCallback(callback1)
```


### 信号触发

在需要触发事件回调时向 `PikaEventListener` 发送信号。

- 通过 `pika_eventListener_sendSignal` 发送 `eventID` 和 `signal code`。 

```c
extern PikaEventListener* g_pika_device_event_listener;

...
	/* 通过某种方式来获得要触发的回调的 ID */
    uint32_t eventId = ...;
    /* 在需要触发回调的时候使用发送信号的函数 */
	uint32_t singalCode = 0;
    pks_eventLisener_sendSignal(g_pika_device_event_listener, eventId, singalCode);
	singalCode = 1;
    pks_eventLisener_sendSignal(g_pika_device_event_listener, eventId, singalCode);
...

```

- 运行结果：
```
callback1, signal: 0
callback1, signal: 1
```

### 等待返回值

事件回调函数可以有返回值，如直接返回 `signal + 1`。

``` Python
def callback1(signal):
    return signal + 1
```

这个功能需要 OS 的支持， 需要重写 `pika_platform_thread_yield()` 方法，才能够在等待返回值时调度到主进程执行事件。

如果需要返回值，触发事件可以使用 `pks_eventLisener_sendSignalAwaitResult` 获得回调函数的返回值，返回值是一个 `Arg*` 类型。

``` C
Arg* res_123 = pks_eventLisener_sendSignalAwaitResult(
        g_pika_device_event_listener, GPIO_PA8_EVENT_ID, 123);
int res = arg_getInt(res_123); // res = 124
```

