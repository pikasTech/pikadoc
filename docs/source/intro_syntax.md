# 语法支持

支持 python3 标准语法的子集。

#### 对象支持

|语法|编译时|运行时|Shell|
|---|---|---|---|
|模块定义   |√|-|-|
|模块导入   |√|√|√|
|类定义    |√|√|√|
|类继承    |√|√|√|
|方法定义   |√|√|√|
|方法重载   |√|√|√|
|方法调用   |√|√|√|
|参数定义   |√|√|√|
|参数赋值   |√|√|√|
|对象新建   |√|√|√|
|对象销毁   |√|√|√|
|对象嵌套   |√|√|√|
|控制流     |√|√|√|

#### Operator

| + | - | * | / | == | > | < | >= | <= | % | ** | // | != | & | >> | << | and | or | not | in | += | -= | *= | /= |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|√|

#### Control flow

| Syntax | State |
| --- | --- |
| if | √ |
| while | √ |
| for in [list] | √ |
| for in range(a, b) | √ |
| for in [dict] | √ |
| if elif else | √ |
| for break/continue | √ |
| while break/continue | √ |

#### Module

| Syntax | Python Module | C Module |
| --- | --- | --- |
| import [module] | √ | √ |
| import [module] as | √ | - |
| from [module] import [class/function>]| √ | - |
| from [module] import [class/function>] as | √ | - |
| from [module] import * | - | PikaObj Module Only |

#### List/Dict

| Syntax | State |
| --- | --- |
| l = list() | √  |
| l = [a, b, c] | √ |
| d = dict() | √ |
| d = {'a':x, 'b':y, 'c':z} | √ |

#### Exception

| Syntax | State |
| --- | --- |
|try:| √ |
|except:| √ |
|except [Exception]:| - |
|except [Exception] as [err]: | - |
|except: ... else:| - |
|raise:| √ |
|raise [Exception]:| - |
|finally:| - |

#### Slice

| Syntax | str | bytes | list |
| --- | --- | --- | --- |
| test[i] | √ | √ | √ |
| test[a : b] | √ | √ | √ | 
| test[a :] | √ | √ | √ |

#### Other keywords/Syntax

| yield | is | comprehensions |
| --- | --- | --- |
| - | √ | - |