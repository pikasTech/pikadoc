# 对接IDE
## 概述
PikaScript需要对接IDE的工具集包括

1. 包管理器pikaPackage.exe

参考**包管理器与模块管理**相关文档

2. 预编译器rust-msc-latest-win10.exe

参考**模块开发**相关文档
## 调用方式
### 1. 起始路径：

   1. [裸机工程根目录]/pikascript路径
   1. [rtthread工程根目录]/packages/pikascript-latest路径
### 2. 包管理器

   1. 初次从PikaSciprt远程拉取模块时，需要运行pikaPackge.exe
   1. 修改requestment.txt后，需要运行pikaPackage.exe
   1. 如使用了latest版本模块，更新模块至最新时，需要运行pikaPackage.exe
### 3. 预编译器
a. 在每次编译前运行
**【注意】：**初次运行时，先用pikaPackage.exe拉取预编译器。
## 工程文件

   1. 在执行包管理器或者预编译器后，需要添加**pikascript-lib,pikascript-core,pikascript-api**下的**全部（包括子文件夹）**的.c文件和include路径。
   1. 重置PikaScript工程文件：删除pikascript-lib，pikascript-core，pikascript-api后，重新运行pikaPackage.exe和rust-msc-latest-win10.exe。
