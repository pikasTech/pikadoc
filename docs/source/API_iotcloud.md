# iotcloud 模块 API 文档

## API

### class IOT:
``` python
def __init__(self):...
```

``` python
def randStr(self,len):...
```

``` python
def getTimeStamp(self,t):...
```

``` python
def urlEncode(self,s):...
```

``` python
def aliyun(self,clientId:str,productKey:str,deviceName:str,deviceSecret:str,signMethod="hmacmd5",regionID="cn-shanghai",ssl=False):...
```

``` python
def tencent(self,productId,deviceName,deviceSecret,signMethod="hmacsha1",expiryTime=3600,ssl=False):...
```

``` python
def onenet(self,productId,deviceName,accessKey,mode=ONENET_DEVICE,signMethod="hmacmd5",expiryTime=3600,ssl=False):...
```

``` python
def onenetMulti(self,productId,deviceId,apiKey):...
```

``` python
def connect(self,keepalive=600):...
```

``` python
def disconnect(self):...
```

``` python
def subsribe(self,topic,cb,qos=0):...
```

``` python
def publish(self,topic,payload,qos=0):...
```

``` python
def new():...
```



## Examples

### test_basic_tencent.py

```python
from PikaStdDevice import Time
import iotcloud


productKey = "xxxx"
deviceName = "test1"
deviceSecret = "xxxxx"
topic = productKey + "/" + deviceName + "/data"

print("iotcloud tencent iot hub test")
c = iotcloud.new()
if c.tencent(productKey, deviceName, deviceSecret):
    print("tencent iot hub init ok")
else:
    print("tencent iot hub init fail")


def up_cb(signal):
    recv_msg = c.client.getMsg(signal)
    recv_topic = c.client.getTopic(signal)
    recv_qos = c.client.getQos(signal)
    print("cb: %s-qos:%d-->>%s" % (recv_topic, recv_qos, recv_msg))

e = c.connect()
print("connect:", e)
if e == 0:
    print("subcribe status:", c.subsribe(topic, up_cb))

    for i in range(10):
        print("publish status:", c.publish(topic, '{"id":'+str(i)+'}'))
        Time.sleep_s(3)

a = c.disconnect()
print("disconnect status:", a)

```
### test_basic_aliyun.py

```python

from PikaStdDevice import Time
import iotcloud

clientId = "pikascript"
productKey = "xxx"
deviceName = "test1"
deviceSecret = "xxxxx"

topic = "/" + productKey + "/" + deviceName + "/user/update"

print("iotcloud aliyun test")
c = iotcloud.new()
c.aliyun(clientId, productKey, deviceName, deviceSecret)


def up_cb(signal):
    recv_msg = c.client.getMsg(signal)
    recv_topic = c.client.getTopic(signal)
    recv_qos = c.client.getQos(signal)
    print("cb: %s-qos:%d-->>%s" % (recv_topic, recv_qos, recv_msg))

e = c.connect()
print("connect:", e)
if e == 0:
    print("subcribe status:", c.subsribe(topic, up_cb))

    for i in range(10):
        print("publish status:", c.publish(topic, '{"id":'+str(i)+'}'))
        Time.sleep_s(3)

a = c.disconnect()
print("disconnect status:", a)


```
