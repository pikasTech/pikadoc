# unittest 模块 API 文档

## API

### class TestResult:
``` python
def __init__(self):...
```

``` python
def wasSuccessful(self):...
```

``` python
def __str__(self):...
```

### class TestCase:
``` python
def assertEqual(self,x,y):...
```

``` python
def assertNotEqual(self,x,y):...
```

``` python
def assertLessEqual(self,x,y):...
```

``` python
def assertGreaterEqual(self,x,y):...
```

``` python
def assertTrue(self,x):...
```

``` python
def assertFalse(self,x):...
```

``` python
def assertIs(self,x,y):...
```

``` python
def assertIsNot(self,x,y):...
```

``` python
def assertIsNone(self,x):...
```

``` python
def assertIsNotNone(self,x):...
```

``` python
def assertIn(self,x,y):...
```

``` python
def assertNotIn(self,x,y):...
```

``` python
def run(self,result:TestResult,suite_name):...
```

### class TestSuite:
``` python
def __init__(self,name):...
```

``` python
def addTest(self,case):...
```

``` python
def run(self,result:TestResult):...
```

### class TextTestRunner:
``` python
def run(self,suite:TestSuite):...
```



## Examples

### test2.py

```python
import unittest


class TestUnittestAssertions(unittest.TestCase):
    def testEqual(self):
        print("in testEqual...")
        self.assertEqual(0, 0)

    def testTrue(self):
        print("in testTrue...")
        self.assertTrue(True)

    def testFalse(self):
        print("in testFalse...")
        self.assertFalse(False)

    def testFalse2(self):
        print("in testFalse2...")
        self.assertFalse(True)


suit = unittest.TestSuite("test1")
suit.addTest(TestUnittestAssertions())
runner = unittest.TextTestRunner()
res = runner.run(suit)

```
### test1.py

```python
import unittest


class TestUnittestAssertions(unittest.TestCase):
    def testEqual(self):
        print("in testEqual...")
        self.assertEqual(0, 0)

    def testTrue(self):
        print("in testTrue...")
        self.assertTrue(True)

    def testFalse(self):
        print("in testFalse...")
        self.assertFalse(False)

suit = unittest.TestSuite("test1")
suit.addTest(TestUnittestAssertions())
runner = unittest.TextTestRunner()
res = runner.run(suit)

```
### test3.py

```python
import socket
import random
import unittest


class TestUnittestAssertions(unittest.TestCase):
    def testSocket(self):
        server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        host = "127.0.0.1"
        port = 9999 + random.randint(0, 1000) + 1
        print("port:", port)
        server.bind((host, port))
        server.listen(5)
        
        client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        client.connect((host, port))
        
        accept, addr = server.accept()
        self.assertEqual(addr, "127.0.0.1")
        
        print("recv from client: %s" % str(addr))
        
        client.send("send test from client".encode())
        print("server recv:", accept.recv(1024).decode())
        
        accept.send("send test from server".encode())
        print("client recv:", client.recv(1024).decode())
        
        accept.close()
        client.close()
        server.close()


suit = unittest.TestSuite("test1")
suit.addTest(TestUnittestAssertions())
runner = unittest.TextTestRunner()
res = runner.run(suit)

```
