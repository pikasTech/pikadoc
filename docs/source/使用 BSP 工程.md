# 使用 BSP 工程
## 1. 创建工程
进入 pikascript 官网 [http://pikascript.com](http://pikascript.com)
选择平台，模块，然后点击 "开始生成"。
（选择平台后会自动选择默认的模块)
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22991477/1644129110261-049ad5bb-21af-40e2-9533-a1c8c86790f1.png#clientId=ud8f924e7-b341-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=671&id=u7a239101&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1174&originWidth=887&originalType=binary&ratio=1&rotation=0&showTitle=false&size=146959&status=done&style=none&taskId=ub307287a-b2cc-40c1-abcd-76c1ca0a625&title=&width=506.85714285714283)
## 2. 工程的来源
移植好的裸机MCU工程在pikascript/bsp目录，里面的每一个文件夹都是一个移植好的裸机工程。
**每个工程都是独立的，可以拷贝出pikascript仓库单独使用。**
（simulation-keil-dev和pico是列外，这两个bsp只能在仓库里面用，是用来开发内核的。）
[https://gitee.com/Lyon1998/pikascript/tree/master/bsp](https://gitee.com/Lyon1998/pikascript/tree/master/bsp)
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638605947761-93b30636-099f-4c7c-a432-6aae5e2d8b53.png#clientId=u1f653719-4dd4-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=256&id=u46da1803&margin=%5Bobject%20Object%5D&name=image.png&originHeight=984&originWidth=2028&originalType=binary&ratio=1&rotation=0&showTitle=false&size=146222&status=done&style=none&taskId=u2c1d9a47-9e15-4b66-9f43-2d525e5c35f&title=&width=528)
## 3. 支持列表
在bsp文件夹的README.md中，标注了目前的平台支持情况和bsp的使用方法。
（以下的表格不是最新的）
[最新表格点这里](https://gitee.com/Lyon1998/pikascript#2%E5%B9%B3%E5%8F%B0%E6%94%AF%E6%8C%81%E5%88%97%E8%A1%A8)
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639629972025-ca8fdf74-5dc2-472e-8497-5bc163bccdf4.png#clientId=ub4f5b7e7-1daa-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=410&id=u99328c28&margin=%5Bobject%20Object%5D&name=image.png&originHeight=855&originWidth=792&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59120&status=done&style=none&taskId=u0c0dd159-00a1-4ca9-9393-0fd0a7ad3c3&title=&width=380)
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639629981607-43c6b771-34bf-45ac-9a66-8604f705ddff.png#clientId=ub4f5b7e7-1daa-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=205&id=ufa0c559b&margin=%5Bobject%20Object%5D&name=image.png&originHeight=474&originWidth=1075&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30721&status=done&style=none&taskId=u3d6cec82-1f3a-4bd1-9d5c-1ce030fbb2b&title=&width=465.5)
你可以通过贡献**驱动模块**或者**bsp**来帮助PikaScript拓展这个表格，具体请参考文档中的**新平台移植指南**、**模块开发**和**包管理**部分。
## 4. 工程结构
以CH32V103为例，一个PikaScript的工程包含以下的几个部分。
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638631568309-cbc19553-75be-4915-900a-72fe700b4d16.png#clientId=u1584620a-be5e-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=324&id=u781912f3&margin=%5Bobject%20Object%5D&name=image.png&originHeight=630&originWidth=909&originalType=url&ratio=1&rotation=0&showTitle=false&size=32332&status=done&style=none&taskId=u410b192b-efc2-4bdd-9b83-da9ad093344&title=&width=468)

1. 首先是BSP文件夹中除了PikaScript文件夹以外的部分，这一部分是真正的BSP，包含了厂家提供的基本外设库、CMSIS等一些平台上的通用库，只需要对厂家的例程进行整理就可以得到。

​


2. 上面的一部分是PikaScript的启动器，包含main.c入口文件，pika_config.c配置文件，还有*.s汇编启动文件。启动器负责支持printf，堆栈设置，PikaScript的启动，以及交互式运行、串口下载Python等一些功能。

**pika_config.c是用于支持串口下载Python等一些高级功能的，没有这个文件PikaScript依然可以运行。**
​


3. 再上面就是PikaScript的主要部分了，分为内核和模块两个部分，内核就是pikascript/src中的文件，选择一个版本全部添加编译即可，**不需要任何的修改。**



4. **​**模块部分是可以自己开发，或者从仓库中拉取的，**PikaStdLib标准库模块是必选的。**其他模块是可选的。

关于如何使用模块以及如何制作模块，请参考**模块开发**部分，关于如何贡献模块到PikaScript参考，请参考**如何贡献PikaScript模块**部分。
​


5. 最上层是PikaScript工程能够支持的Python脚本，Python脚本可以直接解释运行，加载脚本的方式有多种，包括**预编译进固件、交互式运行、串口下载Python脚本**等，预编译进固件可以参考**模块开发**的部分，交互式运行和串口下载可以参考**新平台移植**的部分。

**只有在main.py中import的模块会被编译进固件，**因此main.py还可以起到**剪裁模块**的作用。
## 5. 模块管理
**启动器、内核和模块都可以使用包管理器进行管理。**
因此BSP中的PikaScript文件夹中只包含包管理器**pikaPackage.exe**本身，**requestment.txt**模块描述文件和**main.py**示例脚本三个文件。
​

requestment.txt使用与通用python一样的模块描述语法，直接运行pikaPackage.exe就可以识别当前文件夹下的requestment.txt然后拉取相应的模块。
​

以stm32g030的bsp中的requestment.txt为例，被拉取的模块有：

1. 内核： pikascript-core
1. 标准库： PikaStdLib
1. 启动器：STM32G030Booter
1. 外设模块： STM32G0 PikaPiZero PikaStdDevice
```
pikascript-core==v1.2.6
PikaStdLib==v1.2.1
PikaStdDevice==v1.4.2
PikaPiZero==v1.1.2
STM32G030Booter==v1.2.5
STM32G0==v1.0.2
```
拉取后的模块需要预编译，直接运行rust-msc-latest-win10.exe即可。
## 6. 注意事项

1. Keil版本**强烈建议**不低于**5.36**

![O(DF$DRTP13}EI88JNQRUTF.png](https://cdn.nlark.com/yuque/0/2022/png/22991477/1641372084863-db6426eb-b3cc-454d-b14a-5338818d01aa.png#clientId=u864f7269-941d-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=450&id=ue31babc1&margin=%5Bobject%20Object%5D&name=O%28DF%24DRTP13%7DEI88JNQRUTF.png&originHeight=861&originWidth=787&originalType=binary&ratio=1&rotation=0&showTitle=false&size=237043&status=done&style=none&taskId=u05c8de03-d4b1-497b-b392-bf4ef98b049&title=&width=411)
