# ctypes 模块 API 文档

### class c_uint(TinyObj):
``` python
def __init__(self,value:int):...
```

### class c_float(TinyObj):
``` python
def __init__(self,value:float):...
```

### class c_wchar_p(TinyObj):
``` python
def __init__(self,value:str):...
```

### class c_bool(c_uint):
### class c_byte(c_uint):
### class c_ubyte(c_uint):
### class c_short(c_uint):
### class c_int(c_uint):
### class c_long(c_uint):
### class c_ulong(c_uint):
### class c_longlong(c_uint):
### class c_ulonglong(c_uint):
### class c_size_t(c_uint):
### class c_ssize_t(c_uint):
### class c_void_p(c_uint):
### class c_char(c_wchar_p):
### class c_wchar(c_wchar_p):
### class c_char_p(c_wchar_p):
### class c_double(c_float):
### class c_longdouble(c_float):
### class Test(TinyObj):
``` python
def add(self,c_uint1:c_uint,c_uint2:c_uint)->int:...
```

``` python
def dc_cpuapdu_hex(self,slen:int,sendbuf:bytes,rlen:c_uint,rcvbuf:c_char_p)->int:...
```

``` python
def print_rcv(self,rcvbuf:c_char_p):...
```

### class create_string_buffer(TinyObj):
``` python
def __init__(self,size:int):...
```

``` python
def __getitem__(self,__key:int)->int:...
```

### class c_buffer(TinyObj):
``` python
def __init__(self,value:any,size:int):...
```

``` python
def __getitem__(self,__key:int)->int:...
```

