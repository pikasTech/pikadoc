# keil 仿真工程

在本篇中，你将可以在手边没有硬件的情况下对 pikascript 进行上手测试。
测试使用 keil5 的仿真工程，仿真目标板为 stm32f103 ，下载仿真工程即可直接开始测试。
### 创建工程
进入 pikascript 官网 [http://pikascript.com](http://pikascript.com)
选择 simulation-keil，然后点击“开始生成”
![image.png](https://cdn.nlark.com/yuque/0/2022/png/22991477/1644128841425-378e4391-426d-4dc3-bb2d-934e8facd22e.png)
解压下载的 zip 压缩包，打开工程
![](https://user-images.githubusercontent.com/88232613/130745821-864038df-d8b0-41d2-97e8-199815d0d57d.png#crop=0&crop=0&crop=1&crop=1&id=bvV6n&originHeight=873&originWidth=920&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)


### 运行仿真工程
选择使用仿真器进行调试
![](https://user-images.githubusercontent.com/88232613/130747706-b912e09f-3f68-495a-a69f-f8f7500b1e4e.png#crop=0&crop=0&crop=1&crop=1&id=uluci&originHeight=490&originWidth=1446&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)


编译工程然后进入调试
![](https://user-images.githubusercontent.com/88232613/130747350-70ffa319-f04d-4f26-a75b-61864a19b8d8.png#crop=0&crop=0&crop=1&crop=1&id=wl3IA&originHeight=317&originWidth=1448&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
打开串口显示面板
![](https://user-images.githubusercontent.com/88232613/130747952-42073ba1-c4c4-4acb-9495-766cd5731374.png#crop=0&crop=0&crop=1&crop=1&id=BSGKN&originHeight=950&originWidth=1450&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
运行然后查看输出结果
![](https://user-images.githubusercontent.com/88232613/130748221-53fff9f6-6427-417d-b95a-3fa52a57eeaf.png#crop=0&crop=0&crop=1&crop=1&id=WWfzW&originHeight=975&originWidth=1461&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
### 改改脚本看看
用任意编辑器打开 main.py ，推荐 vscode ， 没有 vscode 用记事本打开也可以
![](https://user-images.githubusercontent.com/88232613/130748847-477facfb-e16e-4e0e-8876-d66efd0ae48c.png#crop=0&crop=0&crop=1&crop=1&id=q7ZRQ&originHeight=845&originWidth=834&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
以下就是 main.py
```python
# main.py
from PikaObj import  *
import Device
import PikaStdLib 

led = Device.LED()
uart = Device.Uart()
mem = PikaStdLib.MemChecker()

print('hello wrold')
uart.setName('com1')
uart.send('My name is:')
uart.printName()
print('mem used max:')
mem.max()
print('mem used now:')
mem.now()
```
这个脚本使用标准的 python3 语法，那么如何让这个脚本在单片机里运行呢？
​

事实上，pikascript 虽然使用 python 语法，但原理上更像是 java，是半编译半解释型的，pikascript 的类和方法是需要编译的，而方法调用和对象新建/销毁则是在运行时解释的。
​

编译 pikascript 分为两步，第一步是使用 pikascript 预编译器将 .py 文件编译为 pikascript-api 中的 .c 和 .h 文件。


第二步是使用 c 编译器编译所有的 c 文件，然后下载到单片机里即可。


双击 rust-msc-v0.5.0.exe 运行 pika 预编译器，值得一提的是，这个预编译器是使用 rust 语言编写的。
![](https://user-images.githubusercontent.com/88232613/130749341-d12b7985-3685-419c-b9b8-8a09ae6f73d3.png#crop=0&crop=0&crop=1&crop=1&id=OF9No&originHeight=349&originWidth=835&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
为了验证编译的效果，我们可以先把 pikascript-api 文件夹里的文件全部删除，然后再运行编译器，看看能不能自动生成 pikascript-api 里面的 .c,.h文件。


注意不要把 pikascript-api 文件夹给删掉了，只删除里面的文件即可。


下面就是 pikascript-api 生成的 .c,.h 文件
![](https://user-images.githubusercontent.com/88232613/130750476-eaffce03-caeb-40b3-9841-550034fa191a.png#crop=0&crop=0&crop=1&crop=1&id=dMnmQ&originHeight=666&originWidth=793&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
接下来我们来修改一下 main.py 看看效果
```python
from PikaObj import  *
import Device
import PikaStdLib 

led = Device.LED()
uart = Device.Uart()
mem = PikaStdLib.MemChecker()

print('hello wrold')
uart.setName('com1')
uart.send('My name is:')
uart.printName()
print('mem used max:')
mem.max()
print('mem used now:')
mem.now()

# new code start
print('add new code start')
uart.setName('com2')
uart.printName()
print('add new code end')
# new code end
```
我们在 main.py 下面新加了4行脚本，我们来编译运行看看效果。
编译 pikascript-api
![](https://user-images.githubusercontent.com/88232613/130751195-40944d60-7d56-48a9-9f47-cab87d77d5a8.png#crop=0&crop=0&crop=1&crop=1&id=lKWmk&originHeight=386&originWidth=812&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
编译 keil 工程然后进入调试
![](https://user-images.githubusercontent.com/88232613/130751539-aa0bdb82-750f-4f98-8f6f-02d653dda64a.png#crop=0&crop=0&crop=1&crop=1&id=LkL2a&originHeight=261&originWidth=1463&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
运行然后观察输出
![](https://user-images.githubusercontent.com/88232613/130751653-cad627c2-367c-45a6-8c5f-686c7514df3c.png#crop=0&crop=0&crop=1&crop=1&id=Y2gPs&originHeight=944&originWidth=1465&originalType=binary&ratio=1&rotation=0&showTitle=false&status=done&style=none&title=)
我们发现多了3行输出，说明编译运行顺利。
好了，到这里 pikaScript 的三分钟快速上手就结束了。


[

](./3.PikaScript%E6%A0%87%E5%87%86%E5%BC%80%E5%8F%91%E6%B5%81%E7%A8%8B.md)
