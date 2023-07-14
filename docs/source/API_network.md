# network 模块 API 文档

## API

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



## Examples

### network_config.py

```python
import network

wlan = network.WLAN(network.STA_IF)
wlan.active(True)
wlan.connect('testssid', 'testpassword')
wlan.config(ssid='configssid', channel=11)
print(wlan.config('ssid'), wlan.config('channel'))
wlan.close()

```
### network_connect.py

```python
import network

wlan = network.WLAN(network.STA_IF)
wlan.active(True)
wlan.connect('testssid', 'testpassword')
wlan.isconnected()
wlan.close()

```
### network_scan.py

```python
import network

wlan = network.WLAN(network.STA_IF)
wlan.active(True)
wlan.scan()
wlan.close()

```
