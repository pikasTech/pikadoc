# PikaStdDevice 模块 API 文档

## API

## PikaStdDevice

PikaStdDevice is a standard and abstract device module for PikaScript.

PikaStdDevice supplies the standard device API for users.

Document: https://pikadoc.readthedocs.io/en/latest/PikaStdDevice%20%E6%A0%87%E5%87%86%E8%AE%BE%E5%A4%87.html


### class GPIO(BaseDev):
``` python
def __init__(self):...
```

``` python
def setPin(self,pinName:str):...
```

Use the name of the pin to select the GPIO pin.

example: `"PA0"`, `"PA1"` ...


``` python
def setId(self,id:int):...
```

Use the id of the pin to select the GPIO pin.

example: 0, 1 ...


``` python
def getId(self)->int:...
```

Get the id of the pin.


``` python
def getPin(self)->str:...
```

Get the name of the pin.


``` python
def setMode(self,mode:str):...
```

Set the mode of the pin.

example: "in", "out" ...


``` python
def getMode(self)->str:...
```

Get the mode of the pin.


``` python
def setPull(self,pull:str):...
```

Set the pull of the pin.

example: `"up"`, `"down"`, `"none"` ...


``` python
def enable(self):...
```

Enable the pin.


``` python
def disable(self):...
```

Disable the pin.


``` python
def high(self):...
```

Set the pin to high.


``` python
def low(self):...
```

Set the pin to low.


``` python
def read(self)->int:...
```

Read the pin value.


``` python
def setCallBack(self,eventCallBack:any,filter:int):...
```

Add a callback function to the pin.

Example: 

``` python
def cb1(signal):
    print("cb1", signal)
io.setCallBack(cb1, io.SIGNAL_RISING)
```

The `signal` parameter is the signal type.

The callback function will be called when the signal is triggered.


``` python
def close(self):...
```

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

``` python
def Time()->time:...
```

use time module instead 


### class ADC(BaseDev):
``` python
def __init__(self):...
```

``` python
def setPin(self,pin:str):...
```

Use the name of the pin to select the ADC pin.

example: `"PA0"`, `"PA1"` ...


``` python
def enable(self):...
```

Enable the ADC.


``` python
def disable(self):...
```

Disable the ADC.


``` python
def read(self)->float:...
```

Read the ADC value.


``` python
def close(self):...
```

``` python
def platformEnable(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformDisable(self):...
```

### class DAC(BaseDev):
``` python
def __init__(self):...
```

``` python
def setPin(self,pin:str):...
```

Use the name of the pin to select the DAC pin.

example: `"PA0"`, `"PA1"` ...


``` python
def enable(self):...
```

Enable the DAC.


``` python
def disable(self):...
```

Disable the DAC.


``` python
def write(self,val:float):...
```

write the DAC value.


``` python
def close(self):...
```

### class UART:
``` python
def __init__(self):...
```

``` python
def setBaudRate(self,baudRate:int):...
```

Set the baud rate.


``` python
def setId(self,id:int):...
```

Set the id of the UART.


``` python
def setStopBits(self,stopBits:int):...
```

Set the stop bits of the UART.


``` python
def setParity(self,parity:int):...
```

Set the parity of the UART.


``` python
def setFlowControl(self,flowControl:int):...
```

Set the flow control of the UART.


``` python
def setDataBits(self,dataBits:int):...
```

Set the data bits of the UART.


``` python
def enable(self):...
```

Enable the UART.


``` python
def disable(self):...
```

Disable the UART.


``` python
def write(self,data:str):...
```

Write string to the UART.


``` python
def writeBytes(self,data:bytes,length:int):...
```

Write bytes to the UART.


``` python
def read(self,length:int)->str:...
```

Read string from the UART.


``` python
def readBytes(self,length:int)->bytes:...
```

Read bytes from the UART.


``` python
def setPinTX(self,pin:str):...
```

Remap the TX pin.


``` python
def setPinRX(self,pin:str):...
```

Remap the RX pin.


``` python
def setPinCTS(self,pin:str):...
```

Remap the CTS pin.


``` python
def setPinRTS(self,pin:str):...
```

Remap the RTS pin.


``` python
def close(self):...
```

``` python
def setCallBack(self,eventCallBack:any,filter:int):...
```

Add a callback function to the pin.

Example: 

``` python
def cb1(signal):
    print(uart.read(-1))
io.setCallBack(cb1, uart.SIGNAL_RX)
```


``` python
def platformEnable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformWriteBytes(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformReadBytes(self):...
```

