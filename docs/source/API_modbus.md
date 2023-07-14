# modbus 模块 API 文档

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

### class ModBus(_modbus._ModBus):
A subclass of _modbus._ModBus that provides methods for serializing and sending modbus messages.


``` python
def serializeWriteBits(self,addr:int,src:list)->bytes:...
```

Serialize a write multiple coils request.

Args:

addr (int): The starting address of the coils to be written.

src (list): A list of boolean values (0 or 1) to be written to the coils.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeWriteRegisters(self,addr:int,src:list)->bytes:...
```

Serialize a write multiple registers request.

Args:

addr (int): The starting address of the registers to be written.

src (list): A list of integer values (0-65535) to be written to the registers.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeReadBits(self,addr:int,nb:int)->bytes:...
```

Serialize a read coils request.

Args:

addr (int): The starting address of the coils to be read.

nb (int): The number of coils to be read.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeReadInputBits(self,addr:int,nb:int)->bytes:...
```

Serialize a read discrete inputs request.

Args:

addr (int): The starting address of the discrete inputs to be read.

nb (int): The number of discrete inputs to be read.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeReadRegisters(self,addr:int,nb:int)->bytes:...
```

Serialize a read holding registers request.

Args:

addr (int): The starting address of the holding registers to be read.

nb (int): The number of holding registers to be read.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeReadInputRegisters(self,addr:int,nb:int)->bytes:...
```

Serialize a read input registers request.

Args:

addr (int): The starting address of the input registers to be read.

nb (int): The number of input registers to be read.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeWriteBit(self,addr:int,status:int)->bytes:...
```

Serialize a write single coil request.

Args:

addr (int): The address of the coil to be written.

status (int): The value (0 or 1) to be written to the coil.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeWriteRegister(self,addr:int,value:int)->bytes:...
```

Serialize a write single register request.

Args:

addr (int): The address of the register to be written.

value (int): The value (0-65535) to be written to the register.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeMaskWriteRegister(self,addr:int,andMask:int,orMask:int)->bytes:...
```

Serialize a mask write register request.

Args:

addr (int): The address of the register to be modified.

andMask (int): The AND mask to be applied to the current value of the register.

orMask (int): The OR mask to be applied to the result of the AND operation.

Returns:

bytes: The serialized message as a bytes object.


``` python
def serializeReportSlaveId(self)->int:...
```

Serialize a report slave ID request.

Returns:

int: The length of the serialized message in bytes.


``` python
def deserializeReadRegisters(self,msg:bytes)->list:...
```

Deserialize a read holding registers response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

list: A list of integer values (0-65535) read from the registers.


``` python
def deserializeReadBits(self,msg:bytes)->list:...
```

Deserialize a read coils response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

list: A list of boolean values (True or False) read from the coils.


``` python
def deserializeReadInputBits(self,msg:bytes)->list:...
```

Deserialize a read discrete inputs response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

list: A list of boolean values (True or False) read from the discrete inputs.


``` python
def deserializeReadInputRegisters(self,msg:bytes)->list:...
```

Deserialize a read input registers response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

list: A list of integer values (0-65535) read from the input registers.


``` python
def deserializeWriteAndReadRegisters(self,msg:bytes)->list:...
```

Deserialize a write and read registers response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

list: A list of integer values (0-65535) written to and read from the registers.


``` python
def deserializeWriteBit(self,msg:bytes)->int:...
```

Deserialize a write single coil response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

int: The address of the coil written to.


``` python
def deserializeWriteRegister(self,msg:bytes)->int:...
```

Deserialize a write single register response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

int: The address of the register written to.


``` python
def deserializeWriteBits(self,msg:bytes)->int:...
```

Deserialize a write multiple coils response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

int: The number of coils written to.


``` python
def deserializeWriteRegisters(self,msg:bytes)->int:...
```

Deserialize a write multiple registers response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

int: The number of registers written to.


``` python
def deserializeMaskWriteRegister(self,msg:bytes)->int:...
```

Deserialize a mask write register response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

int: The address of the register modified.


``` python
def deserializeReportSlaveId(self,msg:bytes)->bytes:...
```

Deserialize a report slave ID response.

Args:

msg (bytes): The received message as a bytes object.

Returns:

bytes: The slave ID.


### class ModBusRTU(ModBus):
``` python
def __init__(self,sendBuffSize=128,readBuffSize=128,uart:PikaStdDevice.UART=None):...
```

Initialize a Modbus RTU protocol instance.

Args:

sendBuffSize (int): The size of the send buffer in bytes.

readBuffSize (int): The size of the read buffer in bytes.


``` python
def recvCallback(self,signal):...
```

``` python
def setUart(self,uart:PikaStdDevice.UART):...
```

``` python
def recv(self,count:int=10):...
```

获取uart返回的数据

