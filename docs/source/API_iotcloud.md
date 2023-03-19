# iotcloud 模块 API 文档

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

