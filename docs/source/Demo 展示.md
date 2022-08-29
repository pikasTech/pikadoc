# Demo 展示

我就想用单片机跑个 Python ，得用 linux 虚拟机+交叉编译工具链+命令行编译 micropython 固件，还得用 DfuSe 工具烧录固件，烧录完还不能用 C 的调试器来调试。

我想拓展个自己的 C 模块，还要学着用一些完全看不懂的宏函数，还得手动注册，还得编写 makeFile ，编译完照样不能调试 C 。

我穷，买不起 STM32F4 ，想买个 **STM32F103C8T6** 的 micropython 开发板，淘宝一搜，好像没有。

现在 C8T6 也贵了，我还想用 **F0，用 G0，用国产芯片**，能行吗？

好像，给 G0 移植 micropython，不是很容易。

那？有没有另一种玩法？

换句话说，我想**用 Keil 开发，用 Keil 调试，**我还想用**最便宜的单片机，**而且**开发 C 模块还非常简单**。

这，能玩 Python吗？

![](assets/132941900-985ebc9e-fb65-48f6-8677-d3ebc65422ee.gif)

要不，试试 PikaScript？

啥是 PikaScript？

PikaScript 可以为**资源受限**的 mcu 提供**极易部署和拓展**的 **Python **脚本支持。**不需要操作系统**，能**裸机**运行，还**不需要文件系统**。

PikaScript 支持裸机运行，最低可运行于 **RAM ≥ 4kB** ，**FLASH ≥ 32kB** 的 mcu 中，推荐配置为 RAM ≥ 10kB， FLASH ≥ 64kB，像是 stm32f103c8t6、stm32g070RBT6 这些完全没有压力，甚至已经满足了推荐配置。

而且支持 **Keil、IAR、RT-Thread studio、segger embedded studio** 等 IDE 开发，零依赖，零配置，开箱即用，极易集成进已有的 C 工程。

说了这么多，刘华强就有疑问了，你说这脚本，保熟吗？

![](assets/1638666543673-423aafcb-0c29-49b3-8221-22fdc3c65199.png)

我这开~~水果~~脚本摊儿的，能买你生脚本蛋子？

这就挑点儿 Demo 给哥儿几个瞧瞧。

这可都是 STM32G070RBT6 的 Demo。

## Demo 01 点个灯

``` python
import PikaStdLib
import machine

mem = PikaStdLib.MemChecker()
io1 = machine.GPIO()
time = machine.Time()

io1.setPin('PA8')
io1.setMode('out')
io1.enable()
io1.low()

print('hello pikascript')
print('mem.max :')
mem.max()
print('mem.now :')
mem.now()

while True:
    io1.low()
    time.sleep_ms(500)
    io1.high()
    time.sleep_ms(500)
    
```

看看这脚本，可都是如假包换的 Python3 标准语法。

这灯不就闪起来了吗。

![](assets/132943428-f2b365ca-140e-42f4-936c-db6a7d9f8dee.gif)

## Demo 02 串口测试

``` python
import PikaStdLib
import machine

time = machine.Time()
uart = machine.UART()
uart.setId(1)
uart.setBaudRate(115200)
uart.enable()

while True:
    time.sleep_ms(500)
    readBuff = uart.read(2)
    print('read 2 char:')
    print(readBuff)
    
```

开个串口，读俩字符试试

![](assets/132943365-0f7059b3-4f9d-4989-a5ec-2cce72b0cc96.gif)

非常顺滑

## Demo 03 读个ADC试试

``` python
import PikaStdLib
import machine

time = machine.Time()
adc1 = machine.ADC()

adc1.setPin('PA1')
adc1.enable()

while True:
    val = adc1.read()
    print('adc1 value:')
    print(val)
    time.sleep_ms(500)
    
```

同样几行脚本搞定。

![](assets/132944185-0a01b1ba-8cf7-4f9f-9d73-fe9cbcd52f0b.png)

这是输出的结果。

这几个 Demo 占用的 RAM 最大值只有 **3.56K**，把 1K 的堆栈也算上就是 4.56K，Flash 最大占用是 30.4K，以STM32F103C8T6 的 20K RAM 和 64K Flash 为标准，RAM 才**用掉不到25%**，Flash 才**用掉不到50%**，简直是资源多到不知道咋霍霍。

同样跑 Python，我们可以简单对比一下 micropython 的常用芯片 STM32F405RG 和这次跑 PikaScript 的芯片 STM32G070CB

## RAM 资源对比

![](assets/132944731-a55ece1d-061f-4b91-ba87-bd6547be96a7.png)

## Flash 资源对比

![](assets/132944745-e9cf598d-e75f-40bb-873e-911819d535b7.png)
## 参考价对比(以2021年9月11日立创商城10片售价为参考）

![](assets/132944757-2b5cfda8-f93f-4456-8d7f-4e4767954056.png)

## 拓展能力如何呢？

除了设备驱动之外，为 mcu 开发**自定义的 python 脚本绑定**在 pikascript 的开发框架下**非常轻松**，下面两个 Demo 就是自定义的 C 模块拓展，这个 Demo 基于 ARM-2D 图像驱动库开发了一些 python 脚本接口。
## 几个小方块~

![](assets/132945282-bfd310df-8063-456d-b90c-6b798a2c8ed5.gif)
## 几个旋转太阳~

![](assets/132945107-e473a2cc-9fbc-47f9-aaed-a28d3ad1048c.gif)
## 那，PikaScript 是开源的吗？
当然，这个就是 PikaScript 的 github 主页：
[https://github.com/pikasTech/pikascript](https://github.com/pikasTech/pikascript)

## 开发难不难？
PikaScript 为开发者准备了丰富的Demo和由浅入深的开发指南，指南还会持续完善和维护。

## 可以商用吗？
当然！PikaScript 采用 MIT 协议，允许修改和商用，但是要注意保留原作者的署名。

