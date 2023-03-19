# pika_cjson 模块 API 文档

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

