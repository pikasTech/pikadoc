# socket 模块 API 文档

## API

### class socket(_socket.socket):
``` python
def __init__(self,*vars):...
```

``` python
def bind(self,host_port):...
```

``` python
def listen(self,num):...
```

``` python
def accept(self):...
```

``` python
def send(self,data):...
```

``` python
def close(self):...
```

``` python
def connect(self,host_port):...
```

``` python
def recv(self,num):...
```

``` python
def setblocking(self,sta):...
```

``` python
def gethostname():...
```



## Examples

### socket_thread.py

```python
import socket
import _thread
import random
import time

test_finished = False
server_started = False


def socket_server_task(host, port):
    """
    socket 服务器任务
    :return:
    """
    print("socket server start:", host, port)
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind((host, port))
    s.listen(5)
    print("socket server waiting accept")
    global server_started
    server_started = True
    accept, addr = s.accept()
    print("socket server accepted at", addr)
    while True:
        try:
            data = accept.recv(1024)
            print('socket server recv:', data.decode())
            accept.send(data)
        except Exception:
            print('socket server closing accept')
            accept.close()
            break
    print("socket server closing")
    s.close()
    global test_finished
    test_finished = True


def socket_server_init(host='0.0.0.0', port=36500):
    _thread.start_new_thread(socket_server_task, (host, port))


def socket_client_task(host, port):
    print("socket client start:", host, port)
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client.connect((host, port))
    client.send("hello".encode())
    recv = client.recv(1024).decode()
    print("client recv:", recv)
    client.close()


def socket_server_test(host='0.0.0.0', port=36500):
    _thread.start_new_thread(socket_client_task, (host, port))


test_port = random.randint(10000, 65535)
socket_server_init(port=test_port)
while not server_started:
    time.sleep(0.1)
socket_server_test(port=test_port)
while not test_finished:
    time.sleep(0.1)

```
### server_client.py

```python
import socket
import random

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = "127.0.0.1"
port = 9999 + random.randint(0, 1000)
print("port:", port)
server.bind((host, port))
server.listen(5)

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect((host, port))

accept, addr = server.accept()

print("recv from client: %s" % str(addr))

client.send("send test from client".encode())
print("server recv:", accept.recv(1024).decode())

accept.send("send test from server".encode())
print("client recv:", client.recv(1024).decode())

accept.close()
client.close()
server.close()

```
### gethostname.py

```python
import socket

hostname = socket.gethostname()
print(hostname)

```
### socket_json.py

```python
import socket
import _thread
import random
import time
import json

test_finished = False
server_started = False
test_data = {
    'result': {
        'a_a': {
            'value': 0.290000, 'desc': 'A 相电流'
        }
    }, 'code': 0
}


def socket_server_task(host, port):
    """
    socket 服务器任务
    :return:
    """
    print("socket server start:", host, port)
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    s.bind((host, port))
    s.listen(5)
    global server_started
    server_started = True
    while True:
        try:
            print("socket server waiting accept")
            accept, addr = s.accept()
            print("socket server accepted at", addr)
            while True:
                data = accept.recv(1024)
                print('socket server recv:', data.decode())
                # accept.send(data)
                accept.send(json.dumps(test_data))
        except Exception:
            print('socket server closing accept')
            accept.close()
            break
    print("socket server closing")
    s.close()
    global test_finished
    test_finished = True


def socket_server_init(host='0.0.0.0', port=36500):
    _thread.start_new_thread(socket_server_task, (host, port))


def socket_client_task(host, port):
    print("socket client start:", host, port)
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client.connect((host, port))
    for i in range(2):
        client.send("hello".encode())
        recv = client.recv(1024).decode()
        print("client recv:", recv)
    client.close()


def socket_server_test(host='0.0.0.0', port=36500):
    _thread.start_new_thread(socket_client_task, (host, port))


test_port = random.randint(10000, 65535)
socket_server_init(port=test_port)
while not server_started:
    time.sleep(0.1)
socket_server_test(port=test_port)
while not test_finished:
    time.sleep(0.1)

```
