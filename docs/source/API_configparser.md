# configparser 模块 API 文档

## API

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



## Examples

### test2.py

```python
import configparser

fd = open('test/assets/widget_config.ini', 'r')
s = fd.read(-1)
print(s)
config = configparser.ConfigParser()
config.read_string(s)
print(config)
font_color = config.get('文本控件_20030101', 'font_color')
type(font_color)
print(font_color)
fd.close()

```
### test1.py

```python
import configparser
from PikaStdLib import MemChecker
config = configparser.ConfigParser()

config_string = '[DEFAULT]\n\
ServerAliveInterval = 45\n\
Compression = yes\n\
CompressionLevel = 9\n\
ForwardX11 = yes\n\
\n\
[bitbucket.org]\n\
User = hg\n\
\n\
[topsecret.server.com]\n\
Port = 50022\n\
ForwardX11 = no\n\
content = http://sbkpda.hazz.hrss.gov.cn:9001/nontax_platforml/nontax/pay?Q=wj%2Bf'

config.read_string(config_string)

print('\n========== config_string ==========')
print(config_string)

print('\n===== config.sections() =====')
print(config.sections())

print('\n===== config.options("DEFAULT") =====')
print(config.options('DEFAULT'))
mem = MemChecker()

config.set('bitbucket.org', 'User', 'hhdd123')

print('\n========= config["bitbucket.org"] bitbucket.org ===========') 
print(config['bitbucket.org'])

section = config['bitbucket.org']
section['User'] = '3833qwe'

print('\n========= config["bitbucket.org"] ===========')
print(config['bitbucket.org'])

print('\n========= config.items("DEFAULT") ===========')
print(config.items('DEFAULT'))

print('\n=============== all ================')
print(config)

print("mem used now: %0.2f kB" % mem.getNow())
print("mem used max: %0.2f kB" % mem.getMax())

```
