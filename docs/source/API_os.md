# os 模块 API 文档

## API

``` python
def __init__(self):...
```

``` python
def mkdir(self,path:str,*mode):...
```

``` python
def rmdir(self,path:str):...
```

``` python
def chdir(self,path:str):...
```

``` python
def listdir(self,path:str)->list:...
```

``` python
def getcwd(self)->str:...
```

``` python
def open(self,filename:str,flags:int)->FILE:...
```

``` python
def read(self,fd:FILE,len:int)->str:...
```

``` python
def write(self,fd:FILE,buf:any)->int:...
```

``` python
def lseek(self,fd:FILE,pos:int,how:int)->int:...
```

``` python
def close(self,fd:FILE):...
```

``` python
def fstat(self,fd:FILE)->fileStat:...
```

``` python
def remove(self,filename:str):...
```

``` python
def rename(self,old:str,new:str):...
```

### class fileStat:
``` python
def st_size(self)->int:...
```

### class path:
``` python
def join(self,*paths)->str:...
```

``` python
def split(self,path:str)->tuple:...
```

``` python
def splitext(self,path:str)->tuple:...
```

``` python
def basename(self,path:str)->str:...
```

``` python
def dirname(self,path:str)->str:...
```

``` python
def exists(self,path:str)->bool:...
```

``` python
def isdir(self,path:str)->bool:...
```

``` python
def isfile(self,path:str)->bool:...
```

``` python
def isabs(self,path:str)->bool:...
```

``` python
def abspath(self,path:str)->str:...
```



## Examples

### os_path.py

```python
import os
p = os.path
assert p.join('dir', 'file.txt') == 'dir/file.txt'
assert p.join('/home/user', 'dir', 'file.txt') == '/home/user/dir/file.txt'

# Test split method
assert p.split('dir/file.txt')[0] == 'dir'
assert p.split('dir/file.txt')[1] == 'file.txt'
assert p.split('/home/user/dir/file.txt')[0] == '/home/user/dir'
assert p.split('/home/user/dir/file.txt')[1] == 'file.txt'
    
# Test splitext method
assert p.splitext('file.txt')[0] == 'file'
assert p.splitext('file.txt')[1] == '.txt'
assert p.splitext('/home/user/file.tar.gz')[0] == '/home/user/file.tar'
assert p.splitext('/home/user/file.tar.gz')[1] == '.gz'

# Test basename method
assert p.basename('dir/file.txt') == 'file.txt'
assert p.basename('/home/user/dir/file.txt') == 'file.txt'

# Test dirname method
assert p.dirname('dir/file.txt') == 'dir'
assert p.dirname('/home/user/dir/file.txt') == '/home/user/dir'

# Test exists method
assert p.exists('config/pika_config_void') == False
assert p.exists('/usr/bin') == True

# Test isdir method
assert p.isdir('config/pika_config_void.h') == False
assert p.isdir('config') == True

# Test isfile method
assert p.isfile('config') == False
assert p.isfile('config/pika_config_void.h') == True

# Test isabs method
assert p.isabs('dir/file.txt') == False
assert p.isabs('/home/user/file.txt') == True

# Test abspath method
# assert p.abspath('config/pika_config_void.h') == "/root/pikascript/port/linux/config/pika_config_void.h"
assert p.abspath('/usr/bin') == "/usr/bin"

print("PASS")

```
### os_test1.py

```python
import os
origin = os.getcwd()
os.chdir("test/out")
os.getcwd()

try:
    # cleanup
    os.remove("_testdir/testfile")
    os.rmdir("_testdir")
except:
    pass

os.mkdir("_testdir")
os.chdir("_testdir")


f = os.open("testfile", os.O_CREAT | os.O_RDWR)
assert os.write(f, b"Hello World!") == 12
assert os.lseek(f, 0, 0) == 0
print(os.read(f, 100))
os.close(f)
os.chdir("..")
os.chdir(origin)
print("PASS")

```
