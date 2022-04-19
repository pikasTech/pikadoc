# 从 RT-Thread 软件包开始

PikaScript 已加入 [RT-Thread软件包](https://packages.rt-thread.org/detail.html?package=pikascript)，在编程语言分类下，直接添加软件包即可快速使用 PikaScript 。

PikaScript 软件包支持**全部的 RT-Thread BSP** 。
![](assets/1638840464842-02580253-48dc-4dcc-94a4-e62f1b596b38.png)
如果在使用过程中遇到兼容性问题，可以在 [gitee](https://gitee.com/Lyon1998/pikascript)，[github](https://github.com/pikasTech/pikascript) 提 issue 或者[论坛](https://whycan.com/f_55.html)提问。

## 安装

   引入 pikascript 软件包

   ![image](assets/159112436-d8814770-0e86-4016-a529-7053d7256df9.png)

   ![image](assets/159112451-20335611-fb55-42da-b1ec-c6e9878333b3.png)

   ![image](assets/159112459-36030f2a-69f7-4e8f-8b3f-57011eaff82b.png)

   ![image](assets/159112482-378a549c-fb3b-4be6-b72e-a02b8e1217f3.png)

   在 rt-thread/src/kservice.c 中的 rt_vsnprintf 前添加 RT_WEAK **(只针对rt_thread 4.1.0版本以下)**

![](assets/1639103607485-f33b48f8-a127-4612-9c4a-e2094ec5d79e.png)

   删除 rt-thread/components/finsh/shell.c 中 finsh_getchar 的 static **(只针对rt_thread 4.1.0版本以下)**

![](assets/1639103788555-fcf1c31c-386f-4baf-b1d0-4f3016af32bc.png)

## 启动 pikascript

**方案一：使用msh启动（默认模式）**

   在 packages/pikascript-latest/requestment.txt 中使用 pikaRTThread 模块（默认已引入）。

可以在这里查看最新的默认 [requestment.txt](https://gitee.com/Lyon1998/pikascript/blob/master/port/rt-thread/requestment.txt)。

   在msh中输入 "pika" ，即可 **在一个线程中启动** PikaScript。

初次启动会执行 /pikascript-latest/main.py 初始化脚本。执行完毕后进入 pika **交互式运行** 模式，
输入 "exit()" 回到 msh，再次输入 "pika" 进入 pikascript，将**直接进入**交互式运行模式。
![](assets/1639058943232-9f0e0f78-0c8e-4b80-9283-6113c2450edf.png)
**方案二：开机自动启动**

   进入软件包详细配置

![](assets/1639184483048-498f471e-cae7-4b6f-ad94-c1b5149d621c.png)

   勾选Enable auto-running PikaScript

![](assets/1639184596044-a85902ac-601c-49b6-b2e5-3d20bd55ce81.png)

   3设置好后会自动启动 PikaScript ，运行 main.py 脚本，然后回到 msh

在 msh 输入 **pika** 进入交互式运行。

**方案三：手动启动**

如果需要 **定制启动** ，可以使用以下的方式手动启动。

   引入头文件：
```c
#include "pikaScript.h"
```
 启动 PikaScript：
```c
PikaObj * pikaMain = pikaScriptInit();
```

   交互式运行

参考**支持交互式运行**部分文档。

   串口下载 Python 脚本

参考**支持串口下载 Python** 部分文档。

### 使用 PikaScript 模块和包管理器

   修改 pikascript-latest/requestment.txt，然后右键工程，Sconscripts Update，即可安装模块/修改模块版本，并预编译。

![](assets/1639531121038-abc40292-62fe-4a30-b074-7101714f6db7.jpeg)


更多用法参考**包管理器**，**模块使用，模块开发**部分文档。
