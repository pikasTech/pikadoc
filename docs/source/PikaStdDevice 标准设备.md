PikaStdDevice 是一个抽象的设备模型，提供了跨平台的统一外设 API 。
## 安装

1. 在 requestment.txt 中加入 PikaStdDevice 的依赖。
```
PikaStdDevice==v1.4.3
```

2. 运行 pikaPackage.exe
## 为什么要有标准设备模块
什么是标准设备模块呢？我们先从其他的脚本技术说起，比如 MicroPython，并没有统一的外设调用 API，这使得用户在使用不同的平台时，都需要重新学习 API，比如下面这个是 MicroPython 在 STM32F4 平台驱动 GPIO 的代码。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495380966-02a52d33-9986-401c-a7e1-136ce71ad53e.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=188&id=ubd899c44&margin=%5Bobject%20Object%5D&originHeight=234&originWidth=398&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uc6136c79-2878-474f-ab2e-c2a2d44cafc&title=&width=320)
这个是 ESP8266 的
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381179-e6afcca5-7f32-4a2f-a531-10f6b106db15.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=246&id=u7fb6ebb1&margin=%5Bobject%20Object%5D&originHeight=357&originWidth=784&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u376e2aa7-35df-4e57-91f7-8e3e17df0e7&title=&width=541)
可以明显看到在选择 pin 的管脚时，一个用的是字符串，而另一个用的是整型数，控制电平时，一个使用 `high()`，`low()`方法，而另一个使用`on()`，`off()`方法，总之驱动的API标准很混乱。
有没有什么办法，能够统一外设的 API，使得用户只需要熟悉一套 API，就能够在任意平台通用呢？
方法是有的，就是 PikaStdDevice 标准设备驱动模块。
## 模块结构
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638681382807-901fa254-8323-4a9b-92ef-4e5b6e8ad5f9.png#clientId=u6816b2ec-184f-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=490&id=u1c4c9e48&margin=%5Bobject%20Object%5D&name=image.png&originHeight=979&originWidth=2234&originalType=binary&ratio=1&rotation=0&showTitle=false&size=143479&status=done&style=none&taskId=u7eb909de-24c1-4532-8fc7-8f2048a7aee&title=&width=1117)
PikaStdDevice 是一个抽象的设备驱动模块，定义了所有的用户 API，各个平台的驱动模块只要从PikaStdDevice 继承，就能够获得一模一样的用户 API，而 PikaStdDevice 内部会间接调用平台驱动，通过多态特性重写底层的平台驱动，就可以在不同的平台工作了。
## 模块示例
以 GPIO 模块为例，以下是 PikaStdDevice 定义的用户 API
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381064-51409a36-812a-48ea-a6ae-23b3c177582d.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=413&id=u5d68e5c8&margin=%5Bobject%20Object%5D&originHeight=868&originWidth=1080&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u939cee7c-97cb-42ec-b6fd-e567c96ed70&title=&width=514)​
以下是 PikaStdDevice 需要重写的平台驱动
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381214-1189c3eb-28ef-408e-a21e-e6bbc594d6fb.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=706&id=ud4d18db3&margin=%5Bobject%20Object%5D&originHeight=869&originWidth=598&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u2aea0733-f96f-4f6d-948e-9c565ad9bb0&title=&width=486)
而我们要制作的 CH32V103 的 GPIO 模块，就从标准驱动模块中继承。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381703-8e227dcc-97d7-4069-8754-4c118deea3fb.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=475&id=u75555419&margin=%5Bobject%20Object%5D&originHeight=956&originWidth=1080&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uc3e23147-d0b9-47af-ab47-133d6b19509&title=&width=537)​
通过这个方法，我们就可以让 STM32 的驱动模块、CH32 的驱动模块、ESP32 的驱动模块有着一模一样的用户 API。用户只要熟悉了一套 API，就可以轻松使用支持了 PikaScript 标准驱动模块的所有平台。
下面是部分被注册在驱动模块里面 C 原生驱动函数
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1638495381557-21aaad62-bd63-40bc-b818-257e16992780.webp#clientId=u35f47dbf-87ab-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=533&id=ubc061889&margin=%5Bobject%20Object%5D&originHeight=671&originWidth=768&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u89d468d0-edc6-48a4-8f3b-4bb315164ca&title=&width=610)


