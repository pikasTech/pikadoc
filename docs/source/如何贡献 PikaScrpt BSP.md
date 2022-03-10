# 如何贡献 PikaScript BSP
## 制作 BSP 的步骤：
### 制作 pikascript 模板工程
- pikascript 的 BSP 很简单，就是一个可以**独立编译**的 pikascript 模板工程。
- 这个工程只需要能够**最基本**地运行 pikascript 即可。
- 可以参考**新平台移植指南**，确保能够正常运行 main.py 中的 `print('hello PikaScript!')`。
### 清理工程
- 清理**编译产物**，只留下工程文件和源码。（ 编译产物包括中间文件 .o .d ，二进制产物 .bin, .hex ，可执行文件 .exe 等）。
- 清理 pikascript 文件夹中**自动拉取**和**自动生成**的代码，pikascript 文件夹只保留 main.py，requestment.txt，和 pikaPackage.exe 三个文件即可。
- 清理没有用到的源码和库，将工程的体积控制在到**50MB**以内。**如果清理后工程体积仍大于50MB，可以新建一个专门仓库放置BSP，在 pikscript/bsp 中仅放置一个包含专门仓库链接的 README.md。**
### 提交文件
- 进入 pikascript 代码仓库，gitee 或 github 均可，fork 一份 pikascript 仓库，然后将 **fork 后的**仓库 clone 到本地。

![](assets/1638664526181-09b00c29-fc72-429a-bb99-3f009eae141e.png)

- 在 [fork后的仓库]/bsp 目录下新建一个新文件夹，然后拷贝进去模板工程，使用 git 命令添加文件，并推送到 **fork 后的** pikascript 仓库中。
   
```shell
cd pikascript/bsp
git add *
git commit -m 'add bsp'
git push
```


- （可选）在 pikascript/README.md 和 pikascript/README_zh.md 中更新 BSP 信息。
- 开启 Pull Request，等待合并。
