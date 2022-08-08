# 从 CMSIS-PACK 开始

使用 Keil 开发的用户可以使用 CMSIS-PACK 一键安装 PikaScript。

## 安装 PikaTech.PikaScript.x.x.x.pack

[ 点击下载 ](https://gitee.com/Lyon1998/pikascript/attach_files/1151246/download)

一路 Next 安装即可

![](assets/image-20220624090014867.png)

## 在工程中设置

![](assets/image-20220624090340868.png)

勾选 PikaScript，包括 Core 和 PikaStdLib

![](assets/image-20220624090401713.png)

这是可以看到 PikaScript 已经被添加进来了

![](assets/image-20220624090444608.png)

在 Before Build 加入

```
.\RTE\PikaScript\pikaBeforBuild-keil.bat
```

![](assets/image-20220624090543736.png)

然后在 main.c 引入

``` c
#include "pikaScript.h"
```

在初始化系统和 printf 后启动 PikaScript

``` c
PikaObj *pikaMain = pikaScriptInit();
```

编译成功：

![](assets/image-20220624091046123.png)

运行成功：

![](assets/image-20220624091137190.png)

更多用法请参考 [移植指南](https://pikadoc.readthedocs.io/zh/latest/index_porting.html)
