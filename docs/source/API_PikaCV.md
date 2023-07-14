# PikaCV 模块 API 文档

## API

### class ImageFormat:
The ImageFormat class is used to 

store the image format enum of an image.


``` python
def __init__(self):...
```

### class Image:
Create a empty image. The image can be 

filled with data by read a file e.g.: `read()` 

or load bytes e.g:. `loadRGB888`, `loadRGB565`, `loadGray` or `loadJpeg`


``` python
def __init__(self):...
```

``` python
def read(self,path:str):...
```

Read the image from the specified path, 

Need implement the   `__platform_fopen()`, `__platform_fread()`

and `__platform_fclose()`


``` python
def write(self,path:str):...
```

Write the image to the specified path, 

Need implement the   `__platform_fopen()`, `__platform_fwrite()` 

and `__platform_fclose()`


``` python
def loadJpeg(self,bytes:any):...
```

Load the image from bytes


``` python
def loadRGB888(self,width:int,height:int,bytes:bytes):...
```

Load the image from bytes


``` python
def loadRGB565(self,width:int,hight:int,bytes:bytes):...
```

Load the image from bytes


``` python
def loadGray(self,width:int,hight:int,bytes:bytes):...
```

Load the image from bytes


``` python
def width(self)->int:...
```

Get the width of the image


``` python
def hight(self)->int:...
```

Get the hight of the image


``` python
def format(self)->int:...
```

Get the format of the image. 

The format is one of the `ImageFormat` enum, 

like `ImageFormat.RGB888`


``` python
def data(self)->bytes:...
```

Get the data of the image


``` python
def getPixel(self,x:int,y:int,channel:int)->int:...
```

Get the pixel value of the specified channel.

For example, if the format of image is `RGB888`, 

the channel `0`, `1`, `2`, means `R`, `G`, `B`, 

and for the format of `GRAY8`, the channel is `0`


``` python
def setPixel(self,x:int,y:int,channel:int,value:int):...
```

Set the pixel value of the specified channel.

For example, if the format of image is `RGB888`, 

the channel `0`, `1`, `2`, means `R`, `G`, `B`, 

and for the format of `GRAY8`, the channel is `0`


``` python
def size(self)->int:...
```

Get the size of the image by bytes


``` python
def add(self,image:Image):...
```

Add two images


``` python
def minus(self,image:Image):...
```

Minus two images


``` python
def split(self)->list:...
```

Split one 3-channels image to three 1-channel


``` python
def merge(self,R:Image,G:Image,B:Image):...
```

Merge three 1-channel image to 3-channels


### class Converter:
The Converter class is used to 

convert an image from one format to another.


``` python
def toRGB888(image:Image):...
```

Convert the image to RGB888


``` python
def toRGB565(image:Image):...
```

Convert the image to RGB565


``` python
def toGray(image:Image):...
```

Convert the image to Gray


``` python
def toBMP(image:Image):...
```

Convert the image to BMP


``` python
def toBGR888(image:Image):...
```

Convert the image to BGR888


``` python
def converter(image:Image,format:int):...
```

2:RGB888

3:BGR888

4:RGB565

5:GRAY

6:BMP


### class Transforms:
The transforms class is used to 

supply the rotate, flip, and crop operation for an image.


``` python
def rotateDown(image:Image):...
```

Rotate the image 


``` python
def threshold(image:Image,thre:int,maxval:int,thresholdType:int):...
```

0:THRESH_BINARY 

1:THRESH_BINARY_INV

2:THRESH_TRUNC

3:THRESH_TOZERO

4:THRESH_TOZERO_INV

5:OTSU


``` python
def setROI(image:Image,x:int,y:int,w:int,h:int):...
```

xywh


``` python
def getOTSUthre(image:Image)->int:...
```

return otsu threshold


``` python
def setOTSU(image:Image):...
```

otsu


``` python
def resize(image:Image,x:int,y:int,resizeType:int):...
```

resize image

0:NEAREST

TODO:

1:BILINEAR


``` python
def adaptiveThreshold(image:Image,maxval:int,subsize:int,c:int,method:int):...
```

AdaptiveThreshold

method

0:meanFilter

1:medianFilter

#TODO 2:gaussianFilter


### class Filter:
The Filter class is used to 

supply some Image Filtering Algorithms .


``` python
def meanFilter(image:Image,ksizex:int,ksizey:int):...
```

mean filter,ksize is odd


``` python
def medianFilter(image:Image):...
```

median filter,kernel size is 3*3




## Examples

### PikaCV_test11.py

```python
import PikaCV as cv
import binascii
img = cv.Image()
img.read("test/assets/test2.jpg")

cv.Converter.toGray(img)
data = img.data()
print(binascii.b2a_hex(img.data()).decode())
cv.Converter.toBMP(img)
img.write("test/out/test.bmp")


```
### PikaCV_test10.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toGray(img)
cv.Transforms.adaptiveThreshold(img,255,3,0,0)
cv.Converter.toBMP(img)
img.write("test/out/test10.bmp")

```
### PikaCV_test1.py

```python
import PikaCV as cv
import binascii
img = cv.Image()
img.read("test/assets/test.jpg")

cv.Converter.toRGB565(img)
print(str(binascii.b2a_hex(img.data())))
cv.Converter.toBMP(img)
img.write("test/out/test.bmp")


```
### PikaCV_test2.py

```python
import PikaCV as cv
import binascii
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)

Channel = img.split()
R = Channel[0]
G = Channel[1]
B = Channel[2]

cv.Converter.toBMP(R)
cv.Converter.toBMP(G)
cv.Converter.toBMP(B)
R.write("test/out/R.bmp")
G.write("test/out/G.bmp")
B.write("test/out/B.bmp")
```
### PikaCV_test4.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")

cv.Converter.toGray(img)
cv.Transforms.threshold(img,120,255,0)
cv.Converter.toBMP(img)
img.write("test/out/test.bmp")


```
### PikaCV_test3.py

```python
import PikaCV as cv
import binascii
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)

Channel = img.split()
R = Channel[0]
G = Channel[1]
B = Channel[2]

img1 = cv.Image()
cv.Converter.toRGB888(img1)
img1.merge(R,G,B)
cv.Converter.toBMP(img1)
img1.write("test/out/merge.bmp")

print("Merge done")
```
### PikaCV_test5.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)
cv.Transforms.setROI(img,5,5,5,5)
cv.Converter.toBMP(img)
img.write("test/out/test1.bmp")

```
### PikaCV_test8.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)
cv.Filter.meanFilter(img,3,3)
cv.Converter.toBMP(img)
img.write("test/out/test8.bmp")
```
### PikaCV_test6.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)
thre = cv.Transforms.getOTSUthre(img)
print(thre)
cv.Transforms.setOTSU(img)
cv.Converter.toBMP(img)
img.write("test/out/test2.bmp")

```
### PikaCV_test9.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)
cv.Filter.medianFilter(img)
cv.Converter.toBMP(img)
img.write("test/out/test9.bmp")
```
### PikaCV_test7.py

```python
import PikaCV as cv
img = cv.Image()
img.read("test/assets/test.jpg")
cv.Converter.toRGB888(img)
thre = cv.Transforms.resize(img,25,25,0)
cv.Converter.toBMP(img)
img.write("test/out/test3.bmp")
```
