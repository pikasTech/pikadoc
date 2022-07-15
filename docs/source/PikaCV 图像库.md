# 5.6 PikaCV 图像库

PikaCV图像库实现了部分常用的图像处理算法。

## 5.6.1 安装

1. 在 requestment.txt 中加入 PikaCV的依赖，PikaCV的版本号应当与内核的版本号相同。

   ```
   PikaCV==latest
   ```

2. 运行 pikaPackage.exe

## 5.6.2 导入

在 main.py 中加入：

```python
#main.py
import PikaCV as cv
```

## 5.6.3 class Image():

Image类是PikaCV库的基础，后续的图像处理算法都基于Image类。使用Image类可以创建一个空图像，如：

```python
import PikaCV
img = cv.Image()
```

### 5.6.3.1 图像读写

目前，PikaCV可以读取Jpeg格式文件与写入bmp格式文件。

```python
    def read(self, path: str):
        """Read the image from the specified path, 
        Need implement the   `__platform_fopen()`, `__platform_fread()`
          and `__platform_fclose()`"""
        ...

    def write(self, path: str):
        """Write the image to the specified path, 
        Need implement the   `__platform_fopen()`, `__platform_fwrite()` 
        and `__platform_fclose()`"""
        ...

    def loadJpeg(self, bytes: any):
        """Load the image from bytes"""

    def loadRGB888(self, width: int, height: int, bytes: bytes):
        """Load the image from bytes"""

    def loadRGB565(self, width: int, hight: int, bytes: bytes):
        """Load the image from bytes"""

    def loadGray(self, width: int, hight: int, bytes: bytes):
        """Load the image from bytes"""
```

### 5.6.3.2 图像属性

图像的``size``为``width * hight * channel``。

```python
    def width(self) -> int:
        """Get the width of the image"""

    def hight(self) -> int:
        """Get the hight of the image"""

    def format(self) -> int:
        """Get the format of the image. 
        The format is one of the `ImageFormat` enum, 
        like `ImageFormat.RGB888`"""
            def data(self) -> bytes:
        """Get the data of the image"""

    def getPixel(self, x: int, y: int, channel: int) -> int:
        """Get the pixel value of the specified channel.
        For example, if the format of image is `RGB888`, 
        the channel `0`, `1`, `2`, means `R`, `G`, `B`, 
        and for the format of `GRAY8`, the channel is `0`
        """

    def setPixel(self, x: int, y: int, channel: int, value: int):
        """Set the pixel value of the specified channel.
        For example, if the format of image is `RGB888`, 
        the channel `0`, `1`, `2`, means `R`, `G`, `B`, 
        and for the format of `GRAY8`, the channel is `0`
        """

    def size(self) -> int:
        """Get the size of the image by bytes"""
```

### 5.6.3.3 图像运算

```python
    def add(self,image:Imgae):
        """Add two images"""

    def minus(self,image:Imgae):
        """Minus two images"""

    def split(self) -> List:
        """Split one 3-channels image to three 1-channel"""

    def merge(self,R:Image,G:Image,B:Image):
        """Merge three 1-channel image to 3-channels"""
```

``add()`` 与``minus()``逐像素操作，当像素值超过255时归为255，低于0时归为0。

``merge()``与``split()``的通道顺序均为RGB。

## 5.6.4 class Converter():

Converter类主要实现了图像格式之间的转换，目前Converter支持以下图像存储格式及转换：

| From\To | RGB888 | RGB565 | Gray | BMP  | BGR888 |
| ------- | ------ | ------ | ---- | ---- | ------ |
| RGB888  | -      | √      | √    | *    | √      |
| RGB565  | √      | -      | √    | *    | √      |
| Gray    | √      | √      | -    | *    | √      |
| BMP     | √      | √      | √    | -    | √      |
| BGR888  | √      | √      | √    | √    | -      |

其中，``-``代表不执行任何操作，``*``代表需要经一次中间转换，`` √``代表可以直接转换。

图像格式转换操作示例如下：

```python
cv.Converter.toBMP(img)
```

## 5.6.5 class Transforms():

Transforms类主要实现了图像变换算法,目前已经实现的变换算法有：

1. ``rotateDown``

   可将图像旋转180度。