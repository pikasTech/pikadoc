# random 模块 API 文档

## API

``` python
def __init__(self):...
```

Initialize the random number generator.


``` python
def random()->float:...
```

Return a random float in the range [0.0, 1.0).


``` python
def randint(a:int,b:int)->int:...
```

Return a random integer in the range [a, b], including both end points.


``` python
def randrange(start:int,stop:int,step:int)->int:...
```

Return a randomly-selected element from range(start, stop, step).


``` python
def seed(a:int)->None:...
```

Initialize the random number generator.


``` python
def uniform(a:float,b:float)->float:...
```

Return a random float in the range [a, b).




## Examples

