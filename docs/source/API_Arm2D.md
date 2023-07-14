# Arm2D 模块 API 文档

## API

### class Window:
``` python
def __init__(self):...
```

``` python
def addCallBack(callback:any):...
```

Interface of callback:

``` callback(frameBuff: Tile, isNewFrame:int) ```


``` python
def __init__():...
```

``` python
def create_region(x:int,y:int,w:int,h:int)->Region:...
```

``` python
def create_location(x:int,y:int)->Location:...
```

``` python
def update():...
```

### class Tile:
``` python
def __init__(self):...
```

``` python
def get_root(self,validRegion:Region,offset:Location)->Tile:...
```

``` python
def generate_child(self,reg:Region,clipRegion:int)->Tile:...
```

``` python
def width_compare(self,reference:Region)->int:...
```

``` python
def height_compare(self,reference:Region)->int:...
```

``` python
def shape_compare(self,reference:Region)->int:...
```

``` python
def region_diff(self,tile:Tile)->Region:...
```

``` python
def transform(self,reg:Region,centre:Location)->int:...
```

``` python
def is_root_tile(self)->int:...
```

``` python
def get_absolute_location(self)->Location:...
```

``` python
def is_point_inside_region(region:Region,location:Location)->int:...
```

``` python
def tile_copy(src:Tile,des:Tile,des_reg:Region,mode:int)->int:...
```

``` python
def tile_rotation(src:Tile,des:Tile,des_reg:Region,centre:Location,angle:float,mask_color:int)->int:...
```

``` python
def alpha_blending(src:Tile,des:Tile,reg:Region,alp:int)->int:...
```

``` python
def fill_colour(tile:Tile,reg:Region,colour:int)->int:...
```

### class Region:
``` python
def __init__(self):...
```

``` python
def intersect(self,in2:Region)->Region:...
```

### class Location:
``` python
def __init__(self):...
```

### class Star(Tile):
``` python
def __init__(self):...
```

### class BackGround:
``` python
def __init__(self):...
```

``` python
def setColor(self,color:int):...
```

``` python
def getColor(self)->int:...
```

``` python
def update(self):...
```

### class ElementList:
``` python
def update(self):...
```

### class Element:
``` python
def __init__(self):...
```

``` python
def move(self,x:int,y:int):...
```

``` python
def right(self,x:int):...
```

``` python
def lift(self,x:int):...
```

``` python
def up(self,y:int):...
```

``` python
def down(self,y:int):...
```

``` python
def update(self):...
```

``` python
def setAlpha(self,alpha:int):...
```

### class Box(Element):
``` python
def update(self):...
```

``` python
def __init__(self):...
```

``` python
def setColor(self,color:int):...
```

``` python
def setSize(self,x:int,y:int):...
```



## Examples

### main.py

```python
import PikaStdLib
import Arm2D

mem = PikaStdLib.MemChecker()
mem.max()
win = Arm2D.Window()
win.init()
win.background.setColor('white')
win.elems.box = Arm2D.Box()
win.elems.box.init()
while True:
    win.elems.box.move(20, 20)
    win.elems.box.setColor('green')
    win.update()
    win.elems.box.move(30, 50)
    win.elems.box.setColor('blue')
    win.update()
    win.elems.box.move(50,30)
    win.elems.box.setColor('red')
    win.update()
    mem.max()
    
```
