1. PikaScript 已加入 [RT-Thread软件包](https://packages.rt-thread.org/detail.html?package=pikascript)，在编程语言分类下，直接添加软件包即可快速使用 PikaScript 。

PikaScript 软件包支持**全部的 RT-Thread BSP **。
![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1638840464842-02580253-48dc-4dcc-94a4-e62f1b596b38.png#clientId=u2bb66c9e-0682-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=345&id=CTurG&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1216&originWidth=1771&originalType=binary&ratio=1&rotation=0&showTitle=false&size=187118&status=done&style=none&taskId=uca77f9cf-af5d-4cf6-933d-c77040aaa99&title=&width=503)
如果在使用过程中遇到兼容性问题，可以在 [gitee](https://gitee.com/Lyon1998/pikascript)，[github](https://github.com/pikasTech/pikascript) 提 issue 或者[论坛](https://whycan.com/f_55.html)提问。
**安装：**

   1. 引入 pikascript 软件包
   1. 在 rt-thread/src/kservice.c 中的 rt_vsnprintf 前添加 RT_WEAK **(只针对rt_thread 4.1.0版本以下)**

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639103607485-f33b48f8-a127-4612-9c4a-e2094ec5d79e.png#clientId=u99c0dd23-5056-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=101&id=u0854ea63&margin=%5Bobject%20Object%5D&name=image.png&originHeight=101&originWidth=529&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8193&status=done&style=none&taskId=u950418f4-65be-4697-bab8-1715c1da301&title=&width=529)

   3. 删除 rt-thread/components/finsh/shell.c 中 finsh_getchar 的 static **(只针对rt_thread 4.1.0版本以下)**

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639103788555-fcf1c31c-386f-4baf-b1d0-4f3016af32bc.png#clientId=ufd063eb4-fe7c-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=108&id=udd6a79b6&margin=%5Bobject%20Object%5D&name=image.png&originHeight=108&originWidth=394&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8433&status=done&style=none&taskId=uc18edcfc-c8b4-419d-a723-8b824e151bd&title=&width=394)


2. 启动 pikascript

**方案一：使用msh启动（默认模式）**

   1. 在 packages/pikascript-latest/requestment.txt 中使用 pikaRTBooter 模块（默认已引入）。

可以在这里查看最新的默认 [requestment.txt](https://gitee.com/Lyon1998/pikascript/blob/master/port/rt-thread/requestment.txt)。

   2. 在msh中输入 **"pika" **，即可**在一个线程中启动 **PikaScript。

初次启动会执行 /pikascript-latest/**main.py **初始化脚本。执行完毕后进入 pika **交互式运行**模式，
输入 "**exit()" **回到 msh，再次输入 **"pika" **进入 pikascript，将**直接进入**交互式运行模式。
![d241761d5858d3ceade44d6a678f3d9.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639058943232-9f0e0f78-0c8e-4b80-9283-6113c2450edf.png#clientId=ufd1f7665-0328-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=399&id=u885f2eae&margin=%5Bobject%20Object%5D&name=d241761d5858d3ceade44d6a678f3d9.png&originHeight=797&originWidth=965&originalType=binary&ratio=1&rotation=0&showTitle=false&size=54609&status=done&style=none&taskId=u5f2ace4e-aec0-4f27-92f0-04a91650d60&title=&width=482.5)
**方案二：开机自动启动**

   1. 进入软件包详细配置

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639184483048-498f471e-cae7-4b6f-ad94-c1b5149d621c.png#clientId=u4ec79a5f-0da0-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=139&id=u27c698e1&margin=%5Bobject%20Object%5D&name=image.png&originHeight=277&originWidth=663&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13408&status=done&style=none&taskId=ud52f65dc-dfe0-4cdb-892d-cb7b4a582e5&title=&width=331.5)

   2. 勾选Enable auto-running PikaScript

![image.png](https://cdn.nlark.com/yuque/0/2021/png/22991477/1639184596044-a85902ac-601c-49b6-b2e5-3d20bd55ce81.png#clientId=u4ec79a5f-0da0-4&crop=0&crop=0&crop=1&crop=1&from=drop&height=213&id=uf5f10b0e&margin=%5Bobject%20Object%5D&name=image.png&originHeight=552&originWidth=1500&originalType=binary&ratio=1&rotation=0&showTitle=false&size=42520&status=done&style=none&taskId=u8fe9bc28-3e0e-4901-9fe2-c3b9e94e20d&title=&width=580)

   3. 设置好后会自动启动 PikaScript ，运行 main.py 脚本，然后回到 msh

在 msh 输入 **pika **进入交互式运行**。**
**方案三：手动启动**
如果需要**定制启动，**可以使用以下的方式手动启动。

   1. 引入头文件：
```c
#include "pikaScript.h"
```
 启动 PikaScript：
```c
PikaObj * pikaMain = pikaScriptInit();
```

   2. 交互式运行

参考**支持交互式运行**部分文档。

   3. 串口下载 Python 脚本

参考**支持串口下载 Python **部分文档。


3. 使用 PikaScript 模块和包管理器

   1. 修改 pikascript-latest/requestment.txt，然后右键工程，Sconscripts Update，即可安装模块/修改模块版本，并预编译。

![IMG_20211215_091327.jpg](https://cdn.nlark.com/yuque/0/2021/jpeg/22991477/1639531121038-abc40292-62fe-4a30-b074-7101714f6db7.jpeg#clientId=u2f6e8a27-3f82-4&crop=0&crop=0&crop=1&crop=1&from=ui&height=1104&id=u26009eda&margin=%5Bobject%20Object%5D&name=IMG_20211215_091327.jpg&originHeight=2400&originWidth=1080&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1368269&status=done&style=none&taskId=ubbf1a015-08a0-47a2-abdf-b8b6ed84673&title=&width=497)


更多用法参考**包管理器**，**模块使用，模块开发**部分文档。
