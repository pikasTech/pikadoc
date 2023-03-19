# unittest 模块 API 文档

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

