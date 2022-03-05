# PikaStdDevice 标准设备

PikaStdDevice 是一个抽象的设备模型，提供了跨平台的统一外设 API 。
## 安装

1. 在 requestment.txt 中加入 PikaStdDevice 的依赖。
```
PikaStdDevice==v1.4.3
```

2. 运行 pikaPackage.exe
## 为什么要有标准设备模块
什么是标准设备模块呢？我们先从其他的脚本技术说起，比如 MicroPython，并没有统一的外设调用 API，这使得用户在使用不同的平台时，都需要重新学习 API，比如下面这个是 MicroPython 在 STM32F4 平台驱动 GPIO 的代码。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495380966-02a52d33-9986-401c-a7e1-136ce71ad53e.webp)
这个是 ESP8266 的
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381179-e6afcca5-7f32-4a2f-a531-10f6b106db15.webp)
可以明显看到在选择 pin 的管脚时，一个用的是字符串，而另一个用的是整型数，控制电平时，一个使用 `high()`，`low()`方法，而另一个使用`on()`，`off()`方法，总之驱动的API标准很混乱。
有没有什么办法，能够统一外设的 API，使得用户只需要熟悉一套 API，就能够在任意平台通用呢？
方法是有的，就是 PikaStdDevice 标准设备驱动模块。
## 模块结构
![image.png](assets/1638681382807-901fa254-8323-4a9b-92ef-4e5b6e8ad5f9.png)
PikaStdDevice 是一个抽象的设备驱动模块，定义了所有的用户 API，各个平台的驱动模块只要从PikaStdDevice 继承，就能够获得一模一样的用户 API，而 PikaStdDevice 内部会间接调用平台驱动，通过多态特性重写底层的平台驱动，就可以在不同的平台工作了。
## 模块示例
以 GPIO 模块为例，以下是 PikaStdDevice 定义的用户 API
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381064-51409a36-812a-48ea-a6ae-23b3c177582d.webp)​
以下是 PikaStdDevice 需要重写的平台驱动
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381214-1189c3eb-28ef-408e-a21e-e6bbc594d6fb.webp)
而我们要制作的 CH32V103 的 GPIO 模块，就从标准驱动模块中继承。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381703-8e227dcc-97d7-4069-8754-4c118deea3fb.webp)​
通过这个方法，我们就可以让 STM32 的驱动模块、CH32 的驱动模块、ESP32 的驱动模块有着一模一样的用户 API。用户只要熟悉了一套 API，就可以轻松使用支持了 PikaScript 标准驱动模块的所有平台。
下面是部分被注册在驱动模块里面 C 原生驱动函数
![](assets/1638495381557-21aaad62-bd63-40bc-b818-257e16992780.webp)


