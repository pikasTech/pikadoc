# mqtt 模块 API 文档

### class MQTT(_mqtt._MQTT):
``` python
def __init__(self,ip:str,port=1883,clinetID='mac',username='',password='',version='3.1.1',ca='',keepalive=60):...
```

``` python
def subscribe(self,topic,cb,qos=1):...
```

``` python
def publish(self,topic,payload,qos=1):...
```

``` python
def setWill(self,topic,payload,qos=1,retain=0):...
```

``` python
def unsubscribe(self,topic=''):...
```

