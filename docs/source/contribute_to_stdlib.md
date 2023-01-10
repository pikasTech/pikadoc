# 如何贡献通用模块

## PikaPython 通用模块是什么？

PikaPython 通用模块是一系列跨平台的常用工具库，比如 string, time 等等，这些库有一些提供了和 CPython 一致或者类似的 API, 有些提供了 MCU 开发的常用工具。

## PikaPython 开发环境搭建

PikaPython 标准库是跨平台的，所以不能够使用平台（比如 stm32）专有的资源，为了确保这一点，标准库都是在 linux 的平台开发的。

如何确保标准库的可用性呢？PikaPython 在 linux 平台部署了 GoogleTest 单元测试框架，可以为这些标准库提供测例，GoogleTest 可以在开发者的本地机器运行，也会在每次提交到 github 的 master 分支后自动在云端运行（基于Github Actions）。

### 构建 Docker 容器

[ 快速开始 -> 从 Docker 开发环境开始 ](https://pikadoc.readthedocs.io/zh/latest/get-start_linux.html)

## 使用 VSCODE 连接到容器进行开发

### 启动

VSCODE 提供了连接到容器进行开发的工具，连接后开发体验就和在容器外部一样好。

在 VSCODE 侧边栏选择远程，Containers，pikadev，然后点击打开目录，即可在 VSCODE 中连接到 Dockder 内部。

![](assets/image-20220601001455518-16627321708954.png)

初次打开需要等待一些插件自动安装，以后再打开就可以直接启动了。

![](assets/image-20220601001641800-16627321708956.png)

 `cd` 到 `~/pikapython/port/linux`, 然后输入 `code .`，切换工作路径到 `pikapython/port/linux`

![](assets/image-20220601001904516-16627321708955.png)

### 编译运行

- 初始化
```
sh pull-core.sh # 更新内核源码
```

- 预编译并配置 CMake
```
sh init.sh
```

- 编译
```
sh only_make.sh
```

- 测试
```
sh gtest.sh # 运行 google test
sh ci_benchmark.sh # 运行 benchmark
sh valgrind.sh # 运行 valgrind
```

- 运行
```
sh run.sh # 启动 REPL
```

### 开发

标准库的 pyi 声明文件在 package/pikascript 目录下，标准库包括了 PikaStdLib.pyi, PikaStdData.pyi, PikaDebug.pyi, PikaStdTask.pyi 等，实现文件在 PikaStdLib 文件夹下。

![](assets/image-20220601002350438-16627321708968.png)

然后可以为标准库增加类，或者函数，例如，为 `PikaStdData.String` 类增加一个 `startswith()` 方法，首先在 PikaStdData.pyi 中的 `String` 类下面新增 ` startswith() ` 方法的声明。

![](assets/image-20220601003457155-16627321708967.png)

然后运行：

```
bash init.sh
```

进行预编译和重新配置 CMake。

再打开 `PikaStdData_String.h`，会发现自动生成的 startswith 方法的 c 函数声明。

![](assets/image-20220601003545995-16627321708969.png)

接着在 PikaStdData_String.c 中实现这个函数。

![](assets/image-20220601003710360-166273217089610.png)

### 调试

调试已经被配置好了，直接在 vscode 中打断点，然后 F5 即可进入调试。

注意: vscode 工作路径需要在 ~/pikapython/port/linux 下，切换工作路径的方式：

 `cd` 到 `~/pikapython/port/linux`, 然后输入 `code .`

![](assets/172127039-49e0d663-6f7a-4057-b5fe-1363c68dd9a0.png)

可以修改 .vscode/launch.json 的 "--gtest_filter" 指定调试单个测例

![](assets/178643919-48af254d-1c38-4ddf-9082-9ab89fca0996.png)

例如只测试 `TEST(PikaCV,test1)`，则修改为 `"--gtest_filter==PikaCV.test1"`

![](assets/178644052-4d1efa56-3856-49b0-b411-d66deaecbda3.png)

### 测试

然后可以运行 GoogleTest，查看是否破坏了原有的代码。

```
bash gtest.sh 
```

![](assets/image-20220601003830732-166273217089611.png)

如果测试都通过了，就可以编写功能测试的代码了。

测试代码在 test 目录下。

![](assets/image-20220601003945867-166273217089614.png)

标准库的测试可以放在 pikaMain-test.cpp 下。

一个测例的内容如下，首先是用 TEST 宏声明一个测例，然后填入测试组的名字，和测例的名字，测试组的名字和当前文件的其他测例一致即可，测试名字需要和其他测例不同。

```C
TEST(<test group>, <test name>){

    /* do something */

    /* assert */
    
    /* deinit */
}
```

测例主要分为三个部分：

- 运行

- 判定

- 析构

  下面是一个典型的测例，我们复制这个测例，然后修改测例名。

  ``` C
  TEST(pikaMain, a_signed) {
      /* init */
      pikaMemInfo.heapUsedMax = 0;
      PikaObj* pikaMain = newRootObj("pikaMain", New_PikaMain);
      /* run */
      obj_run(pikaMain, "a = -1\n");
      /* collect */
      int a = obj_getInt(pikaMain, "a");
  
      /* assert */
      EXPECT_EQ(-1, a);
  
      /* deinit */
      obj_deinit(pikaMain);
      EXPECT_EQ(pikaMemNow(), 0);
  }
  ```

我们修改 `obj_run()` 的部分，运行一段 python 脚本，然后取出结果使用 EXPECT_EQ 宏对结果进行判定。

``` C
TEST(pikaMain, string_startswith) {
    /* init */
    pikaMemInfo.heapUsedMax = 0;
    PikaObj* pikaMain = newRootObj("pikaMain", New_PikaMain);
    /* run */
    obj_run(pikaMain, 
    "a = PikaStdData.String('test')\n"
    "res1 = a.startswith('te')\n"
    "res2 = a.startswith('st')\n"
    );
    /* collect */
    int res1 = obj_getInt(pikaMain, "res1");
    int res2 = obj_getInt(pikaMain, "res2");

    /* assert */
    EXPECT_EQ(res1, 1);
    EXPECT_EQ(res2, 0);

    /* deinit */
    obj_deinit(pikaMain);
    EXPECT_EQ(pikaMemNow(), 0);
}
```

`EXPECT_EQ`  宏是由 GoogleTest 提供的，作用是判定两个值是否相等，如果不相等，则 GoogleTest 会抛出错误，可以查看 GoogleTest 的文档了解更多。

然后我们再运行 GoogleTest

```
sh gtest.sh
```

可以看到，测例个数为 331，比之前的 330 多了一个，而且都通过了，这说明测试是成功的。

![](assets/image-20220601005050927-166273217089613.png)

### 提交

测试通过后，就可以提交这个修改了，在提交修改之前，你需要先 fork PikaPython 的仓库，Gitee 和 Github 均可。

第一次提交时，需要修改你的提交信息，包括你的用户名，email，和 fork 后的仓库地址。

```
git config --global user.name < your user name >
git config --global user.email < your email >
git config remote.origin.url < your forked git repo url >
```

运行 `sh push-core.sh` 将修改后的代码提交到 ~/pikascript/package/PikaStdLib。

如果提交 PikaStdLib 之外的库，可以使用 `sh pkg-push.sh [package name]` 命令提交，比如 `sh pkg-push.sh PikaMath`。

然后运行 `git commit -a` 输入 commit 信息，如果你不熟悉 vim，请先简单了解 vim 的基础使用方法。

![](assets/image-20220601005532339-166273217089612.png)

接下来就可以提交了

``` 
git push
```

如果出现冲突，可以先

```
git pull --rebase
```

然后再 `git push` 提交，更多 git 的用法请参考 git 使用手册。

![](assets/image-20220601005949285-166273217089615.png)

然后在 gitee / github 中发起 Pull Request

![](assets/image-20220601010131920-166273217089616.png)
