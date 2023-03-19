# re 模块 API 文档

``` python
def __init__():...
```

### class Pattern:
``` python
def __init__(self):...
```

``` python
def __del__(self):...
```

``` python
def findall(self,subject:str,*flags)->list:...
```

``` python
def sub(self,repl:str,subjet:str,*count__flags)->str:...
```

``` python
def subn(self,repl:str,subjet:str,*count__flags)->list:...
```

``` python
def match(self,subject:str,*flags)->Match:...
```

``` python
def fullmatch(self,subject:str,*flags)->Match:...
```

``` python
def search(self,subject:str,*flags)->Match:...
```

``` python
def split(self,subject:str,*maxsplit__flags)->list:...
```

### class Match:
``` python
def __init__(self):...
```

``` python
def __del__(self):...
```

``` python
def group(self,*n)->str:...
```

``` python
def groups(self)->list:...
```

``` python
def span(self,*group_n)->list:...
```

``` python
def findall(pattern:str,subject:str,*flags)->list:...
```

``` python
def sub(pattern:str,repl:str,subjet:str,*count__flags)->str:...
```

``` python
def match(pattern:str,subject:str,*flags)->Match:...
```

``` python
def fullmatch(pattern:str,subject:str,*flags)->Match:...
```

``` python
def search(pattern:str,subject:str,*flags)->Match:...
```

``` python
def compile(pattern:str,*flags)->Pattern:...
```

``` python
def escape(pattern:str)->str:...
```

``` python
def subn(pattern:str,repl:str,subjet:str,*count__flags)->list:...
```

``` python
def split(pattern:str,subject:str,*maxsplit__flags)->list:...
```

