# _thread 模块 API 文档

## API

``` python
def start_new_thread(function:any,args_:any):...
```

``` python
def stack_size(*size)->int:...
```



## Examples

### test2.py

```python
import time
import _thread

finished = False

def test_thread(arg):
    global finished
    for i in range(3):
        print(i)
        time.sleep(0.1)
    finished = True
    print('test_thread arg:', arg)
    assert arg == 'test'

# 开启线程 获取数据
_thread.start_new_thread(test_thread, ('test'))
while not finished:
    time.sleep(0.1)
time.sleep(0.1)

```
### thread_self.py

```python
import _thread
import time


class Test:
    _val = 1

    def __init__(self):
        self._val = 2
        _thread.start_new_thread(self.init, ())

    def init(self):
        print('self._val:', self._val)
        self._val = 3

test = Test()
while test._val != 3:
    time.sleep(0.1)

time.sleep(0.5)

```
### test1.py

```python
import _thread
import time

task1_finished = False
task2_finished = False


def task1():
    global task1_finished
    print("task1")
    for i in range(10):
        time.sleep(0.05)
        print("task1")
    task1_finished = True


def task2(sleep_time, loop_count):
    global task2_finished
    print("task2:", sleep_time, loop_count)
    for i in range(loop_count):
        time.sleep(sleep_time)
        print("task2")
    task2_finished = True


_thread.start_new_thread(task1, ())
_thread.start_new_thread(task2, (0.05, 10))

while not task1_finished or not task2_finished:
    time.sleep(0.1)

time.sleep(0.5)  # wait for threads to exit

```
