# PikaStdDevice 标准设备

PikaStdDevice 是一个抽象的设备模型，提供了跨平台的统一外设 API 。

## 安装

- 在 requestment.txt 中加入 PikaStdDevice 的依赖。
```
PikaStdDevice
```

- 运行 pikaPackage.exe
## 为什么要有标准设备模块
什么是标准设备模块呢？我们先从其他的脚本技术说起，比如 MicroPython，并没有统一的外设调用 API，这使得用户在使用不同的平台时，都需要重新学习 API，比如下面这个是 MicroPython 在 STM32F4 平台驱动 GPIO 的代码。

![](assets/1638495380966-02a52d33-9986-401c-a7e1-136ce71ad53e.webp)

这个是 ESP8266 的

![](assets/1638495381179-e6afcca5-7f32-4a2f-a531-10f6b106db15.webp)

可以明显看到在选择 pin 的管脚时，一个用的是字符串，而另一个用的是整型数，控制电平时，一个使用 `high()`，`low()`方法，而另一个使用`on()`，`off()`方法，总之驱动的API标准很混乱。
有没有什么办法，能够统一外设的 API，使得用户只需要熟悉一套 API，就能够在任意平台通用呢？
方法是有的，就是 PikaStdDevice 标准设备驱动模块。

## 模块结构

![](assets/image-20221207125315706.png)

- `PikaStdDevice` 模块提供了 `GPIO`、`IIC`、`PWM` 等基础的外设 Python 模块。
- `PikaStdDevice` 基于 `pika_hal` 设备抽象层，`pika_hal`是一个纯 `c` 语言的设备抽象层，将不同平台的外设操作都统一为相同的 `API` 供 `PikaStdDevice` 调用，这样不同的平台 (STM32、ESP32、BL602) 等都可以使用通用的 `Python` 代码来控制设备了。
- `pika_hal` 设备抽象层需要在不同的平台进行适配 (Platform Port)，通过在不同的平台重写形如 `pika_hal_platform_xxxx()`  的 `WEAK` 函数，就可以为不同的平台提供支持。
- 除了 `PikaStdDevice` 模块之外，还有一些 `sensor` / `motor` 等 `Python` 模块，也基于 `pika_hal` 开发，这些模块使用的是 `pika_hal` 的 `GPIO`、`IIC`、`PWM` 等适配好的功能，所以只需要适配好 `pika_hal`就可以使用。

[关于 pika_hal 的详细介绍](pika_hal.html)

## `PikaStdDevice` 模块示例

以 GPIO 模块为例，以下是 PikaStdDevice 定义的用户 API

``` python
class GPIO:
    def __init__(self):
        pass

    def init(self):
        pass

    def setPin(self, pinName: str):
        pass

    def setId(self, id: int):
        pass

    def getId(self) -> int:
        pass

    def getPin(self) -> str:
        pass

    def setMode(self, mode: str):
        pass

    def getMode(self) -> str:
        pass

    def setPull(self, pull: str):
        pass

    def enable(self):
        pass

    def disable(self):
        pass

    def high(self):
        pass

    def low(self):
        pass

    def read(self) -> int:
        pass

```

`PikaStdDevice` 模块的示例代码在 [https://gitee.com/Lyon1998/pikapython/tree/master/examples/Device](https://gitee.com/Lyon1998/pikapython/tree/master/examples/Device) 路径下，示例中的 `machine` 模块是 `PikaStdDevice` 模块的简单重命名。
