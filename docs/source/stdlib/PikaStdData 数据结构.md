# PikaStdData 数据结构

PikaStdData 数据结构库提供了 List （列表），Dict（字典）数据结构。
## 安装

1. 在 requestment.txt 中加入 PikaStdLib 的依赖，PikaStdLib 的版本号应当与内核的版本号相同。
```
PikaStdLib==v1.6.1
```

2. 运行 pikaPackage.exe
## 导入
在 main.py 中加入
```python
#main.py
import PikaStdData
```
## class List():
List 类提供了 List 列表功能，由 List 类创建对象，即可创建一个列表。
如：
```python
import PikaStdData
list = PikaStdData.List()
```
### List 类的方法
```python
    # add an arg after the end of list
    def append(self, arg: any):
        pass

    # get an arg by the index
    def get(self, i: int) -> any:
        pass

    # set an arg by the index
    def set(self, i: int, arg: any):
        pass

    # get the length of list
    def len(self) -> int:
        pass
```
注意，`set()` 方法的索引不能够超出 List 的长度，如果要添加列表的成员，需要使用 `append()`方法。
### 使用 '[]' 中括号索引列表
List 对象可以使用 '[]' 进行索引。`list[1] = a`等效于 `list.set(1, a)`，`a = list[1]`等效于`a = list.get(1)`。
### 使用 for 循环遍历 List
List 对象支持 for 循环遍历
例：
```python
import PikaStdData
list = PikaStdData.List()
list.append(1)
list.append('eee')
list.append(23.44)
for item in list:
    print(item)

```
## class Dict():
Dict 类提供了 Dict 字典功能，由 Dict 类创建对象，即可创建一个字典。
如：
```python
import PikaStdData
dict = PikaStdData.Dict()
```
### Dict 类的方法
```python
    # get an arg by the key
    def get(self, key: str) -> any:
        pass

    # set an arg by the key
    def set(self, key: str, arg: any):
        pass

    # remove an arg by the key
    def remove(self, key: str):
        pass
```
### 使用 '[]' 中括号索引字典
Dict 对象可以使用 '[]' 进行索引。`dict['x'] = a`等效于 `dict.set('x', a)`，`a = dict['x']`等效于`a = dict.get('x')`。
### 使用 for 循环遍历 Dict
Dict 对象支持 for 循环遍历
例：
```python
import PikaStdData
dict = PikaStdData.Dict()
dict['a'] = 1
dict['b'] = 'eee'
dict['c'] = 23.44
for item in dict:
    print(item)

```
## class ByteArray(List)

[注意]: PikaStdData 的版本至少需要 v1.5.3

ByteArray 类提供了 ByteArray 字节数组功能，由 ByteArray 类创建对象，即可创建一个字节数组。

如：
```python
import PikaStdData
bytes = PikaStdData.ByteArray()
```

ByteArray 类继承自 List 类，可以使用 List 类的方法。

### ByteArray 类的方法

``` python
    # convert a string to ByteArray
    def fromString(self, s:str):
        pass
```
用例:
``` python
>>> bytes = PikaStdData.ByteArray()
>>> bytes.fromString('test')
>>> for byte in bytes:
...     print(byte)
... 
116
101
115
116
>>> bytes.append(0xff)
>>> bytes.append(0x0f)
>>> print(bytes[4])
255
>>> print(bytes[5])
15
```
