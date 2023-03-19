# os 模块 API 文档

### class fileStat:
``` python
def st_size(self)->int:...
```

``` python
def __init__(self):...
```

``` python
def mkdir(self,path:str,*mode):...
```

``` python
def rmdir(self,path:str):...
```

``` python
def chdir(self,path:str):...
```

``` python
def listdir(self,path:str)->list:...
```

``` python
def getcwd(self)->str:...
```

``` python
def open(self,filename:str,flags:int)->FILE:...
```

``` python
def read(self,fd:FILE,len:int)->str:...
```

``` python
def write(self,fd:FILE,buf:any)->int:...
```

``` python
def lseek(self,fd:FILE,pos:int,how:int)->int:...
```

``` python
def close(self,fd:FILE):...
```

``` python
def fstat(self,fd:FILE)->fileStat:...
```

``` python
def remove(self,filename:str):...
```