``` python
def platformDisable(self):...
```

### class IIC(BaseDev):
``` python
def __init__(self):...
```

``` python
def setPinSCL(self,pin:str):...
```

Set the SCL pin.


``` python
def setPinSDA(self,pin:str):...
```

Set the SDA pin.


``` python
def setDeviceAddr(self,addr:int):...
```

Set the device address.


``` python
def enable(self):...
```

Enable the IIC.


``` python
def disable(self):...
```

Disable the IIC.


``` python
def write(self,addr:int,data:str):...
```

Write string to the IIC.


``` python
def writeBytes(self,addr:int,data:bytes,length:int):...
```

Write bytes to the IIC.


``` python
def read(self,addr:int,length:int)->str:...
```

Read string from the IIC.


``` python
def readBytes(self,addr:int,length:int)->bytes:...
```

Read bytes from the IIC.


``` python
def platformEnable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformWriteBytes(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformReadBytes(self):...
```

``` python
def platformDisable(self):...
```

### class PWM(BaseDev):
``` python
def __init__(self):...
```

``` python
def setName(self,name:str):...
```

Use the device name to select the PWM pin.

exmpale: `"PWM0"`, `"PWM1"` ...


``` python
def getName(self)->str:...
```

Get the device name.


``` python
def setChannel(self,ch:int):...
```

Set the channel.


``` python
def getChannel(self)->int:...
```

Get the channel.


``` python
def setPin(self,pin:str):...
```

Use the name of the pin to select the PWM pin.

example: `"PA0"`, `"PA1"` ...


``` python
def setFrequency(self,freq:int):...
```

Set the frequency.


``` python
def setFreq(self,freq:int):...
```

Set the frequency.


``` python
def setDuty(self,duty:float):...
```

Set the duty.


``` python
def enable(self):...
```

Enable the PWM.


``` python
def disable(self):...
```

Disable the PWM.


``` python
def getFrequency(self)->int:...
```

Get the frequency.


``` python
def getDuty(self)->float:...
```

Get the duty.


``` python
def close(self):...
```

``` python
def platformEnable(self):...
```

``` python
def platformSetFrequency(self):...
```

``` python
def platformSetDuty(self):...
```

``` python
def platformDisable(self):...
```

### class SPI(BaseDev):
``` python
def __init__(self):...
```

``` python
def setPinSCK(self,pin:str):...
```

Set the SCK pin.


``` python
def setPinMOSI(self,pin:str):...
```

Set the MOSI pin.


``` python
def setPinMISO(self,pin:str):...
```

Set the MISO pin.


``` python
def setName(self,name:str):...
```

Use the device name to select the SPI pin.

exmpale: `"SPI0"`, `"SPI1"` ...


``` python
def setId(self,id:int):...
```

Set the id of the SPI.

example: `0`, `1` ...


``` python
def setPolarity(self,polarity:int):...
```

Set the polarity.


``` python
def setPhase(self,phase:int):...
```

Set the phase.


``` python
def setBaudRate(self,baudRate:int):...
```

Set the baud rate.


``` python
def enable(self):...
```

Enable the SPI.


``` python
def disable(self):...
```

Disable the SPI.


``` python
def write(self,data:str):...
```

Write string to the SPI.


``` python
def writeBytes(self,data:bytes,length:int):...
```

Write bytes to the SPI.


``` python
def read(self,length:int)->str:...
```

Read string from the SPI.


``` python
def readBytes(self,length:int)->bytes:...
```

Read bytes from the SPI.


``` python
def platformEnable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformWriteBytes(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformReadBytes(self):...
```

``` python
def platformDisable(self):...
```

### class CAN(BaseDev):
``` python
def __init__(self):...
```

``` python
def setName(self,name:str):...
```

Use the device name to select the CAN pin.

exmpale: `"CAN0"`, `"CAN1"` ...


``` python
def setId(self,id:int):...
```

Use the id to select the CAN pin.

example: `0`, `1` ...


``` python
def setBaudRate(self,baudRate:int):...
```

Set the baud rate.


``` python
def setMode(self,mode:str):...
```

Set the mode.

example: `"normal"`, `"loopback"`, `"silent"`, `"silent_loopback"`


``` python
def enable(self):...
```

Enable the CAN.


``` python
def disable(self):...
```

Disable the CAN.


``` python
def write(self,data:str):...
```

Write string to the CAN.


``` python
def writeBytes(self,data:bytes,length:int):...
```

Write bytes to the CAN.


