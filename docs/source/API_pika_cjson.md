# pika_cjson 模块 API 文档

## API

### class cJSON(TinyObj):
``` python
def print(self)->str:...
```

``` python
def __del__(self):...
```

``` python
def __init__(self):...
```

``` python
def getObjectItem(self,string:str)->cJSON:...
```

``` python
def getArrayItem(self,index:int)->cJSON:...
```

``` python
def getArraySize(self)->int:...
```

``` python
def getType(self)->int:...
```

``` python
def getNext(self)->cJSON:...
```

``` python
def getPrev(self)->cJSON:...
```

``` python
def getChild(self)->cJSON:...
```

``` python
def getValueString(self)->str:...
```

``` python
def getValueInt(self)->int:...
```

``` python
def getValueDouble(self)->float:...
```

``` python
def getString(self)->str:...
```

``` python
def getValue(self)->any:...
```

``` python
def isInvalid(self)->int:...
```

``` python
def isFalse(self)->int:...
```

``` python
def isTrue(self)->int:...
```

``` python
def isBool(self)->int:...
```

``` python
def isNull(self)->int:...
```

``` python
def isNumber(self)->int:...
```

``` python
def isString(self)->int:...
```

``` python
def isArray(self)->int:...
```

``` python
def isObject(self)->int:...
```

``` python
def isRaw(self)->int:...
```

``` python
def addItemToArray(self,item:cJSON):...
```

``` python
def addItemToObject(self,string:str,item:cJSON):...
```

``` python
def Parse(value:str)->cJSON:...
```

### class Null(cJSON):
``` python
def __init__(self):...
```

### class True_(cJSON):
``` python
def __init__(self):...
```

### class False_(cJSON):
``` python
def __init__(self):...
```

### class Bool(cJSON):
``` python
def __init__(self,bolean:int):...
```

### class Number(cJSON):
``` python
def __init__(self,num:float):...
```

### class String(cJSON):
``` python
def __init__(self,string:str):...
```

### class Raw(cJSON):
``` python
def __init__(self,raw:str):...
```

### class Array(cJSON):
``` python
def __init__(self):...
```

### class Object(cJSON):
``` python
def __init__(self):...
```

### class StringReference(cJSON):
``` python
def __init__(self,string:str):...
```

### class ObjectReference(cJSON):
``` python
def __init__(self,child:cJSON):...
```

### class ArrayReference(cJSON):
``` python
def __init__(self,child:cJSON):...
```



## Examples

### test4.py

```python
import pika_cjson

data1 = '{"data":{"requestSocialInsuranceFromYangCheng":"","authenticationComparison":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"jell","facediscernMode":"01","hospitalCode":"102"},"success":true,"resultCode":"0000","time":"2022-05-20 14:10:27","message":"ok"}'

a = pika_cjson.Parse(data1)
a.print()

```
### test2.py

```python
import pika_cjson

data1 = "{\"data\":{\"validTime\":28800,\"token\":\"3E6EA1D907B9CFEB6AB1DECB5667E4A7\"},\"success\":true,\"resultCode\":\"0000\"} "
a = pika_cjson.Parse(data1)
a.print()

```
### test5.py

```python
import pika_cjson

data1 = "{\"data\":{\"requestSocialInsuranceFromYangCheng\":\"\",\"authenticationComparison\":\"no\",\"startupLogo\":\"4\",\"cardType\":\"00,01,02,03,04\",\"synfromhis\":\"no\",\"alarmThresholdValue\":\"37.2\",\"hospitalName\":\"余杭农贸市场\",\"facediscernMode\":\"01\",\"hospitalCode\":\"102\"},\"success\":true,\"resultCode\":\"0000\",\"time\":\"2022-05-20 14:10:27\",\"message\":\"操作成功\"} "

a = pika_cjson.Parse(data1)
a.print()

```
### test7.py

