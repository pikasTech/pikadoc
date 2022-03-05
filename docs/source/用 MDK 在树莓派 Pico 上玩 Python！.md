# 用 MDK 在树莓派 Pico 上玩 Python

我们知道树莓派Pico玩Python可以直接使用MicroPython的固件，但是Micropython的固件开发难度很大，如果你想要自己绑定C模块很麻烦，需要依赖大量linux生态下的工具，而且很难调试。

但是树莓派Pico的硬件资源和售价真的很香，pio等特性也极具可玩性，那么，能不能在我们熟悉的平台，用接地气的开发方法，比如在MDK中，开发树莓派Pico呢？当然可以，隆重请出“傻孩子”大佬的Pico_template，可以让你在熟悉的MDK中开发树莓派pico，还支持免调试器单步调试（用一个核调试另一个）。

了解详情可以看：

【独家】我就要用MDK来开发树莓派Pico，怎么地吧！
GorgonMeducer 傻孩子，公众号：裸机思维[【独家】我就要用MDK来开发树莓Pico，怎么地吧！](http://mp.weixin.qq.com/s?__biz=MzAxMzc2ODMzNg==&mid=2656103324&idx=1&sn=f1d3ece87c81eeaa7d402f3cba60dc8f&chksm=8039c863b74e4175edc806b4e329c25e75b6372df53f07565bd9a46cfbf13a3c4cd9e20c08cc#rd)
​

MicroPython绑定C模块很复杂，很难调试，有没有更方便的技术，可以很简单地绑定C模块呢？
有的，那就是PikaScript，PikaScript是一个完全重写的超轻量级python引擎，零依赖，零配置，可以在少于4KB的RAM下运行，具有框架式C模块开发工具，只要用Python写好调用API，就能够自动连接到C模块，非常方便快捷。不用手动处理任何全局表、宏函数、模块注册等等过程。
而且PikaScript也支持MDK开发，能够轻松地调试C模块。
​

了解详情可以看：
【独家】我就要用最便宜的单片机来跑python，还要用MDK开发，怎么地吧！
李昂1998，公众号：吉大仪电216小论坛[【独家】我就要用最便宜的单片机来跑python，还要用MDK开发，怎么地吧！](http://mp.weixin.qq.com/s?__biz=MzU4NzUzMDc1OA==&mid=2247484313&idx=1&sn=2749a27bba09b2fe9c7bc0ad4977c8a6&chksm=fdebd4f0ca9c5de6f9160d42c58aa5d5e072168752c826cbf82f700f1fc301b96a3aaf4cfcfd#rd)
​

除了pico之外，pikascript的易移植特性使其可以在非常多的平台上运行。
从stm32g0，stm32f1，到国产的ch32，apm32，cm32，还有平头哥的w801，博流的bl-706，统统支持。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1640497097904-f2b13577-44ee-4510-a7ce-e18dd01aaa20.webp#clientId=ueaf7376e-6f92-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=ue05bf978&margin=%5Bobject%20Object%5D&originHeight=1012&originWidth=938&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u554f52c7-6351-49ca-b881-1e6f930f52e&title=)
很火的ESP32C3，龙芯架构，还有这次的主角树莓派Pico。
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1640497097922-8490fdc1-ba88-48a4-888b-3859384ca650.webp#clientId=ueaf7376e-6f92-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u50b06e32&margin=%5Bobject%20Object%5D&originHeight=753&originWidth=1080&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ufb772967-0916-4763-a523-f4175fc0620&title=)
除了支持裸机，还支持rt-thread、vsf操作系统，linux操作系统。

并且与rt-thread深度融合，能够基于软件包支持rt-thread全系列BSP
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1640497097898-69cdc136-7b7a-4a8c-b79c-0650ae3f5111.webp#clientId=ueaf7376e-6f92-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u70957796&margin=%5Bobject%20Object%5D&originHeight=535&originWidth=701&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u6831ba37-5961-4959-a85a-20bd2bc85e3&title=)
下面进入正题，看看如何在树莓派pico上面用MDK开发，并玩上Python。
使用说明：
[https://gitee.com/Lyon1998/pikascript/tree/master/bsp/pico#pikascript-in-pico](https://gitee.com/Lyon1998/pikascript/tree/master/bsp/pico#pikascript-in-pico)
如果能在串口看到下面的信息，就说明运行成功了！
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1640497099248-1358725f-072c-4810-a999-c9d372575f19.webp#clientId=ueaf7376e-6f92-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u69dd38bd&margin=%5Bobject%20Object%5D&originHeight=434&originWidth=809&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ufe736105-d75e-489a-acef-1b1368d6cbe&title=)
Enjoy！
更多技术支持可以在论坛讨论~
https://whycan.com/f_55.html
![](https://cdn.nlark.com/yuque/0/2021/webp/22991477/1640497099365-67930749-d3a2-4f70-9320-73da30f72659.webp#clientId=ueaf7376e-6f92-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u001067b4&margin=%5Bobject%20Object%5D&originHeight=373&originWidth=1080&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=ueba0c39f-4a9b-4000-9d16-e0815cfc7cb&title=)
