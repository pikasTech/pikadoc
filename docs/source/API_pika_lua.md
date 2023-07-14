# pika_lua 模块 API 文档

## API

PikaPython lua auto binging module

- Import lua module as a python module

``` python
import pika_lua
# import lua module as a python module
lua_math = pika_lua.require("math")
# get vars from lua module
print(lua_math.pi)
# call lua function
print(lua_math.sin(1))
```

- Eval lua code

``` python
import pika_lua
# eval lua code
print(pika_lua.eval("print(1 + 1)"))
```


``` python
def evals(cmd:str):...
```

``` python
def evalLine(line:str):...
```

``` python
def getVar(name:str):...
```

``` python
def setVar(name:str,value):...
```

### class LuaModuleProxy:
``` python
def __init__(self,name:str):...
```

``` python
def __getattr__(self,name:str):...
```

``` python
def __setattr__(self,name:str,value)->None:...
```

``` python
def __proxy__(self,methodName,*args):...
```

``` python
def require(module:str)->LuaModuleProxy:...
```



## Examples

### require.py

```python
import pika_lua
lua_math = pika_lua.require("math")
assert lua_math.pi == 3.141592653589793
assert lua_math.sin(0) == 0
assert lua_math.sin(lua_math.pi / 2) == 1
assert lua_math.sin(lua_math.pi) == 0
assert lua_math.sin(lua_math.pi * 3 / 2) == -1
assert lua_math.sin(lua_math.pi * 2) == 0
assert lua_math.cos(0) == 1
assert lua_math.cos(lua_math.pi / 2) == 0
assert lua_math.cos(lua_math.pi) == -1
print('PASS')

```
### eval.py

```python
import pika_lua

# 测试数字
assert pika_lua.evals('return 1 + 1') == 2

# 测试字符串
assert pika_lua.evals('return "hello"') == "hello"

# 测试布尔值
assert pika_lua.evals('return true') == True

# 测试nil
assert pika_lua.evals('return nil') == None

# 测试变量赋值
pika_lua.evals('x = 10')
assert pika_lua.evals('return x') == 10

# 测试函数调用
pika_lua.evals('function add(a, b) return a + b end')
assert pika_lua.evals('return add(1, 2)') == 3

# table to list
l = pika_lua.evals('return {1, 2, 3}')
assert l[0] == 1
assert l[1] == 2
assert l[2] == 3

# table to dict
d = pika_lua.evals('return {a = 1, b = 2, c = 3}')
assert d['a'] == 1
assert d['b'] == 2
assert d['c'] == 3

print('PASS')

```
