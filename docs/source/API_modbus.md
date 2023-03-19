# modbus 模块 API 文档

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
           

### class ModBusRTU(ModBus):
``` python
def __init__(self,sendBuffSize:int,readBuffSize:int):...
```

   Initialize a Modbus RTU protocol instance.
           Args:
               sendBuffSize (int): The size of the send buffer in bytes.
               readBuffSize (int): The size of the read buffer in bytes.
           

### class ModBusTCP(ModBus):
``` python
def __init__(self,sendBuffSize:int,readBuffSize:int):...
```

   Initialize a Modbus TCP protocol instance.
           Args:
               sendBuffSize (int): The size of the send buffer in bytes.
               readBuffSize (int): The size of the read buffer in bytes.
           