:param count:

:return:


``` python
def setBaudRate(self,baud:int):...
```

``` python
def send(self,msg:bytes):...
```

发送485十六进制消息

:param msg: modbus rtu 消息

:param band: 波特率

:return:


``` python
def setOption(self,op_code:str):...
```

``` python
def _getOperation(self,prefix:str,op_code:str):...
```

``` python
def getSerializer(self,op_code:str):...
```

``` python
def getDeserializer(self,op_code:str):...
```

``` python
def serializeRequest(self,op_code:str,addr:int,arg,slave:int=None)->bytes:...
```

序列化modbus rtu请求

:param op_code: 操作码

:param addr: 寄存器地址

:param arg: 参数 读取时为数量 写入时为值

:param slave: 从机地址

:return: 序列化后的数据


``` python
def deserializeResponse(self,op_code:str,msg:bytes):...
```

反序列化modbus rtu响应

:param op_code: 操作码

:param msg: 响应消息

:return: 解码后的数据


``` python
def _do_request(self,op_code:str,addr:int,arg,slave:int=None):...
```

发送modbus rtu请求

:param op_code: 操作码

:param addr: 寄存器地址

:param arg: 参数 读取时为数量 写入时为值

:param slave: 从机地址

:return: 解码后的数据


``` python
def request(self,op_code:str,addr:int,arg,slave:int=None):...
```

发送modbus rtu请求

:param op_code: 操作码

:param addr: 寄存器地址

:param arg: 参数 读取时为数量 写入时为值

:param slave: 从机地址

:return: 解码后的数据


``` python
def set_request_callback(self,cb_before,cb_after):...
```

``` python
def set_send_callback(self,cb_before,cb_after):...
```

### class ModBusTCP(ModBus):
``` python
def __init__(self,sendBuffSize:int,readBuffSize:int):...
```

Initialize a Modbus TCP protocol instance.

Args:

sendBuffSize (int): The size of the send buffer in bytes.

readBuffSize (int): The size of the read buffer in bytes.




## Examples

### rtu_request.py

```python
import modbus

# Create a ModBusRTU object, specify the send buffer and receive buffer size as 128 bytes
mb = modbus.ModBusRTU(128, 128)

# Set slave address to 1
op_code = 'x06'
slave_addr = 0x13
reg_addr = 0x00
reg_value = 0x01
mb.serializeRequest(op_code, reg_addr, reg_value, slave_addr)
res = b'\x13\x06\x00\x00\x00\x01\x4b\x78'
ret = mb.deserializeResponse('x06', res)
assert ret == 1

```
### rtu_master_err.py

```python
# Import modbus module
import modbus

# Create a ModBusRTU object, specify the send buffer and receive buffer size as 128 bytes
mb = modbus.ModBusRTU(128, 128)

# Set slave address to 1
mb.setSlave(1)

# Generate a request frame for reading registers, specify the start address as 0 and the quantity as 10
send_buff = mb.serializeReadRegisters(0, 10)

# Print the byte string of the request frame
print(send_buff)

# Parse a response frame for reading registers, return a list containing the values of the registers
host_regists = mb.deserializeReadRegisters(
    b'\x01\x03\x14\x00\x00\x04\xD2\x00\x00\x00\x00\x00\x7B\x00\x00\x00\x00\x00\x00\x00\x00\xE5\x0B'
)
print(host_regists)

```
### rtu_master.py

```python
# Import modbus module
import modbus

# Create a ModBusRTU object, specify the send buffer and receive buffer size as 128 bytes
mb = modbus.ModBusRTU(128, 128)

# Set slave address to 1
mb.setSlave(1)

# Generate a request frame for reading registers, specify the start address as 0 and the quantity as 10
send_buff = mb.serializeReadRegisters(0, 10)

# Print the byte string of the request frame
print(send_buff)

# Parse a response frame for reading registers, return a list containing the values of the registers
host_regists = mb.deserializeReadRegisters(
    b'\x01\x03\x14\x00\x00\x00\x00\x04\xD2\x00\x00\x00\x00\x00\x7B\x00\x00\x00\x00\x00\x00\x00\x00\xE5\x0B'
)
print(host_regists)


# Generate a request frame for reading input registers, specify the start address as 0 and the quantity as 2
mb.serializeReadInputRegisters(0, 2)

# Parse a response frame for reading input registers, return a list containing the values of the input registers

mb.deserializeReadInputRegisters(b'\x01\x04\x04\x00\x00\x08\xE6\x7D\xCE')


# Generate a request frame for writing a single register, specify the register address as 0 and the value as 0x1234
send_buff = mb.serializeWriteRegister(0, 0x1234)
print(send_buff)

send_buff = mb.serializeWriteBits(0, [1, 1, 1, 0, 1, 0, 1, 0])
print(send_buff)

```
