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

#### Slice

| Syntax | str | bytes | list |
| --- | --- | --- | --- |
| test[i] | √ | √ | √ |
| test[a : b] | √ | √ | √ | 
| test[a :] | √ | √ | √ |

#### Function Arguments

| Syntax                                | State |
| ------------------------------------- | ----- |
| Default Arguments                     | √     |
| Keyword Arguments                     | √     |
| Variable Positional Arguments (\*args) | √     |
| Variable Keyword Arguments (\*\*kwargs) | √     |

#### String Formatting

| Syntax                                | State |
| ------------------------------------- | ----- |
| %-formatting                          | √     |
| str.format()                          | -     |
| f-strings (formatted string literals) | -     |

#### Comparison Operations

| Syntax                        | Number | List | Dictionary |
| ----------------------------- | ------ | ---- | ---------- |
| Equal (==)                    | √      | -    | -          |
| Greater Than (>)              | √      | -    | -          |
| Less Than (<)                 | √      | -    | -          |
| Greater Than or Equal To (>=) | √      | -    | -          |
| Less Than or Equal To (<=)    | √      | -    | -          |
| Membership (in)               | -      | √    | √ (keys)   |
| Non-membership (not in)       | -      | √    | √ (keys)   |
| Identity (is)                 | √      | √    | √          |
| Non-identity (is not)         | √      | √    | √          |

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

#### Context Managers

| Syntax                                                       | State |
| ------------------------------------------------------------ | ----- |
| with statement                                               | -     |
| custom context managers (using __enter__ and __exit__ methods) | -     |

#### Generators

| Syntax                              | State |
| ----------------------------------- | ----- |
| generator functions (using 'yield') | -     |
| generator expressions               | -     |
