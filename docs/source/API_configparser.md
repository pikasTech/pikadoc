# configparser 模块 API 文档

### class ConfigParser():
``` python
def _parse(self):...
```

``` python
def sections(self):...
```

``` python
def options(self,section):...
```

``` python
def get(self,section,option):...
```

``` python
def set(self,section,option,value):...
```

``` python
def __setitem__(self,__key,__val):...
```

``` python
def __getitem__(self,__key):...
```

``` python
def items(self,section):...
```

``` python
def __str__(self):...
```

``` python
def write(self,file_name):...
```

``` python
def read_string(self,content):...
```

``` python
def read(self,file_name):...
```

``` python
def _getvalue(stmt):...
```

