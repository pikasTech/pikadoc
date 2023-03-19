# network 模块 API 文档

### class WLAN(_network.WLAN):
``` python
def __init__(self,interface_id:int):...
```

``` python
def active(self,is_active=None):...
```

``` python
def connect(self,ssid=None,key=None,bssid=None):...
```

``` python
def disconnect(self):...
```

``` python
def status(self,param=None):...
```

``` python
def isconnected(self)->int:...
```

``` python
def config(self,*para,**kwargs):...
```

``` python
def ifconfig(self,config=None):...
```

``` python
def scan(self):...
```

