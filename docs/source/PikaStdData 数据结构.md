PikaStdData 数据结构库提供了 List （列表），Dict（字典）数据结构。
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
import PikaStdData
```
## 类
### class List():
List 类提供了 List 列表功能，由 List 类创建对象，即可创建一个列表。
如：
```python
import PikaStdData
list = PikaStdData.List()
```
#### List 类的方法
```python
    # add an arg after the end of list
    def append(arg: any):
        pass

    # get an arg by the index
    def get(i: int) -> any:
        pass

    # set an arg by the index
    def set(i: int, arg: any):
        pass

    # get the length of list
    def len() -> int:
        pass
```
注意，`set()` 方法的索引不能够超出 List 的长度，如果要添加列表的成员，需要使用 `append()`方法。
#### 使用 '[]' 中括号索引列表
List 对象可以使用 '[]' 进行索引。`list[1] = a`等效于 `list.set(1, a)`，`a = list[1]`等效于`a = list.get(1)`。
#### 使用 for 循环遍历 List
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
### class Dict():
Dict 类提供了 Dict 字典功能，由 Dict 类创建对象，即可创建一个字典。
如：
```python
import PikaStdData
dict = PikaStdData.Dict()
```
#### Dict 类的方法
```python
    # get an arg by the key
    def get(key: str) -> any:
        pass

    # set an arg by the key
    def set(key: str, arg: any):
        pass

    # remove an arg by the key
    def remove(key: str):
        pass
```
#### 使用 '[]' 中括号索引字典
Dict 对象可以使用 '[]' 进行索引。`dict['x'] = a`等效于 `dict.set('x', a)`，`a = dict['x']`等效于`a = dict.get('x')`。
#### 使用 for 循环遍历 Dict
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
