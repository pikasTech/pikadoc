# at_client 模块 API 文档

## API

``` python
def ClientCB(signal):...
```

### class Client:
``` python
def __init__(self,uart:PikaStdDevice.UART):...
```

``` python
def configMode(self):...
```

``` python
def cmd(self,cmd):...
```

``` python
def get(self,arg):...
```

``` python
def set(self,arg,val):...
```

``` python
def res(self):...
```

``` python
def __getattr__(self,name):...
```

``` python
def __setattr__(self,name,value):...
```



## Examples