```python
import pika_cjson as cjson

root = cjson.Object()
root.addItemToObject('name', cjson.String('mculover666'))
root.addItemToObject('age', cjson.Number(22))
root.addItemToObject('weight', cjson.Number(55.5))
address = cjson.Object()
address.addItemToObject('country', cjson.String('China'))
address.addItemToObject('zip-code', cjson.String('111111'))
root.addItemToObject('address', address)
skill = cjson.Array()
skill.addItemToArray(cjson.String('c'))
skill.addItemToArray(cjson.String('Java'))
skill.addItemToArray(cjson.String('Python'))
root.addItemToObject('skill', skill)
root.addItemToObject('student', cjson.False_())
root.print()

# data1 = "{"data":{"name":"11"}}"
# data1 = "{"data":{"token":"3E6EA1D907B9CFEB6AB1DECB5667E4A7","resultCode":"0000"},"resultCode":"0000"}"
#data1 = '{"data":{"requestSocialInsuranceFromYangCheng":"","authenticationComparison":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"jell","facediscernMode":"01","hospitalCode":"102"},"success":true,"resultCode":"0000","time":"2022-05-20 14:10:27","message":"ok"}'
#data1 = '{"data":{"validTime":28800,"token":"3E6EA1D907B9CFEB6AB1DECB5667E4A7"},"success":true,"resultCode":"0000"}'
# data1 = "{"data":{"jjj":"","333":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"jell","facediscernMode":"01","hospitalCode":"102"},"success":true,"resultCode":"0000","time":"2022-05-20 14:10:27","message":"ok"}"
#data1 = "{\"data\":{\"requestSocialInsuranceFromYangCheng\":\"\",\"authenticationComparison\":\"no\",\"startupLogo\":\"4\",\"cardType\":\"00,01,02,03,04\",\"synfromhis\":\"no\",\"alarmThresholdValue\":\"37.2\",\"hospitalName\":\"余杭农贸市场\",\"facediscernMode\":\"01\",\"hospitalCode\":\"102\"},\"success\":true,\"resultCode\":\"0000\",\"time\":\"2022-05-20 14:10:27\",\"message\":\"操作成功\"} "
#data1 = '{"sites": [{ "name":"Google", "info":[ "Android", "Google 搜索", "Google 翻译" ] }],"arraytest":{"test1":["c", "Java", "Python"],"test2":["c2", "Java2", "Python2"]},"data":{"requestSocialInsuranceFromYangCheng":"","authenticationComparison":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"余杭农贸市场","facediscernMode":"01","hospitalCode":"102"},"success":"true","resultCode":"0000","time":"2022-05-20 14:10:27","message":"操作成功"}'
data1 = '{"sites": [{ "name":"Google", "info":[ "Android", "Google search", "Google translation" ] },{ "name":"Runoob", "info":[ "ciniao jiaoc", "ciniao tool", "ciniao wechat" ] },{ "name":"Taobao", "info":[ "taobao", "shopping" ] }],"arraytest":{"test1":["c", "Java", "Python"],"test2":["c2", "Java2", "Python2"]},"data":{"requestSocialInsuranceFromYangCheng":"","authenticationComparison":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"余杭农贸市场","facediscernMode":"01","hospitalCode":"102"},"success":"true","resultCode":"0000","time":"2022-05-20 14:10:27","message":"操作成功"}'

a = cjson.Parse(data1)
a.print()
success = a.getObjectItem("success")
success.print()
value = success.getValueString()
print(value)
data = a.getObjectItem("data")
ret = data.isNull()
if ret == 0:
    startupLogo = data.getObjectItem("startupLogo")
    startupLogo.print()
    startupLogovalue = startupLogo.getValueString()
    print(startupLogovalue)
else:
    print("data is null")

sites = a.getObjectItem("sites")
sites_num = sites.getArraySize()
for i in range(0, sites_num):
    sites_item = sites.getArrayItem(i)
    print("-------sites array ------")
    # sites_item.print()
    name = sites_item.getObjectItem("name")
    namevalue = name.getValueString()
    print(namevalue)
    print("-------sites array  info------")
    info = sites_item.getObjectItem("info")
    info_num = info.getArraySize()
    print(info_num)
    for j in range(0, info_num):
        info_item = info.getArrayItem(j)
        # print(info_item)
        # info_item.print()
        infodata = info_item.getValueString()
        print(infodata)

```
### test1.py

```python
import pika_cjson

data1 = '{"data":{"validTime":28800,"token":"3E6EA1D907B9CFEB6AB1DECB5667E4A7"},"success":true,"resultCode":"0000"}'
a = pika_cjson.Parse(data1)
a.print()

```
### test6.py

```python
import pika_cjson

data1 = '{"array33":["c","Java","Python"],"data":{"requestSocialInsuranceFromYangCheng":"","authenticationComparison":"no","startupLogo":"4","cardType":"00,01,02,03,04","synfromhis":"no","alarmThresholdValue":"37.2","hospitalName":"余杭农贸市场","facediscernMode":"02","hospitalCode":"102"},"success":true,"resultCode":"0000","time":"2022-05-20 14:10:27","message":"操作成功"}'

a = pika_cjson.Parse(data1)
a.print()

```
### test3.py

```python
import pika_cjson as cjson

root = cjson.Object()
root.addItemToObject('name', cjson.String('mculover666'))
root.addItemToObject('age', cjson.Number(22))
root.addItemToObject('weight', cjson.Number(55.5))
address = cjson.Object()
address.addItemToObject('country', cjson.String('China'))
address.addItemToObject('zip-code', cjson.String('111111'))
root.addItemToObject('address', address)
skill = cjson.Array()
skill.addItemToArray(cjson.String('c'))
skill.addItemToArray(cjson.String('Java'))
skill.addItemToArray(cjson.String('Python'))
root.addItemToObject('skill', skill)
root.addItemToObject('student', cjson.False_())
root.print()

```
