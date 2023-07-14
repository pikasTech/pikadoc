# fsm 模块 API 文档

## API

``` python
def debug(*info):...
```

``` python
def error(*info):...
```

``` python
def info(*info):...
```

### class State:
``` python
def __init__(self,name:str,function:callable):...
```

``` python
def getName(self):...
```

``` python
def getFunction(self):...
```

``` python
def __str__(self):...
```

### class StateMachine:
``` python
def __init__(self):...
```

``` python
def addState(self,state:State):...
```

``` python
def getStateByName(self,stateName:str):...
```

``` python
def getStateByFunction(self,stateFunction:callable):...
```

``` python
def getState(self,stateNameOrFn:str):...
```

``` python
def setCurrentState(self,stateNameOrFn:str)->int:...
```

``` python
def runCurrentState(self)->str:...
```

``` python
def mainLoop(self,initStateName:str):...
```

``` python
def start(self,initStateName:str):...
```

``` python
def stop(self):...
```

``` python
def wait(self):...
```

``` python
def _initDefaultStateMachine():...
```

``` python
def addState(stateFunction:callable,stateName:str='default'):...
```

``` python
def start(initStateName:str):...
```

``` python
def stop():...
```

``` python
def wait():...
```



## Examples

### test1.py

```python
import fsm


def state1():
    print("state1")
    return "state2"


def state2():
    print("state2")
    return state3


def state3():
    print("state3")
    fsm.stop()
    return "state1"


def test_fsm():
    fsm.addState(state1, "state1")
    fsm.addState(state2, "state2")
    fsm.addState(state3, "state3")
    fsm.start("state1")
    fsm.wait()

test_fsm()

```
