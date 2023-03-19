# CH582 模块 API 文档

### class GPIO(PikaStdDevice.GPIO):
``` python
def platformHigh(self):...
```

``` python
def platformLow(self):...
```

``` python
def platformEnable(self):...
```

``` python
def platformDisable(self):...
```

``` python
def platformSetMode(self):...
```

``` python
def platformRead(self):...
```

### class Time(PikaStdDevice.Time):
``` python
def sleep_s(self,s:int):...
```

``` python
def sleep_ms(self,ms:int):...
```

### class ADC(PikaStdDevice.ADC):
``` python
def platformEnable(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformDisable(self):...
```

### class UART(PikaStdDevice.UART):
``` python
def platformEnable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformDisable(self):...
```

### class IIC(PikaStdDevice.IIC):
``` python
def platformEnable(self):...
```

``` python
def platformDisable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformRead(self):...
```

