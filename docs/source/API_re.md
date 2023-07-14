# re 模块 API 文档

## API

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



## Examples

### sub.py

```python
import re
phone = "2004-959-559 # this is a phone number"
num = re.sub('#.*$', "", phone)
print("the phone number is: ", num)
num = re.sub('\\D', "", phone)
print("the phone number is: ", num)
```
### findall.py

```python
import re
pattern = re.compile('(\\d{4})-([1-9]|1[0-2])-([1-9]|[1-2][0-9]|3[01])\\b')
s = 'date: 2020-1-1, 2022-12-22, 2018-3-31. Wrong format: 2031-13-31, 2032-12-33 ...'
result1 = pattern.findall(s)
print(result1)
result2 = pattern.sub('\\1',s)
print(result2)

```
### search.py

```python
import re
print(re.search('www', 'www.runoob.com').span(0))
print(re.search('com', 'www.runoob.com').span(0)) 

```
### match.py

```python
import re

line = "Cats are smarter than dogs"

m = re.match("(.*) are (.*?) .*", line, re.M | re.I)

if m:
    print("matchObj.group(0) : ", m.group(0))
    print("matchObj.group(1) : ", m.group(1))
    print("matchObj.group(2) : ", m.group(2))
else:
    print("No match!!")

```
