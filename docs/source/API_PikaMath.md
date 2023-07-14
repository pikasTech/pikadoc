# PikaMath 模块 API 文档

## API

### class Operator(TinyObj):
``` python
def plusInt(self,num1:int,num2:int)->int:...
```

``` python
def plusFloat(self,num1:float,num2:float)->float:...
```

``` python
def minusInt(self,num1:int,num2:int)->int:...
```

``` python
def minusFloat(self,num1:float,num2:float)->float:...
```

``` python
def equalInt(self,num1:int,num2:int)->int:...
```

``` python
def equalFloat(self,num1:float,num2:float)->int:...
```

``` python
def graterThanInt(self,num1:int,num2:int)->int:...
```

``` python
def graterThanFloat(self,num1:float,num2:float)->int:...
```

``` python
def lessThanInt(self,num1:int,num2:int)->int:...
```

``` python
def lessThanFloat(self,num1:float,num2:float)->int:...
```

``` python
def AND(self,flag1:int,flag2:int)->int:...
```

``` python
def OR(self,flag1:int,flag2:int)->int:...
```

``` python
def NOT(self,flag:int)->int:...
```

``` python
def __str__(self)->str:...
```

``` python
def __del__(self):...
```

### class Math(TinyObj):
``` python
def __init__(self):...
```

``` python
def ceil(self,x:float)->int:...
```

``` python
def fabs(self,x:float)->float:...
```

``` python
def floor(self,x:float)->int:...
```

``` python
def fmod(self,x:float,y:float)->float:...
```

``` python
def remainder(self,x:float,y:float)->float:...
```

``` python
def trunc(self,x:float)->float:...
```

``` python
def exp(self,x:float)->float:...
```

``` python
def log(self,x:float)->float:...
```

``` python
def log2(self,x:float)->float:...
```

``` python
def log10(self,x:float)->float:...
```

``` python
def pow(self,x:float,y:float)->float:...
```

``` python
def sqrt(self,x:float)->float:...
```

``` python
def acos(self,x:float)->float:...
```

``` python
def asin(self,x:float)->float:...
```

``` python
def atan(self,x:float)->float:...
```

``` python
def atan2(self,x:float,y:float)->float:...
```

``` python
def cos(self,x:float)->float:...
```

``` python
def sin(self,x:float)->float:...
```

``` python
def tan(self,x:float)->float:...
```

``` python
def degrees(self,x:float)->float:...
```

``` python
def radians(self,x:float)->float:...
```

``` python
def cosh(self,x:float)->float:...
```

``` python
def sinh(self,x:float)->float:...
```

``` python
def tanh(self,x:float)->float:...
```

### class Quaternion(TinyObj):
``` python
def __init__(self):...
```

``` python
def set(self,x:float,y:float,z:float,w:float):...
```

``` python
def get(self,key:int)->float:...
```

``` python
def add(self,quat:Quaternion):...
```

``` python
def sub(self,quat:Quaternion):...
```

``` python
def mul(self,quat:Quaternion):...
```

``` python
def magnituded(self)->float:...
```

``` python
def magnitudedsquare(self)->float:...
```

``` python
def reverse(self):...
```

``` python
def inverse(self):...
```

``` python
def normalize(self):...
```

``` python
def isnormalize(self)->int:...
```

``` python
def dot(self,quat:Quaternion)->float:...
```

``` python
def crossproduct(self,quat:Quaternion):...
```

``` python
def fromEuler(self,yaw:float,pitch:float,roll:float,mode:int):...
```

``` python
def toEuler(self)->list:...
```



## Examples

### Quaternion_test.py

```python
from PikaMath import Quaternion

a=Quaternion()
a.set(0.592,0.158,0.592,0.525)

b=Quaternion()

a.add(b)
a.mul(b)



```
### modbus_convert.py

```python
def convert_to_modbus(num):
    # 判断输入数值的符号
    if num >= 0:
        sign = 0
    else:
        sign = 1

    # 如果是负数，将其转换为补码形式
    if sign:
        num = (~(-num) + 1) & 0xFFFF

    return num


def convert_from_modbus(num):
    # 判断输入数值的符号
    if (num & 0x8000):
        sign = 1
    else:
        sign = 0

    # 如果是负数，将其转换回原始的负数形式
    if sign:
        num = -((~num + 1) & 0xFFFF)

    return num


# 测试示例
num = -10
modbus_value = convert_to_modbus(num)

original_value = convert_from_modbus(modbus_value)

assert modbus_value == 65526
assert original_value == -10
print("PASS")

```
