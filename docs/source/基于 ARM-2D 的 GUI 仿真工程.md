# 基于 ARM-2D 的 GUI 仿真工程

## 前言


好消息！ pikascript 的 Arm2D 模块以及仿真工程初步整理好了！pikaScript，ARM-2D，rt-thread 齐活儿，解锁python 玩 Arm2D 的新姿势！还不需要硬件，可以直接仿真，可以说是非常方便了。


在自己的电脑上部署运行这个仿真工程也非常简单，按照下面的几步操作就可以了~
## 获得仿真工程


首先进入 PikaScript 的代码仓库


[https://github.com/pikastech/pikascript](https://github.com/pikastech/pikascript) (需要科学上网)


![](assets/139675132-739ec77b-db22-4ed9-a670-77ec7544d1b9.png)


然后点一个 Star


如果进不去的话，就进下面这个


[https://gitee.com/Lyon1998/pikascript](https://gitee.com/Lyon1998/pikascript) (国内也能上)


![](assets/139675170-fe0ce449-872f-466e-8780-74465730178a.png)


然后也点一个 Star


好，等你点完 Star，我们开始下一步操作。


我们从代码仓库的主页往下翻，看到 Get PikaScript，然后点 PikaPackage.exe 下载 pikascript 的包管理器。


![](assets/139675454-596829d1-0325-42ab-96c5-f3d3d369d7d4.png)


Gitee 上的也是一样的，任选一个即可。


![](assets/139675486-0f63e7b4-669d-4370-80ad-134c0f28f203.png)


下面把 PikaPackage.exe 放到你想要下载 PikaScript 的磁盘，为了节省你的 C 盘，你可以把  PikaPackage.exe 放在D盘，可以是 D 盘的任意位置。


双击 PikaPackage.exe，包管理器就会自动帮你把最新的 PikaScript 下载到 D:/tmp/pikascript 文件夹中。(如果放在 C 盘就会下载到 C:/tmp/pikascript)


下载使用的是国内资源，不需要科学上网，速度应该很不错。


下载完之后，就可以删掉这个 pikaPackage.exe 了。


顺利的话，你就可以在 /tmp/pikascript 文件夹下找到下载好的 pikascript 代码仓库了。


![](assets/139676635-c3f1c6ae-ab44-42a5-ab9a-9bedd2383f31.png)


我们进入 bsp 文件夹，拷贝一份 simulation-rtt-qemu-arm2d 出来。


![](assets/139677151-33c1dbd0-c2f2-4ea3-a5ae-569e5a448cce.png)


到此为止，工程就准备 ok 了。


## 安装开发环境


有了工程之后，还需要安装开发环境，需要安装的只有两个东西，一个是 rt-thread studio，用来做IDE，rt-thread studio 里面集成了 qemu，用来仿真 mcu 和 gui 非常方便。另一个是最新的 arm gcc 工具链。


### rt-thread studio 安装包链接


[https://download-sh-cmcc.rt-thread.org:9151/www/studio/download/RT-Thread Studio-v2.1.2-setup-x86_64_20210831-1200.exe](https://download-sh-cmcc.rt-thread.org:9151/www/studio/download/RT-Thread%20Studio-v2.1.2-setup-x86_64_20210831-1200.exe)


### arm gcc 安装包链接


[https://developer.arm.com/-/media/Files/downloads/gnu-rm/10.3-2021.10/gcc-arm-none-eabi-10.3-2021.10-win32.exe](https://developer.arm.com/-/media/Files/downloads/gnu-rm/10.3-2021.10/gcc-arm-none-eabi-10.3-2021.10-win32.exe)


rt-thread studio 装在你喜欢的地方就可以，arm gcc 要装在默认的c盘。


装好之后，就可以开始用 python 玩 arm-2d 了。


## 拉取模块并预编译


我们进入 simulation-rtt-qemu-arm2d/packages/pikascrpt 目录，这个目录就是 pikascrit 的文件了。


![](assets/139678258-e2cdc50d-475b-435a-af8c-7c19cc3a218d.png)


为了版本管理的方便，pikascript 使用 requestment.txt 管理内核和模块的版本，所以这个文件夹里没有 pikascript 的源码，只有一个 requestment.txt 文件，如果熟悉 pip，就会发现这个文件和 pip 所使用的版本描述文件是一模一样的。


![](assets/139678404-9b747c0a-6508-4f6d-b0ca-671560f31fbd.png)


我们双击运行这个文件夹下的 pikaPackage.exe ，pikascript 的内核和模块就拉取下来了。


![](assets/139678437-a77b7278-cafd-485e-b353-94a12302c8cb.png)


拉下来之后是这样的。


![](assets/139678713-0cd86aef-2996-4898-931d-68c805534312.png)


最后我们再运行 rust-msc-latest-win10.exe 进行预编译，就 OK 了。


![](assets/139678750-befc11e9-d812-4fcf-949e-64dd873d0211.png)


## 运行


我们打开 RT-Thread Studio，点击导入


![](assets/139679061-2e3b2ea0-8e9a-44c9-9a0f-6f40d82a0208.png)


然后选择 simulation-rtt-qemu-arm2d 文件夹


![](assets/139679380-3a45f426-e575-4142-b5f1-76439c7efc38.png)


选择工程，然后点锤子编译，再点虫子进入仿真


![](assets/139679532-e19ed911-c7f4-4840-a5e3-f5b66905a62f.png)


这时会弹出一个 QEMU 的框，然后点击运行。


![](assets/139679756-cb099fc9-c3e9-4b76-9037-38392350530b.png)


运行成功的话，就可以看到白色背景上有一个蓝色的小方块了。到此为止部署就成功了。


![](assets/139679797-3ce8f253-beb9-480f-90ee-1844500a77ab.png)


## 修改python代码试试


python 的源码就在 simulation-rtt-qemu-arm2d/packages/pikascript/main.py 里面，可以打开看看~


![](assets/139679915-45d1362e-7066-4829-ae83-b4bbc5d0aaa0.png)


下面就是 main.py 的内容，新建了一个 box 对象，然后设置了颜色和位置，你可以试着修改颜色为 'red' 或者改一下坐标看看，也可以新建另一个 screen.elems.b2 试试。


![](assets/139680125-11ff47b3-e75e-47f4-8dd7-5b310c5be16c.png)


每次修改完后要记得预编译，才能把 python 转为工程里的 .c 文件


![](assets/139680376-b9681759-971a-43f7-9282-ee0e35a367a5.png)


然后再编译，进入仿真，就可以看到效果了。这次我把方块改成了红色。


![](assets/139680521-20f83ee3-2163-4649-ad23-ae73b77f482e.png)


## 结语


这是 Arm-2D 的仓库~ 还没 star 的同学记得补个 star~

[https://github.com/ARM-software/EndpointAI](https://github.com/ARM-software/EndpointAI)


![](assets/139681272-73a1a8c2-2889-4dab-bd05-7174cb14334c.png)


感谢 liuduanfei 大佬提供的 rtt-Arm2d-qemu 仿真工程~ 下面是 liuduanfei 大佬的 github 主页


![](assets/139681543-99a64e9b-eb10-4c8e-bbe3-e8170c85385a.png)


[https://github.com/liuduanfei](https://github.com/liuduanfei)