``` python
def read(self,length:int)->str:...
```

Read string from the CAN.


``` python
def readBytes(self,length:int)->bytes:...
```

Read bytes from the CAN.


``` python
def addFilter(self,id:int,ide:int,rtr:int,mode:int,mask:int,hdr:int):...
```

Add a filter.


``` python
def platformEnable(self):...
```

``` python
def platformWrite(self):...
```

``` python
def platformWriteBytes(self):...
```

``` python
def platformRead(self):...
```

``` python
def platformReadBytes(self):...
```

``` python
def platformDisable(self):...
```

### class BaseDev:
``` python
def addEventCallBack(self,eventCallback:any):...
```

Add an event callback. 


``` python
def platformGetEventId(self):...
```



## Examples

### GPIO.py

```python
import PikaStdLib
import machine

mem = PikaStdLib.MemChecker()
io1 = machine.GPIO()
time = machine.Time()

io1.setPin('PA8')
io1.setMode('out')
io1.enable()
io1.low()

print('hello pikascript')
print('mem.max :')
mem.max()
print('mem.now :')
mem.now()

while True:
    mem.now()
    io1.low()
    time.sleep_ms(500)
    io1.high()
    time.sleep_ms(500)
    

```
### LCD.py

```python
import PikaStdLib

import machine

lcd = machine.LCD()
lcd.init()
lcd.clear('white')
mem = PikaStdLib.MemChecker()
key = machine.KEY()
key.init()
time = machine.Time()
h = 10
w = 10
x = 10
y = 10
x_last = x
y_last = y
is_update = 0
print('mem used max:')
mem.max()
lcd.fill(x, y, w, h, 'blue')
while True:
    key_val = key.get()
    if key_val != -1:
        x_last = x
        y_last = y
        is_update = 1
    if key_val == 0:
        x = x + 5
    if key_val == 1:
        y = y - 5
    if key_val == 2:
        y = y + 5
    if key_val == 3:
        x = x - 5
    if is_update:
        is_update = 0
        lcd.fill(x_last, y_last, w, h, 'white')
        lcd.fill(x, y, w, h, 'blue')

```
### PWM.py

```python
import PikaStdLib
import machine

time = machine.Time()
pwm = machine.PWM()
pwm.setPin('PA8')
pwm.setFrequency(2000)
pwm.setDuty(0.5)
pwm.enable()
mem = PikaStdLib.MemChecker()

while True:
    mem.now()
    time.sleep_ms(500)
    pwm.setDuty(0.5)
    time.sleep_ms(500)
    pwm.setDuty(0.001)
    

```
### Time.py

```python
import PikaStdLib
import machine

time = machine.Time()

while True:
    time.sleep_ms(500)
    print('0.5s')
    time.sleep_s(1)
    print('1s')
    

```
### UART_CALLBACK.py

```python
import PikaStdDevice as std
print('hello pikascript')

uart = std.UART()
uart.setId(0)
uart.setBaudRate(115200)
uart.enable()

def cb1(signal):
    print('recv:', uart.read(32))

uart.setCallBack(cb1, uart.SIGNAL_RX)

while True:
    pass

```
### GPIO_CALLBCK.py

```python
import PikaStdDevice as std
print('hello pikascript')

io = std.GPIO()
io.setPin('P4')
io.setMode('in')
io.enable()

def cb1(signal):
    print('cb1', signal)

io.setCallBack(cb1, io.SIGNAL_FALLING)

while True:
    pass

```
### UART.py

```python
import PikaStdLib
import machine

time = machine.Time()
uart = machine.UART()
uart.setId(1)
uart.setBaudRate(115200)
uart.enable()

while True:
    time.sleep_ms(500)
    readBuff = uart.read(2)
    print('read 2 char:')
    print(readBuff)
    

```
### RGB.py

```python
import machine

import PikaStdLib

time = machine.Time()
adc = machine.ADC()
pin = machine.GPIO()
pwm = machine.PWM()
uart = machine.UART()
rgb = machine.RGB()
mem = PikaStdLib.MemChecker()

rgb.init()
rgb.enable()

print('hello 2')
print('mem used max:')
mem.max()

while True:
    print('flowing')
    rgb.flow()
    time.sleep_ms(100)


```
### ADC.py

```python
import PikaStdLib
import machine

time = machine.Time()
adc1 = machine.ADC()

adc1.setPin('PA1')
adc1.enable()

while True:
    val = adc1.read()
    print('adc1 value:')
    print(val)
    time.sleep_ms(500)
    

```
