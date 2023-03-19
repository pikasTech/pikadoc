# STM32F4 模块 API 文档

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

### class ADC(PikaStdDevice.ADC):
``` python
def platformEnable():...
```

``` python
def platformRead():...
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

