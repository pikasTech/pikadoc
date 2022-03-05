# PikaStdLib  标准库

PikaStdLib 是 PikaScript 的自带内置库，是必须安装的库，包含了内存检查工具和系统对象。
## 安装

1. 在 requestment.txt 中加入 PikaStdLib 的依赖，PikaStdLib 的版本号应当与内核的版本号相同。
```
PikaStdLib==v1.3.5
```

2. 运行 pikaPackage.exe
## 导入
在 main.py 中加入
```python
#main.py
import PikaStdLib
```
## 类
### class MemChecker()
MemChecker 提供 PikaScript 的内存监控功能。可以用来查看内存占用，以及检查内存泄漏。
```python
def max():
```
打印最大的内存占用值。
```python
def now():
```
打印当前的内存占用值。
```python
def getMax()->float:
```
返回最大的内存占用值
```python
def getNow()->float
```
返回当前的内存占用值。
```python
def resetMax()
```
重置内存最大占用值
**用例：**
```python
# main.py
import PikaStdLib
mem = PikaStdLib.MemChecker()
print('mem used max:')
mem.max()
print('mem used now:')
mem.resetMax()
print('mem used max:' + str(mem.getMax()))
print('mem used now:' + str(mem.getNow()))
```
### class SysObj()
SysObj 用于提供内置函数，main.py 中执行的脚本是由根对象执行的，而根对象由 SysObj 类创建，因此 SysObj 类中的方法就是内置函数。
```python
def type(arg: any):
```
	打印变量的类型
```python
def remove(argPath: str):
```
	删除变量/对象，在删除时使用字符串，例如 `remove('a')`。
```python
def int(arg: any) -> int:
def float(arg: any) -> float:
def str(arg: any) -> str:
```
	用于类型转换
```python
def print(arg:any):
```
	继承自 BaseObj，提供打印输出。暂不支持格式化输出。
