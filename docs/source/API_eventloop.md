# eventloop 模块 API 文档

## API

### class EventTask:
Task Item of EventLoop


``` python
def __init__(self,func,callback,args,period_ms,delay_ms):...
```

:param func: function to be called

:param callback: callback function

:param args: arguments of func

:param period_ms: period of periodic task


### class EventLoop:
Event Loop


``` python
def __init__(self,period_ms=100,thread_stack=0):...
```

:param period_ms: period of loop

:param thread_stack: stack size of thread


``` python
def _add_task(self,task_name,func,callback,args,period_ms,delay_ms):...
```

``` python
def start_new_task(self,func,args,is_periodic=True,period_ms=1000,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop

:param task_name: name of task

:param func: function to be called

:param period_ms: period of task

:param callback: callback function

:param args: arguments of func


``` python
def start_new_task_once(self,func,args,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop, run once

:param task_name: name of task

:param func: function to be called

:param callback: callback function

:param args: arguments of func


``` python
def start_new_task_periodic(self,func,args,period_ms=1000,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop, run periodically

:param task_name: name of task

:param func: function to be called

:param period_ms: period of task

:param callback: callback function

:param args: arguments of func


``` python
def remove_task(self,task_name):...
```

Remove a task from EventLoop

:param task_name: name of task


``` python
def _run_task(self,task:EventTask):...
```

``` python
def _run_thread(self):...
```

``` python
def start(self):...
```

Start EventLoop


``` python
def stop(self):...
```

Stop EventLoop


``` python
def set_debug(enable:bool):...
```

``` python
def _debug(*args):...
```

``` python
def _get_default_event_loop():...
```

``` python
def start_new_task(func,args,is_periodic=True,period_ms=1000,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop

:param task_name: name of task

:param func: function to be called

:param period_ms: period of task

:param callback: callback function

:param args: arguments of func


``` python
def start_new_task_once(func,args,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop, run once

:param task_name: name of task

:param func: function to be called

:param callback: callback function

:param args: arguments of func


``` python
def start_new_task_periodic(func,args,period_ms=1000,callback=None,task_name=None,delay_ms=None):...
```

Add a task to EventLoop, run periodically

:param task_name: name of task

:param func: function to be called

:param period_ms: period of task

:param callback: callback function

:param args: arguments of func


``` python
def remove_task(task_name):...
```

Remove a task from EventLoop

:param task_name: name of task


``` python
def stop():...
```

Stop EventLoop


``` python
def start():...
```

Start EventLoop


``` python
def __del__():...
```



## Examples

### test2.py

```python
import time
from eventloop import EventLoop

run_time = 0

eventloop.set_debug(True)


def test_func(arg1, arg2):
    global run_time
    run_time += 1
    print("Running test function with arguments:", arg1, arg2)
    return arg1 + arg2


def test_func2(arg1, arg2):
    print("test function 2 with arguments:", arg1, arg2)
    return arg1 + arg2


def test_callback(res):
    print("Running test callback function", res)
    assert res == "Hello World"


# Test case 2: Add and run a periodic task
event_loop = EventLoop(period_ms=10)

event_loop.start_new_task_periodic(
    test_func, ("Hello", " World"),
    period_ms=100,
    callback=test_callback
)

event_loop.start_new_task(
    test_func2, ("Hello", " World"),
    is_periodic=True,
    period_ms=20,
    callback=test_callback
)

event_loop.start()

# Sleep for enough time to allow the periodic task to run multiple times
while run_time < 3:
    time.sleep(0.1)

event_loop.stop()

# Test case 3: Test removing a task
event_loop.start_new_task_periodic(
    test_func, ("Hello", " World"), callback=test_callback, task_name="test_task_remove")
event_loop.remove_task("test_task_remove")

print(event_loop._tasks)
assert "test_task_remove" not in event_loop._tasks, "Failed to remove the task"

```
### once2.py

```python
import eventloop
from PikaStdLib import MemChecker
import time

eventloop._is_debug = True
expect_finished = 10
finished = 0

def test_func(arg1, arg2):
    global finished
    finished += 1
    print("finished:", finished)
    print("Running test function with arguments:", arg1, arg2)
    MemChecker().now()


MemChecker().now()
for i in range(expect_finished):
    eventloop.start_new_task_once(
        test_func, ("Hello", " World"), delay_ms=10)
MemChecker().now()

while finished < expect_finished:
    time.sleep(0.1)
eventloop.stop()

```
### once1.py

```python
import eventloop
from PikaStdLib import MemChecker
import time

eventloop._is_debug = True
expect_finished = 10
finished = 0

def test_func(arg1, arg2):
    global finished
    finished += 1
    print("finished:", finished)
    print("Running test function with arguments:", arg1, arg2)
    MemChecker().now()


MemChecker().now()
for i in range(expect_finished):
    eventloop.start_new_task_once(
        test_func, ("Hello", " World"))
MemChecker().now()

while finished < expect_finished:
    time.sleep(0.1)
eventloop.stop()

```
### delay1.py

```python
import time
from eventloop import EventLoop

run_time = 0

eventloop.set_debug(True)


def test_func(arg1, arg2):
    global run_time
    run_time += 1
    print("Running test function with arguments:", arg1, arg2)
    return arg1 + arg2


def test_func2(arg1, arg2):
    print("test function 2 with arguments:", arg1, arg2)
    return arg1 + arg2


def test_callback(res):
    print("Running test callback function", res)
    assert res == "Hello World"


# Test case 2: Add and run a periodic task

eventloop.start_new_task_once(
    test_func, ("Hello", " World"),
    callback=test_callback,
    delay_ms=200
)

eventloop.start_new_task(
    test_func2, ("Hello", " World"),
    is_periodic=True,
    period_ms=20,
    callback=test_callback
)

# Sleep for enough time to allow the periodic task to run multiple times
while run_time < 1:
    time.sleep(0.1)

```
### test1.py

```python
import time
import eventloop
from eventloop import EventLoop

finished = False

eventloop.set_debug(True)


def test_func(arg1, arg2):
    print("Running test function with arguments:", arg1, arg2)
    return arg1 + arg2


def test_callback(res):
    global finished
    print("Running test callback function", res)
    assert res == "Hello World"
    finished = True


# Test case 1: Add and run a one-time task
event_loop = EventLoop(period_ms=10)

event_loop.start_new_task_once(
    test_func, ("Hello", " World"), callback=test_callback)
event_loop.start()

# Sleep for enough time to allow the one-time task to run
while not finished:
    time.sleep(0.1)

event_loop.stop()

```
### test3.py

```python
import time
import eventloop

run_time = 0

eventloop.set_debug(True)


def test_func(arg1, arg2):
    global run_time
    run_time += 1
    print("Running test function with arguments:", arg1, arg2)
    return arg1 + arg2


def test_func2():
    print("test function 2")


def test_func3(arg):
    print("test function 3 with argument:", arg)


def test_callback(res):
    print("Running test callback function", res)
    assert res == "Hello World"


eventloop.start_new_task(test_func, ("Hello", " World"))

eventloop.start_new_task_periodic(
    test_func2, (),
    period_ms=20
)

eventloop.start_new_task_once(test_func3, ("Hello"))

# Sleep for enough time to allow the periodic task to run multiple times
while run_time < 3:
    time.sleep(0.1)

# Test case 3: Test removing a task
eventloop.start_new_task_periodic(
    test_func, ("Hello", " World"), callback=test_callback, task_name="test_task_remove")
eventloop.remove_task("test_task_remove")

```
