# 对接IDE
## 概述
PikaScript 需要对接 IDE 的工具集包括

- 包管理器 pikaPackage.exe

参考 **包管理器与模块管理** 相关文档

- 预编译器 rust-msc-latest-win10.exe

参考 **模块开发** 相关文档

## 调用方式

### 起始路径：

   1. [裸机工程根目录]/pikascript路径
   1. [rtthread工程根目录]/packages/pikascript-latest路径

### 包管理器

   1. 初次从 PikaSciprt 远程拉取模块时，需要运行 pikaPackge.exe
   1. 修改 requestment.txt 后，需要运行 pikaPackage.exe
   1. 如使用了 latest 版本模块，更新模块至最新时，需要运行 pikaPackage.exe

### 预编译器

在每次编译前运行

**【注意】** 初次运行时，先用 pikaPackage.exe 拉取预编译器。

## 工程文件

   1. 在执行包管理器或者预编译器后，需要添加 **pikascript-lib,pikascript-core,pikascript-api** 下的 **全部（包括子文件夹)** 的 .c 文件和 include 路径。
   1. 重置 PikaScript 工程文件：删除 pikascript-lib，pikascript-core，pikascript-api 后，重新运行 pikaPackage.exe 和 rust-msc-latest-win10.exe。

## 示例

为 keil 编写的自动预编译脚本 pikaBeforeBuild-keil.bat ：

```bash
cd ../pikascript

if not exist pikascript-core (
    pikaPackage.exe
)
rust-msc-latest-win10.exe
```

![](https://user-images.githubusercontent.com/88232613/177667714-858d644b-aa13-4104-be29-560de61c2948.png)

Visual Studio 中预编译的设置

![](https://user-images.githubusercontent.com/88232613/172519804-67b32285-1d3c-4ff6-a90b-191f23a04592.png)

