# W801Device 模块 API 文档

## API

### class GPIO(PikaStdDevice.GPIO):
``` python
def platformHigh():...
```

``` python
def platformLow():...
```

``` python
def platformEnable():...
```

``` python
def platformDisable():...
```

``` python
def platformSetMode():...
```

``` python
def platformRead():...
```

### class Time(PikaStdDevice.Time):
``` python
def sleep_s(s:int):...
```

``` python
def sleep_ms(ms:int):...
```

### class UART(PikaStdDevice.UART):
``` python
def platformEnable():...
```

``` python
def platformWrite():...
```

``` python
def platformRead():...
```

### class PWM(PikaStdDevice.PWM):
``` python
def platformEnable():...
```

``` python
def platformSetFrequency():...
```

``` python
def platformSetDuty():...
```

### class IIC(PikaStdDevice.IIC):
``` python
def platformEnable():...
```

``` python
def platformWrite():...
```

``` python
def platformRead():...
```

### class ADC(TinyObj):
``` python
def __init__():...
```

``` python
def init():...
```

``` python
def setChannel(channel:int):...
```

``` python
def enable():...
```

``` python
def read()->float:...
```

``` python
def platformEnable():...
```

``` python
def platformRead():...
```



## Examples

