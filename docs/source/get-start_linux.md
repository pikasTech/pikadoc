# 从 Docker 开发环境开始

## 为什么使用 docker 开发环境

PikaScript 的内核和标准库都是在 docker 环境下开发的，当需要开发一些涉及到内核内部的功能时，会容易出现一些难以调试的问题，如：

- 内存泄漏
- 内存越界
- 破坏内核原有功能

使用 PikaScript 的docker 开发环境可以避免这个问题，docker 开发环境中已经安装了配套的 **单元测试框架** 和 **内存检查工具** ，如果有内存安全问题，可以快速发现并解决，避免出现内存隐患。

PikaScript 的 linux 开发平台还需要安装 go，rust，GoogleTest，GoogleBenchmark，valgrind 等等工具，比较繁琐，基于 Docker 的开发环境可以一键安装这些工具，并保证所有开发者的开发环境都是一致的。

在 Docker 的构建脚本中已经完成了换源操作，所以不需要使用 vpn，即可在中国大陆顺利的搭建 Docker 开发环境。


## 构建 Docker 容器

请确认已经在宿主机安装好了 Docker:

- Linux 平台直接安装 Docker
- Windows 平台安装 Docker-Desktop
  - Docker-Desktop 需要安装 wsl2 [安装手册](https://smartide.cn/zh/docs/install/docker/windows/)

（如果是 windows 平台，可以在 wsl 中使用下面的命令，不要使用 PowerShell）

step1: 克隆仓库

``` shell
git clone https://gitee.com/lyon1998/pikascript
cd pikascript/docker 
```

step2: 构建 Docker 镜像，然后启动容器
```
bash build.sh
sh run.sh
```

step3: 初始化 port/linux

``` shell	
cd port/linux
sh pull-core.sh
sh init.sh
```

step4: 运行 GoogleTest， BenchMark，和 valgrind
``` shell
sh gtest.sh
sh ci_benchmark.sh
sh valgrind.sh
```

step5: 运行 REPL
``` shell
sh run.sh
```

更多 Docker 下的开发指引，请参考 [ 标准库的开发流程 ](https://pikadoc.readthedocs.io/zh/latest/contribute_to_stdlib.html)。
