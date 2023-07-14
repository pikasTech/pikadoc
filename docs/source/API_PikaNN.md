# PikaNN 模块 API 文档

## API

### class net:
``` python
def __init__(self):...
```

``` python
def load(self):...
```

``` python
def unload(self):...
```

``` python
def run(self):...
```

``` python
def test():...
```



## Examples

### PikaNN_test1.py

```python
import PikaNN as nn
mnist=nn.net()
mnist.load()
mnist.run()
mnist.unload()
```
