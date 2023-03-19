# PikaStdLib 模块 API 文档

### class MemChecker:
``` python
def max(self):...
```

``` python
def now(self):...
```

``` python
def getMax(self)->float:...
```

``` python
def getNow(self)->float:...
```

``` python
def resetMax(self):...
```

### class SysObj:
``` python
def int(arg:any,*base)->int:...
```

``` python
def bool(arg:any)->bool:...
```

``` python
def float(arg:any)->float:...
```

``` python
def str(arg:any)->str:...
```

``` python
def iter(arg:any)->any:...
```

``` python
def range(*ax)->any:...
```

``` python
def print(*val,**ops):...
```

``` python
def __setitem__(obj:any,key:any,val:any)->any:...
```

``` python
def __getitem__(obj:any,key:any)->any:...
```

``` python
def type(arg:any)->any:...
```

``` python
def len(arg:any)->int:...
```

``` python
def list(*val)->any:...
```

``` python
def dict(*val)->any:...
```

``` python
def tuple(arg:any)->any:...
```

``` python
def hex(val:int)->str:...
```

``` python
def ord(val:str)->int:...
```

``` python
def chr(val:int)->str:...
```

``` python
def bytes(val:any)->bytes:...
```

``` python
def cformat(fmt:str,*var)->str:...
```

``` python
def id(obj:any)->int:...
```

``` python
def open(path:str,mode:str)->object:...
```

``` python
def dir(obj:any)->list:...
```

``` python
def exec(code:str):...
```

``` python
def eval(code:str)->any:...
```

``` python
def getattr(obj:object,name:str)->any:...
```

``` python
def setattr(obj:object,name:str,val:any):...
```

``` python
def hasattr(obj:object,name:str)->int:...
```

``` python
def exit():...
```

``` python
def input(*info)->str:...
```

``` python
def help(name:str):...
```

``` python
def reboot():...
```

``` python
def clear():...
```

``` python
def gcdump():...
```

### class RangeObj:
``` python
def __next__(self)->any:...
```

### class StringObj:
``` python
def __next__(self)->any:...
```

