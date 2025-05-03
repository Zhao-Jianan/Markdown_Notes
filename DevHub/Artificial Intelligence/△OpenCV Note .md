# OpenCV简介
## 图像处理简介
### 图像的起源
#### 图像的定义
图像是人类视觉的基础，是自然景物的客观反映，是人类认识世界和人类本身的重要源泉。“图”是物体反射或透射光的分布，“像“是人的视觉系统所接受的图在人脑中所形版的印象或认识，照片、绘画、剪贴画、地图、书法作品、手写汉学、传真、卫星云图、影视画面、X光片、脑电图、心电图等都是图像。一姚敏. 数字图像处理：机械工业出版社，2014年

#### 模拟图像和数字图像
- 图像起源于1826年前后法国科学家Joseph Nicéphore Niépce发明的第一张可永久保存的照片，属于模拟图像。模拟图像又称连续图像，它通过某种物理量（如光、电等）的强弱变化来记录图像亮度信息，所以是连续变换的。模拟信号的特点是容易受干扰，如今已经基本全面被数字图像替代
- 在第一次世界大战后，1921年美国科学家发明了Bartlane System，并从伦敦传到纽约传输了第一幅数字图像，其亮度用离散数值表示，将图片编码成5个灰度级，如下图所示，通过海底电缆进行传输。在发送端图片被编码并使用打孔带记录，通过系统传输后在接收方使用特殊的打印机恢复成图像
- 1950年左右，计算机被发明，数字图像处理学科正式诞生

### 数字图像的表示
- 位数
  - 计算机采用0/1编码的系统，数字图像也是利用0/1来记录信息，我们平常接触的图像都是8位数图像，包含0～255灰度，其中0，代表最黑，1，表示最白
- 人眼对灰度更敏感一些，在16位到32位之间

### 图像的分类
#### 二值图像
一幅二值图像的二维矩阵仅由0、1两个值构成，“0”代表黑色，“1”代白色。由于每一像素（矩阵中每一元素）取值仅有0、1两种可能，所以计算机中二值图像的数据类型通常为1个二进制位。二值图像通常用于文字、线条图的扫描识别（OCR）和掩膜图像的存储

#### 灰度图
- 每个像素只有一个采样颜色的图像，这类图像通常显示为从最暗黑色到最亮的白色的灰度，尽管理论上这个采样可以任何颜色的不同深浅，甚至可以是不同亮度上的不同颜色
- 灰度图像与黑白图像不同，在计算机图像领域中黑白图像只有黑色与白色两种颜色；但是，灰度图像在黑色与白色之间还有许多级的颜色深度
- 灰度图像经常是在单个电磁波频谱如可见光内测量每个像素的亮度得到的，用于显示的灰度图像通常用每个采样像素8位的非线性尺度来保存，这样可以有256级灰度（如果用16位，则有65536级）

#### 彩色图
- 每个像素通常是由红（R）、绿（G）、蓝（B）三个分量来表示的，分量介于（0，255）。RGB图像与索引图像一样都可以用来表示彩色图像
- 与索引图像一样，它分别用红（R）、绿（G）、蓝（B）三原色的组合来表示每个像素的颜色
- 但与索引图像不同的是，RGB图像每一个像素的颜色值（由RGB三原色表示）直接存放在图像矩阵中，由于每一像素的颜色需由R、G、B三个分量来表示，M、N分别表示图像的行列数，三个M x N的二维矩阵分别表示各个像素的R、G、B三个颜色分量
- RGB图像的数据类型一般为8位无符号整形，通常用于表示和存放真彩色图像

## OpenCV简介
### OpenCV
#### OpenCV是一款由Intel公司俄罗斯团队发起并参与和维护的一个计算机视觉处理开源软件库，支持与计算机视觉和机器学习相关的众多算法，并且正在日益扩展
### OpenCV的优势
#### 编程语言
OpenCV基于C++实现，同时提供python, Ruby, Matlab等语言的接口。OpenCV-Python是OpenCV的Python API，结合了OpenCV C++ API和Python语言的最佳特性
#### 跨平台
可以在不同的系统平台上使用，包括Windows，Linux，OS X，Android和iOS。基于CUDA和OpenCL的高速GPU操作接口也在积极开发中
#### 活跃的开发团队
#### 丰富的API
完善的传统计算机视觉算法，涵盖主流的机器学习算法，同时添加了对深度学习的支持

### OpenCV-Python
OpenCV-Python是一个Python绑定库，旨在解决计算机视觉问题

Python是一种由Guido van Rossum开发的通用编程语言，它很快就变得非常流行，主要是因为它的简单性和代码可读性。它使程序员能够用更少的代码行表达思想，而不会降低可读性

与C / C++等语言相比，Python速度较慢。也就是说，Python可以使用C / C++轻松扩展，这使我们可以在C / C++中编写计算密集型代码，并创建可用作Python模块的Python包装器。这给我们带来了两个好处

- 代码与原始C / C++代码一样快（因为它是在后台工作的实际C++代码）
- 在Python中编写代码比使用C / C++更容易

OpenCV-Python是原始OpenCV C++实现的Python包装器

OpenCV-Python使用Numpy，这是一个高度优化的数据库操作库，具有MATLAB风格的语法。所有OpenCV数组结构都转换为Numpy数组。这也使得与使用Numpy的其他库（如SciPy和Matplotlib）集成更容易

### OpenCV部署方法
- 安装OpenCV之前需要先安装numpy, matplotlib

- 创建Python虚拟环境cv, 在cv中安装即可

- 先安装OpenCV-Python, 由于一些经典的算法被申请了版权，新版本有很大的限制，所以选用3.4.3以下的版本

- 如果要利用SIFT和SURF等进行特征提取时，还需要安装opencv-contrib-python
```
pip install opencv-contrib-python==3.4.2.17
```

## OpenCV的模块
### 基础模块
#### ```core``` 模块
core模块实现了最核心的数据结构及其基本运算，如绘图函数、数组操作相关函数等
#### ```highgui``` 模块
highgui模块实现了视频与图像的读取、显示、存储等接口
#### ```imgproc``` 模块
imgproc模块实现了图像处理的基础方法，包括图像滤波、图像的几何变换、平滑、阈值分割、形态学处理、边缘检测、目标检测、运动分析和对象跟踪等

### 更高层次的方向及应用模块
#### ```features2d``` 模块
features2d模块用于提取图像特征以及特征匹配，nonfree模块实现了一些专利算法，如sift特征
#### ```objdetect``` 模块
objdetect模块实现了一些目标检测的功能，经典的基于Haar、LBP特征的人脸检测，基于HOG的行人、汽车等目标检测，分类器使用Cascade Classification（级联分类）和Latent SVM等
#### ```stitching``` 模块
stitching模块实现了图像拼接功能
#### ```FLANN``` 模块
FLANN模块（Fast Library for Approximate Nearest Neighbors），包含快速近似最近邻搜索FLANN 和聚类Clustering算法
#### ```ml``` 模块
ml模块机器学习模块（SVM，决策树，Boosting等等）
#### ```photo``` 模块
photo模块包含图像修复和图像去噪两部分
#### ```video``` 模块
video模块针对视频处理，如背景分离，前景检测、对象跟踪等
#### ```calib3d``` 模块
calib3d模块即Calibration（校准）3D，这个模块主要是相机校准和三维重建相关的内容。包含了基本的多视角几何算法，单个立体摄像头标定，物体姿态估计，立体相似性算法，3D信息的重建等等
#### ```G-API``` 模块
G-API模块包含超高效的图像处理pipeline引擎


# OpenCV基本操作
## 图像的基础操作
### 图像的IO操作
#### 读取图像
##### API
```
cv.imread()
```
##### 参数
- 要读取的图像路径
- 读取方式的标志
  - ```cv.IMREAD*COLOR```--------------以彩色模式加载图像，任何图像的透明度都将被忽略。这是默认参数
  - ```cv.IMREAD*GRAYSCALE```----------以灰度模式加载图像
  - ```cv.IMREAD_UNCHANGED```----------包括alpha通道的加载图像模式

**可以使用1、0或者-1来替代上面三个标志**

##### 参考代码
```
import numpy as np
import cv2
# 以灰度图的形式读取图像
img = cv2.imread('messi5.jpg',0)
```

#### 显示图像
##### API
```
cv.imshow()
```
##### 参数
- 显示图像的窗口名称，以字符串类型表示
- 要加载的图像

**注意：在调用显示图像的API后，要调用cv.waitKey()给图像绘制留下时间，否则窗口会出现无响应情况，并且图像无法显示出来**

##### 使用matplotlib对图像进行展示
###### API
```
plt.imshow(img[:,:,::-1])
```
**注意：使用matplotlib展示图像，需要使用 ```[:,:,::-1]``` 转换RGB通道**

##### 参考代码
```
# opencv中显示
cv.imshow('image',img)
cv.waitKey(0)
# matplotlib中展示
plt.imshow(img[:,:,::-1])
```

#### 保存图像
##### API
```
cv.imwrite()
```
##### 参数
- 文件名，要保存在哪里
- 要保存的图像
##### 参考代码
```
cv.imwrite('messigray.png',img)
```
### 绘制几何图形
#### 绘制直线
##### API
```
cv.line(img,start,end,color,thickness)
```
##### 参数
- img  
要绘制直线的图像
- start,end  
直线的起点和终点
- color  
线条的颜色
- thickness  
线条宽度

#### 绘制圆形
##### API
```
cv.circle(img,centerpoint, r, color, thickness)
```
##### 参数
- img  
要绘制圆形的图像
- centerpoint, r  
圆心和半径
- color  
线条的颜色
- thickness  
线条宽度，为-1时生成闭合图案并填充颜色

#### 绘制矩形
##### API
```
cv.rectangle(img,leftupper,rightdown,color,thickness)
```
##### 参数
- img  
要绘制矩形的图像
- leftupper, rightdown  
矩形的左上角和右下角坐标
- color  
线条的颜色
- thickness  
线条宽度

#### 向图像中添加文字
##### API
```
cv.putText(img,text,station, font, fontsize,color,thickness,cv.LINE_AA)
```
##### 参数
- img  
图像
- text  
要写入的文本数据
- station  
文本的放置位置
- font  
字体
- fontsize   
字体大小

#### 参考代码
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1 创建一个空白的图像
img = np.zeros((512,512,3), np.uint8)
# 2 绘制图形
cv.line(img,(0,0),(511,511),(255,0,0),5)
cv.rectangle(img,(384,0),(510,128),(0,255,0),3)
cv.circle(img,(447,63), 63, (0,0,255), -1)
font = cv.FONT_HERSHEY_SIMPLEX
cv.putText(img,'OpenCV',(10,500), font, 4,(255,255,255),2,cv.LINE_AA)
# 3 图像展示
plt.imshow(img[:,:,::-1])
plt.title('匹配结果'), plt.xticks([]), plt.yticks([])
plt.show()
```

### 获取并修改图像中的像素点
#### 可以通过行和列的坐标值获取该像素点的像素值
- 对于BGR图像，它返回一个蓝，绿，红值的数组
- 对于灰度图像，仅返回相应的强度值。使用相同的方法对像素值进行修改
#### 参考代码
```
import numpy as np
import cv2 as cv
img = cv.imread('messi5.jpg')
# 获取某个像素点的值
px = img[100,100]
# 仅获取蓝色通道的强度值
blue = img[100,100,0]
# 修改某个位置的像素值
img[100,100] = [255,255,255]
```
### 获取图像的属性
图像属性包括行数，列数和通道数，图像数据类型，像素数等
#### 形状
```
img.shape
```
#### 图像大小
```
img.size
```
#### 数据类型
```
img.dtype
```
### 图像通道的拆分与合并
有时需要在B，G，R通道图像上单独工作。在这种情况下，需要将BGR图像分割为单个通道。或者在其他情况下，可能需要将这些单独的通道合并到BGR图像。可以通过以下方式完成
#### 通道拆分
```
b,g,r = cv.split(img)
```
#### 通道合并
```
img = cv.merge((b,g,r))
```
### 色彩空间的改变
OpenCV中有150多种颜色空间转换方法。最广泛使用的转换方法有两种，BGR↔Gray和BGR↔HSV
#### API
```
cv.cvtColor(input_image，flag)
```
#### 参数
- ```input_image```  
进行颜色空间转换的图像
- ```flag```  
转换类型
- ```cv.COLOR_BGR2GRAY```  
BGR↔Gray
- ```cv.COLOR_BGR2HSV```  
BGR→HSV

## 图像的算术操作
### 图像的加法
可以使用OpenCV的cv.add()函数把两幅图像相加，或者可以简单地通过numpy操作添加两个图像，如res = img1 + img2。两个图像应该具有相同的大小和类型，或者第二个图像可以是标量值

OpenCV加法和Numpy加法之间存在差异
- OpenCV的加法是饱和操作  
即像素值超过255，会设为255

- Numpy添加是模运算  
如果像素值超过255，会对256取模，例如相加后为260，则结果为260 % 256 = 4

#### API
##### OpenCV的加法
```
cv.add()
```
##### Numpy添加
- 直接相加

- ```np.add()```

### 图像的混合
其实也是加法，但是不同的是两幅图像的权重不同，这就会给人一种混合或者透明的感觉。图像混合的计算公式如下

$$
g(x) = (1-\alpha) f_0(x) + \alpha f_1(x)
$$

#### API
```
cv.addWeighted(img1,α,img2,β,γ)
```
##### 公式为

$$
\text{dst} = \alpha \cdot \text{img}_1 + \beta \cdot \text{img}_2 + \gamma
$$

**α和β之和一般要为1**

*注意：无论是加法还是混合，都要求两幅图像是相同大小的*



# OpenCV图像处理
## 几何变换
### 图像缩放
对图像的大小进行调整，即使图像放大或缩小
#### API
```
cv2.resize(src,dsize,fx=0,fy=0,interpolation=cv2.INTER_LINEAR)
```
#### 参数
- ```src```
输入图像
- ```dsize```
绝对尺寸，直接指定调整后图像的大小
- ```fx,fy```
相对尺寸，将dsize设置为None，然后将fx和fy设置为比例因子即可
- ```interpolation```
插值方法
  - ```cv2.INTER_LINEAR```
双线性插值法
  - ```cv2.INTER_NEAREST```
最近邻插值
  - ```cv2.INTER_AREA```
像素区域重采样（默认）
  - ```cv2.INTER_CUBIC```
双三次插值

#### 参考代码
```
import cv2 as cv
# 1. 读取图片
img1 = cv.imread("./image/dog.jpeg")
# 2.图像缩放
# 2.1 绝对尺寸
rows,cols = img1.shape[:2]
res = cv.resize(img1,(2*cols,2*rows),interpolation=cv.INTER_CUBIC)

# 2.2 相对尺寸
res1 = cv.resize(img1,None,fx=0.5,fy=0.5)

# 3 图像显示
# 3.1 使用opencv显示图像(不推荐)
cv.imshow("orignal",img1)
cv.imshow("enlarge",res)
cv.imshow("shrink）",res1)
cv.waitKey(0)

# 3.2 使用matplotlib显示图像
fig,axes=plt.subplots(nrows=1,ncols=3,figsize=(10,8),dpi=100)
axes[0].imshow(res[:,:,::-1])
axes[0].set_title("绝对尺度（放大）")
axes[1].imshow(img1[:,:,::-1])
axes[1].set_title("原图")
axes[2].imshow(res1[:,:,::-1])
axes[2].set_title("相对尺度（缩小）")
plt.show()
```
### 图像平移
图像平移将图像按照指定方向和距离，移动到相应的位置
#### API
```
cv.warpAffine(img,M,dsize)
```
#### 参数
- ```img```
输入图像
- ```M```
2∗3移动矩阵

对于(x,y)处的像素点，要把它移动到(x+t_x,y+t_y)处时，M矩阵应如下设置：
```
M = [[1,0,t_x],[0,1,t_y],[]]
```
**注意：将M设置为 ```np.float32``` 类型的Numpy数组**
- dsize: 输出图像的大小

**注意：输出图像的大小，它应该是(宽度，高度)的形式。width=列数，height=行数**

#### 参考代码
将图像的像素点移动(50,100)的距离
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1. 读取图像
img1 = cv.imread("./image/image2.jpg")

# 2. 图像平移
rows,cols = img1.shape[:2]
M = M = np.float32([[1,0,100],[0,1,50]])# 平移矩阵
dst = cv.warpAffine(img1,M,(cols,rows))

# 3. 图像显示
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img1[:,:,::-1])
axes[0].set_title("原图")
axes[1].imshow(dst[:,:,::-1])
axes[1].set_title("平移后结果")
plt.show()
```

### 图像旋转
图像旋转是指图像按照某个位置转动一定角度的过程，旋转中图像仍保持这原始尺寸。图像旋转后图像的水平对称轴、垂直对称轴及中心坐标原点都可能会发生变换，因此需要对图像旋转中的坐标进行相应转换
#### 图像旋转原理
假设图像逆时针旋转θ，则根据坐标转换可得旋转转换为:

$$
x' = r \cos(\alpha - \theta)
$$

其中，

$$
r = \sqrt{x^2 + y^2}
$$


$$
\sin \alpha = \frac{y}{\sqrt{x^2 + y^2}}
$$


$$
\cos \alpha = \frac{x}{\sqrt{x^2 + y^2}}
$$


带入上面的公式中，有

$$
x' = x \cos\theta + y \sin\theta
$$


$$
y' = -x \sin\theta + y \cos\theta
$$


也可以写成

$$
\begin{bmatrix} x' & y' & 1 \end{bmatrix} =
\begin{bmatrix} x & y & 1 \end{bmatrix}
\begin{bmatrix} 
\cos\theta & -\sin\theta & 0 \\ 
\sin\theta & \cos\theta & 0 \\ 
0 & 0 & 1 
\end{bmatrix}
$$

同时要修正原点的位置，因为原图像中的坐标原点在图像的左上角，经过旋转后图像的大小会有所变化，原点也需要修正

假设在旋转的时候是以旋转中心为坐标原点的，旋转结束后还需要将坐标原点移到图像左上角，也就是还要进行一次变换

$$
\begin{bmatrix} x'' & y'' & 1 \end{bmatrix} =
\begin{bmatrix} x' & y' & 1 \end{bmatrix}
\begin{bmatrix} 
1 & 0 & 0 \\ 
0 & -1 & 0 \\ 
\text{left} & \text{top} & 1 
\end{bmatrix}
$$


$$
\begin{bmatrix} x'' & y'' & 1 \end{bmatrix} =
\begin{bmatrix} x & y & 1 \end{bmatrix}
\begin{bmatrix} 
\cos\theta & -\sin\theta & 0 \\ 
\sin\theta & \cos\theta & 0 \\ 
0 & 0 & 1 
\end{bmatrix}
\begin{bmatrix} 
1 & 0 & 0 \\ 
0 & -1 & 0 \\ 
\text{left} & \text{top} & 1 
\end{bmatrix}
$$

#### OpenCV实现图像旋转
在OpenCV中图像旋转首先根据旋转角度和旋转中心获取旋转矩阵，然后根据旋转矩阵进行变换，即可实现任意角度和任意中心的旋转效果
##### API
```
cv2.getRotationMatrix2D(center, angle, scale)
```
##### 参数
- center
旋转中心
- angle
旋转角度
- scale
缩放比例
##### 返回
- M
旋转矩阵  
调用 ```cv.warpAffine``` 完成图像的旋转

#### 参考代码
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1 读取图像
img = cv.imread("./image/image2.jpg")

# 2 图像旋转
rows,cols = img.shape[:2]
# 2.1 生成旋转矩阵
M = cv.getRotationMatrix2D((cols/2,rows/2),90,1)
# 2.2 进行旋转变换
dst = cv.warpAffine(img,M,(cols,rows))

# 3 图像展示
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img1[:,:,::-1])
axes[0].set_title("原图")
axes[1].imshow(dst[:,:,::-1])
axes[1].set_title("旋转后结果")
plt.show()
```

### 仿射变换
#### 仿射变换原理
- 图像的仿射变换涉及到图像的形状位置角度的变化，是深度学习预处理中常到的功能,仿射变换主要是对图像的缩放，旋转，翻转和平移等操作的组合

- 图像的仿射变换，图1中的点1, 2 和 3 与图二中三个点一一映射, 仍然形成三角形, 但形状已经大大改变，通过这样两组三点（兴趣点）求出仿射变换， 接下来就能把仿射变换应用到图像中所有的点中，就完成了图像的仿射变换

#### OpenCV实现原理
在OpenCV中，仿射变换的矩阵是一个2*3的矩阵

$$
M = [A, B] =
\begin{bmatrix} 
a_{00} & a_{01} & b_0 \\ 
a_{10} & a_{11} & b_1 
\end{bmatrix}
$$

其中，左边的2\*2子矩阵A是线性变换矩阵，右边的2*1子矩阵B是平移项

$$
A =
\begin{bmatrix} 
a_{00} & a_{01} \\ 
a_{10} & a_{11} 
\end{bmatrix}, \quad
B =
\begin{bmatrix} 
b_0 \\ 
b_1 
\end{bmatrix}
$$

对于图像上的任一位置(x,y)，仿射变换执行的是如下的操作

$$
T_{\text{affine}} = A 
\begin{bmatrix} x \\ y \end{bmatrix} + B = M 
\begin{bmatrix} x \\ y \\ 1 \end{bmatrix}
$$

需要注意的是，对于图像而言，宽度方向是x，高度方向是y，坐标的顺序和图像像素对应下标一致。所以原点的位置不是左下角而是右上角，y的方向也不是向上，而是向下

在仿射变换中，原图中所有的平行线在结果图像中同样平行

为了创建这个矩阵我们需要从原图像中找到三个点以及他们在输出图像中的位置。然后 ```cv2.getAffineTransform``` 会创建一个 2x3 的矩阵，最后这个矩阵会被传给函数 ```cv2.warpAffine```

#### 参考代码
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1 图像读取
img = cv.imread("./image/image2.jpg")

# 2 仿射变换
rows,cols = img.shape[:2]
# 2.1 创建变换矩阵
pts1 = np.float32([[50,50],[200,50],[50,200]])
pts2 = np.float32([[100,100],[200,50],[100,250]])
M = cv.getAffineTransform(pts1,pts2)
# 2.2 完成仿射变换
dst = cv.warpAffine(img,M,(cols,rows))

# 3 图像显示
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img[:,:,::-1])
axes[0].set_title("原图")
axes[1].imshow(dst[:,:,::-1])
axes[1].set_title("仿射后结果")
plt.show()
```
### 透射变换
透射变换是视角变化的结果，是指利用透视中心、像点、目标点三点共线的条件，按透视旋转定律使承影面（透视面）绕迹线（透视轴）旋转某一角度，破坏原有的投影光线束，仍能保持承影面上投影几何图形不变的变换
#### 透射变换原理
透射变换的本质将图像投影到一个新的视平面，其通用变换公式为

$$
\begin{bmatrix} x' & y' & z' \end{bmatrix}
=
\begin{bmatrix} u & v & w \end{bmatrix}
\begin{bmatrix} 
a_{00} & a_{01} & a_{02} \\ 
a_{10} & a_{11} & a_{12} \\ 
a_{20} & a_{21} & a_{22} 
\end{bmatrix}
$$

其中，(u,v)是原始的图像像素坐标，w取值为1，(x=x'/z',y=y'/z')是透射变换后的结果。后面的矩阵称为透视变换矩阵，一般情况下，将其分为三部分

$$
T =
\begin{bmatrix} 
a_{00} & a_{01} & a_{02} \\ 
a_{10} & a_{11} & a_{12} \\ 
a_{20} & a_{21} & a_{22} 
\end{bmatrix}
=
\begin{bmatrix} 
T_1 & T_2 \\ 
T_3 & a_{22} 
\end{bmatrix}
$$

其中,T1表示对图像进行线性变换，T2对图像进行平移，T3表示对图像进行投射变换，a_22一般设为1

#### OpenCV实现原理
在opencv中，我们要找到四个点，其中任意三个不共线，然后获取变换矩阵T，再进行透射变换。通过函数 ```cv.getPerspectiveTransform``` 找到变换矩阵，将 ```cv.warpPerspective``` 应用于此3x3变换矩阵

#### 参考代码
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1 读取图像
img = cv.imread("./image/image2.jpg")
# 2 透射变换
rows,cols = img.shape[:2]
# 2.1 创建变换矩阵
pts1 = np.float32([[56,65],[368,52],[28,387],[389,390]])
pts2 = np.float32([[100,145],[300,100],[80,290],[310,300]])

T = cv.getPerspectiveTransform(pts1,pts2)
# 2.2 进行变换
dst = cv.warpPerspective(img,T,(cols,rows))

# 3 图像显示
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img[:,:,::-1])
axes[0].set_title("原图")
axes[1].imshow(dst[:,:,::-1])
axes[1].set_title("透射后结果")
plt.show()
```

### 图像金字塔
#### 定义
- 图像金字塔是图像多尺度表达的一种，最主要用于图像的分割，是一种以多分辨率来解释图像的有效但概念简单的结构
- 图像金字塔用于机器视觉和图像压缩，一幅图像的金字塔是一系列以金字塔形状排列的分辨率逐步降低，且来源于同一张原始图的图像集合。其通过梯次向下采样获得，直到达到某个终止条件才停止采样
- 金字塔的底部是待处理图像的高分辨率表示，而顶部是低分辨率的近似，层级越高，图像越小，分辨率越低

#### API
##### 对图像进行上采样
```
cv.pyrUp(img)
```
##### 对图像进行下采样
```
cv.pyrDown(img)
```
#### 参考代码
```
import numpy as np
import cv2 as cv
import matplotlib.pyplot as plt
# 1 图像读取
img = cv.imread("./image/image2.jpg")
# 2 进行图像采样
up_img = cv.pyrUp(img)  # 上采样操作
img_1 = cv.pyrDown(img)  # 下采样操作
# 3 图像显示
cv.imshow('enlarge', up_img)
cv.imshow('original', img)
cv.imshow('shrink', img_1)
cv.waitKey(0)
cv.destroyAllWindows()
```

## 形态学(Morphology)
### 连通性
#### 邻接关系
在图像中，最小的单位是像素，每个像素周围有8个邻接像素，常见的邻接关系有3种：4邻接、8邻接和D邻接
- 4邻接  
像素p(x,y)的4邻域是：(x+1,y)；(x-1,y)；(x,y+1)；(x,y-1)，用N_4(p)表示像素p的4邻接
- D邻接  
像素p(x,y)的D邻域是：对角上的点 (x+1,y+1)；(x+1,y-1)；(x-1,y+1)；(x-1,y-1)，用N_D(p)表示像素p的D邻域
- 8邻接  
像素p(x,y)的8邻域是： 4邻域的点 ＋ D邻域的点，用N_8(p)表示像素p的8邻域

#### 连通性
连通性是描述区域和边界的重要概念，两个像素连通的两个必要条件是：
- 两个像素的位置是否相邻
- 两个像素的灰度值是否满足特定的相 似性准则（或者是否相等）
#### 连通性分类
根据连通性的定义，有4联通、8联通和m联通三种
- 4连通性（4-connectivity）  
对于具有值V的像素p和q，如果q在集合N_4(p)中，则称这两个像素是4连通
- 8连通性（8-connectivity）  
对于具有值V的像素p和q，如果q在集合N_8(p)中，则称这两个像素是8连通
- M连通性（M-connectivity）  
对于具有值V的像素p和q，如果  
  - q在集合N_4(p)中
  - 或q在集合N_D(p)中，并且N_4(p)与N_4(q)的交集为空（没有值V的像素）  
则称这两个像素是M连通的，即4连通和D连通的混合连通

### 形态学操作
形态学转换是基于图像形状的一些简单操作。它通常在二进制图像上执行。腐蚀和膨胀是两个基本的形态学运算符。然后它的变体形式如开运算，闭运算，礼帽黑帽等
#### 腐蚀和膨胀
##### 定义
- 腐蚀和膨胀是最基本的形态学操作，腐蚀和膨胀都是针对白色部分（高亮部分）而言的
- 膨胀就是使图像中高亮部分扩张，效果图拥有比原图更大的高亮区域
- 腐蚀是原图中的高亮区域被蚕食，效果图拥有比原图更小的高亮区域
- 膨胀是求局部最大值的操作，腐蚀是求局部最小值的操作

#### 腐蚀
##### 具体操作
用一个结构元素扫描图像中的每一个像素，用结构元素中的每一个像素与其覆盖的像素做“与”操作，如果都为1，则该像素为1，否则为0
##### 腐蚀的作用
消除物体边界点，使目标缩小，可以消除小于结构元素的噪声点
##### API
```
cv.erode(img,kernel,iterations)
```
##### 参数
- img: 要处理的图像
- kernel: 核结构
- iterations: 腐蚀的次数，默认是1

#### 膨胀
##### 具体操作
用一个结构元素扫描图像中的每一个像素，用结构元素中的每一个像素与其覆盖的像素做“与”操作，如果都为0，则该像素为0，否则为1
##### 膨胀的作用
将与物体接触的所有背景点合并到物体中，使目标增大，可添补目标中的孔洞
##### API
```
cv.dilate(img,kernel,iterations)
```
##### 参数
- img: 要处理的图像
- kernel: 核结构
- iterations: 腐蚀的次数，默认是1

#### 开闭运算
开运算和闭运算是将腐蚀和膨胀按照一定的次序进行处理。 但这两者并不是可逆的，即先开后闭并不能得到原来的图像
##### 开运算
开运算是先腐蚀后膨胀
###### 作用
分离物体，消除小区域
###### 特点
消除噪点，去除小的干扰块，而不影响原来的图像
##### 闭运算
闭运算与开运算相反，是先膨胀后腐蚀
###### 作用
消除/“闭合”物体里面的孔洞
###### 特点
可以填充闭合区域

##### API
```
cv.morphologyEx(img, op, kernel)
```
##### 参数
- img
要处理的图像
- op
处理方式
  - 若进行开运算，则设为 ```cv.MORPH_OPEN```
  - 若进行闭运算，则设为 ```cv.MORPH_CLOSE```
- Kernel
核结构


#### 礼帽和黑帽
##### 礼帽运算
原图像与“开运算”的结果图之差
###### 数学表达式
```
dst = tophat(src,element) = src - open(src,element)
```
- 因为开运算带来的结果是放大了裂缝或者局部低亮度的区域，因此，从原图中减去开运算后的图，得到的效果图突出了比原图轮廓周围的区域更明亮的区域，且这一操作和选择的核的大小相关。
- 礼帽运算用来分离比邻近点亮一些的斑块。当一幅图像具有大幅的背景的时候，而微小物品比较有规律的情况下，可以使用顶帽运算进行背景提取

##### 黑帽运算
为”闭运算“的结果图与原图像之差
###### 数学表达式
```
dst = blackhat(src,element) =  close(src,element) - src
```
- 黑帽运算后的效果图突出了比原图轮廓周围的区域更暗的区域，且这一操作和选择的核的大小相关
- 黑帽运算用来分离比邻近点暗一些的斑块

##### API
```
cv.morphologyEx(img, op, kernel)
```
##### 参数
- img
要处理的图像
- op
处理方式
  - ```cv.MORPH_CLOSE``` : 闭运算
  - ```cv.MORPH_OPEN``` : 开运算
  - ```cv.MORPH_TOPHAT``` : 礼帽运算
  - ```cv.MORPH_BLACKHAT``` : 黑帽运算
- Kernel
核结构


## 图像平滑
### 图像噪声
由于图像采集、处理、传输等过程不可避免的会受到噪声的污染，妨碍人们对图像理解及分析处理。常见的图像噪声有高斯噪声、椒盐噪声等
#### 椒盐噪声
- 椒盐噪声也称为脉冲噪声，是图像中经常见到的一种噪声，它是一种随机出现的白点或者黑点，可能是亮的区域有黑色像素或是在暗的区域有白色像素（或是两者皆有）
- 椒盐噪声的成因可能是影像讯号受到突如其来的强烈干扰而产生、类比数位转换器或位元传输错误等。例如失效的感应器导致像素值为最小值，饱和的感应器导致像素值为最大值

#### 高斯噪声
- 高斯噪声是指噪声密度函数服从高斯分布的一类噪声。由于高斯噪声在空间和频域中数学上的易处理性，这种噪声(也称为正态噪声)模型经常被用于实践中
- 斯随机变量z的概率密度函数由下式给出


$$
p(z) = \frac{1}{\sqrt{2\pi} \sigma} e^{-\frac{(z - \mu)^2}{2\sigma^2}}
$$

其中z表示灰度值，μ表示z的平均值或期望值，σ表示z的标准差。标准差的平方σ^2称为z的方差

### 图像平滑处理
#### 概念
- 图像平滑从信号处理的角度看就是去除其中的高频信息，保留低频信息。因此我们可以对图像实施低通滤波。低通滤波可以去除图像中的噪声，对图像进行平滑
- 根据滤波器的不同可分为均值滤波，高斯滤波，中值滤波， 双边滤波

#### 均值滤波
##### 定义
- 采用均值滤波模板对图像噪声进行滤除。令S_{x y} 表示中心在(x, y)点，尺寸为m×n 的矩形子图像窗口的坐标组。 均值滤波器可表示为
f_hat(x,y) = 1/mn * Σg(s,t)
- 由一个归一化卷积框完成的。它只是用卷积框覆盖区域所有像素的平均值来代替中心元素
例如，3*3标准化的平均过滤器可以表示为


$$
K = \frac{1}{9}
\begin{bmatrix} 
1 & 1 & 1 \\ 
1 & 1 & 1 \\ 
1 & 1 & 1 
\end{bmatrix}
$$


##### 均值滤波的优点是算法简单，计算速度较快，缺点是在去噪的同时去除了很多细节部分，将图像变得模糊

##### API
```
cv.blur(src, ksize, anchor, borderType)
```
##### 参数
- src：输入图像
- ksize：卷积核的大小
- anchor：默认值 (-1,-1) ，表示核中心
- borderType：边界类型

#### 高斯滤波
##### 定义
- 二维高斯是构建高斯滤波器的基础，其概率分布函数如下所示


$$
G(x, y) = \frac{1}{2\pi\sigma^2} \exp\left( -\frac{x^2 + y^2}{2\sigma^2} \right)
$$


- G(x,y) 的分布是一个突起的帽子的形状。这里的σ可以看作两个值，一个是x方向的标准差 σ_x，另一个是y方向的标准差 σ_y

- ​当σ_x和σ_y取值越大，整个形状趋近于扁平；当σ_x和σ_y取值越小整个形状越突起

- 正态分布是一种钟形曲线，越接近中心，取值越大，越远离中心，取值越小。计算平滑结果时，只需要将"中心点"作为原点，其他点按照其在正态曲线上的位置，分配权重，就可以得到一个加权平均值
- 高斯平滑在从图像中去除高斯噪声方面非常有效

##### 高斯平滑的流程
- 首先确定权重矩阵
  - 假定中心点的坐标是（0,0），那么距离它最近的8个点的坐标如下

(-1,1)  (0,1)  (1,1)  
(-1,0)  (0,0)  (1,0)  
(-1,-1) (0,-1) (1,-1)  
更远的点以此类推

  - 为了计算权重矩阵，需要设定σ的值
  - 这9个点的权重总和不为1，如果只计算这9个点的加权平均，还必须让它们的权重之和等于1，得到最终的权重矩阵
- 计算高斯模糊
  - 有了权重矩阵，就可以计算高斯模糊的值了
  - 假设现有9个像素点，每个点乘以对应的权重值，将这9个值加起来，就是中心点的高斯模糊的值

- 对所有点重复这个过程，就得到了高斯模糊后的图像。如果原图是彩色图片，可以对RGB三个通道分别做高斯平滑

##### API
```
cv2.GaussianBlur(src,ksize,sigmaX,sigmay,borderType)
```
##### 参数
- src: 输入图像
- ksize:高斯卷积核的大小  
**注意：卷积核的宽度和高度都应为奇数，且可以不同**
- sigmaX: 水平方向的标准差
- sigmaY: 垂直方向的标准差，默认值为0，表示与sigmaX相同
- borderType:填充边界类型

##### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 图像读取
img = cv.imread('./image/dogGasuss.jpeg')
# 2 高斯滤波
blur = cv.GaussianBlur(img,(3,3),1)
# 3 图像显示
plt.figure(figsize=(10,8),dpi=100)
plt.subplot(121),plt.imshow(img[:,:,::-1]),plt.title('原图')
plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(blur[:,:,::-1]),plt.title('高斯滤波后结果')
plt.xticks([]), plt.yticks([])
plt.show()
```
#### 中值滤波
##### 定义
- 中值滤波是一种典型的非线性滤波技术，基本思想是用像素点邻域灰度值的中值来代替该像素点的灰度值
- 中值滤波对椒盐噪声（salt-and-pepper noise）来说尤其有用，因为它不依赖于邻域内那些与典型值差别很大的值
##### API
```
cv.medianBlur(src, ksize)
```
##### 参数
- src：输入图像
- ksize：卷积核的大小

##### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 图像读取
img = cv.imread('./image/dogsp.jpeg')
# 2 中值滤波
blur = cv.medianBlur(img,5)
# 3 图像展示
plt.figure(figsize=(10,8),dpi=100)
plt.subplot(121),plt.imshow(img[:,:,::-1]),plt.title('原图')
plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(blur[:,:,::-1]),plt.title('中值滤波后结果')
plt.xticks([]), plt.yticks([])
plt.show()
```

## 直方图
### 灰度直方图
#### 原理
- 直方图是对数据进行统计的一种方法，并且将统计值组织到一系列实现定义好的 bin 当中。其中， bin 为直方图中经常用到的一个概念，可以译为 “直条” 或 “组距”，其数值是从数据中计算出的特征统计量，这些数据可以是诸如梯度、方向、色彩或任何其他特征
- 图像直方图（Image Histogram）是用以表示数字图像中亮度分布的直方图，标绘了图像中每个亮度值的像素个数。这种直方图中，横坐标的左侧为较暗的区域，而右侧为较亮的区域。因此一张较暗图片的直方图中的数据多集中于左侧和中间部分，而整体明亮、只有少量阴影的图像则相反

*注意：直方图是根据灰度图进行绘制的，而不是彩色图像*

 假设有一张图像的信息（灰度值 0 - 255，已知数字的范围包含 256 个值，于是可以按一定规律将这个范围分割成子区域（也就是 bins）。如


$$
[0,255] = [0,15] \cup [16,30] \cup \dots \cup [240,255]
$$

然后再统计每一个 bin(i) 的像素数目。可以得到直方图（其中 x 轴表示 bin，y 轴表示各个 bin 中的像素个数）

#### 直方图的一些术语和细节
- dims  
需要统计的特征数目。通常dims = 1 ，即仅统计灰度值
- bins  
每个特征空间子区段的数目，可译为 “直条” 或 “组距”，在上例中， ```bins = 16```
- range  
要统计特征的取值范围。在上例中，range = [0, 255]

#### 直方图的意义
- 直方图是图像中像素强度分布的图形表达方式 
- 它统计了每一个强度值所具有的像素个数
- 不同的图像的直方图可能是相同的

#### 直方图的计算和绘制
使用OpenCV中的方法统计直方图，并使用matplotlib将其绘制出来
##### API
```
cv2.calcHist(images,channels,mask,histSize,ranges[,hist[,accumulate]])
```
##### 参数
- images  
原图像。当传入函数时应该用中括号 [] 括起来，例如：[img]

- channels  
如果输入图像是灰度图，它的值就是 [0]；如果是彩色图像的话，传入的参数可以是 [0]，[1]，[2] 它们分别对应着通道 B，G，R 　　

- mask  
掩模图像。要统计整幅图像的直方图就把它设为 None。但是如果想统计图像某一部分的直方图的话，就需要制作一个掩模图像，并使用它。（后边有例子） 　　

- histSize  
BIN 的数目。也应该用中括号括起来，例如：[256] 　　

- ranges  
像素值范围，通常为 [0，256]

##### 参考代码
```
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt
# 1 直接以灰度图的方式读入
img = cv.imread('./image/cat.jpeg',0)
# 2 统计灰度图
histr = cv.calcHist([img],[0],None,[256],[0,256])
# 3 绘制灰度图
plt.figure(figsize=(10,6),dpi=100)
plt.plot(histr)
plt.grid()
plt.show()
```
#### 掩膜
##### 定义
- 掩膜是用选定的图像、图形或物体，对要处理的图像进行遮挡，来控制图像 处理的区域
- 在数字图像处理中，通常使用二维矩阵数组进行掩膜。掩膜是由0和1组成一个二进制图像，利用该掩膜图像要处理的图像进行掩膜，其中1值的区域被处理，0 值区域被屏蔽，不会处理

##### 掩膜的主要用途
- 提取感兴趣区域  
用预先制作的感兴趣区掩模与待处理图像进行”与“操作，得到感兴趣区图像，感兴趣区内图像值保持不变，而区外图像值都为0
- 屏蔽作用  
用掩模对图像上某些区域作屏蔽，使其不参加处理或不参加处理参数的计算，或仅对屏蔽区作处理或统计
- 结构特征提取  
用相似性变量或图像匹配方法检测和提取图像中与掩模相似的结构特征
特殊形状图像制作
- 掩膜在遥感影像处理中使用较多，当提取道路或者河流，或者房屋时，通过一个掩膜矩阵来对图像进行像素过滤，然后将需要的地物或者标志突出显示出来
##### API
```
cv.calcHist（）
```
查找完整图像的直方图。如果要查找图像某些区域的直方图，只需在要查找直方图的区域上创建一个白色的掩膜图像，否则创建黑色，然后将其作为掩码mask传递即可

##### 参考代码
```
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt
# 1. 直接以灰度图的方式读入
img = cv.imread('./image/cat.jpeg',0)
# 2. 创建蒙版
mask = np.zeros(img.shape[:2], np.uint8)
mask[400:650, 200:500] = 255
# 3.掩模
masked_img = cv.bitwise_and(img,img,mask = mask)
# 4. 统计掩膜后图像的灰度图
mask_histr = cv.calcHist([img],[0],mask,[256],[1,256])
# 5. 图像展示
fig,axes=plt.subplots(nrows=2,ncols=2,figsize=(10,8))
axes[0,0].imshow(img,cmap=plt.cm.gray)
axes[0,0].set_title("原图")
axes[0,1].imshow(mask,cmap=plt.cm.gray)
axes[0,1].set_title("蒙版数据")
axes[1,0].imshow(masked_img,cmap=plt.cm.gray)
axes[1,0].set_title("掩膜后数据")
axes[1,1].plot(mask_histr)
axes[1,1].grid()
axes[1,1].set_title("灰度直方图")
plt.show()
```
### 直方图均衡化
#### 原理与应用
- 如果一幅图像整体很亮，那所有的像素值的取值个数应该都会很高。所以应该把它的直方图做一个横向拉伸，就可以扩大图像像素值的分布范围，提高图像的对比度，这就是直方图均衡化要做的事情
- “直方图均衡化”是把原始图像的灰度直方图从比较集中的某个灰度区间变成在更广泛灰度范围内的分布。直方图均衡化就是对图像进行非线性拉伸，重新分配图像像素值，使一定灰度范围内的像素数量大致相同
- 这种方法提高图像整体的对比度，特别是有用数据的像素值分布比较接近时，在X光图像中使用广泛，可以提高骨架结构的显示，另外在曝光过度或不足的图像中可以更好的突出细节

#### API
使用opencv进行直方图统计时，使用的API是
```
dst = cv.equalizeHist(img)
```
##### 参数
- img
灰度图像
##### 返回
- dst
均衡化后的结果

#### 参考代码
```
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt
# 1. 直接以灰度图的方式读入
img = cv.imread('./image/cat.jpeg',0)
# 2. 均衡化处理
dst = cv.equalizeHist(img)
# 3. 结果展示
fig,axes=plt.subplots(nrows=2,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img,cmap=plt.cm.gray)
axes[0].set_title("原图")
axes[1].imshow(dst,cmap=plt.cm.gray)
axes[1].set_title("均衡化后结果")
plt.show()
```

### 自适应的直方图均衡化
#### 直方图均衡存在的问题
直方图均衡，考虑的是图像的全局对比度。在进行完直方图均衡化之后，图片背景的对比度被改变了，但是可能导致部分区域太亮或太暗，丢失了很多信息，所以在许多情况下，这样做的效果并不好
#### 自适应的直方图均衡化原理
- 为了解决这个问题， 需要使用自适应的直方图均衡化
- 此时，整幅图像会被分成很多小块，这些小块被称为“tiles”（在 OpenCV 中 tiles 的 大小默认是 8x8），然后再对每一个小块分别进行直方图均衡化。 所以在每一个的区域中， 直方图会集中在某一个小的区域中
- 如果有噪声的话，噪声会被放大。为了避免这种情况的出现要使用对比度限制
- 对于每个小块来说，如果直方图中的 bin 超过对比度的上限的话，就把 其中的像素点均匀分散到其他 bins 中，然后在进行直方图均衡化
- 最后，为了 去除每一个小块之间的边界，再使用双线性差值，对每一小块进行拼接
- 总结来说，自适应的直方图均衡就是将整幅图像分成很多小块，然后再对每一个小块分别进行直方图均衡化，最后进行拼接

#### API
```
cv.createCLAHE(clipLimit, tileGridSize)
```
#### 参数
- clipLimit: 对比度限制，默认是40
- tileGridSize: 分块的大小，默认为8∗8

#### 参考代码
```
import numpy as np
import cv2 as cv
# 1. 以灰度图形式读取图像
img = cv.imread('./image/cat.jpeg',0)
# 2. 创建一个自适应均衡化的对象，并应用于图像
clahe = cv.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))
cl1 = clahe.apply(img)
# 3. 图像展示
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img,cmap=plt.cm.gray)
axes[0].set_title("原图")
axes[1].imshow(cl1,cmap=plt.cm.gray)
axes[1].set_title("自适应均衡化后的结果")
plt.show()
```


## 边缘检测
### 原理
- 边缘检测是图像处理和计算机视觉中的基本问题，边缘检测的目的是标识数字图像中亮度变化明显的点。图像属性中的显著变化通常反映了属性的重要事件和变化
- 图像边缘检测大幅度地减少了数据量，并且剔除了可以认为不相关的信息，保留了图像重要的结构属性
- 有许多方法用于边缘检测，它们的绝大部分可以划分为两类：基于搜索和基于零穿越
  - 基于搜索  
通过寻找图像一阶导数中的最大值来检测边界，然后利用计算结果估计边缘的局部方向，通常采用梯度的方向，并利用此方向找到局部梯度模的最大值，代表算法是Sobel算子和Scharr算子
  - 基于零穿越  
通过寻找图像二阶导数零穿越来寻找边界，代表算法是Laplacian算子

### Sobel检测算子
#### 概念
- Sobel边缘检测算法比较简单，实际应用中效率比canny边缘检测效率要高，但是边缘不如Canny检测的准确
- 但是很多实际应用的场合，sobel边缘却是首选，Sobel算子是高斯平滑与微分操作的结合体，所以其抗噪声能力很强，用途较多。尤其是效率要求较高，而对细纹理不太关心的时候

#### 原理
- 对于不连续的函数，一阶导数可以写作：


$$
f'(x) = f(x) - f(x-1) \quad \text{或} \quad f'(x) = f(x+1) - f(x)
$$


所以有：


$$
f'(x) = \frac{f(x+1) - f(x-1)}{2}
$$

假设要处理的图像为I，在两个方向求导
###### 水平变化
将图像I与奇数大小的模版进行卷积，结果为G_x。比如，当模板大小为3时, G_x为:

$$
G_x =
\begin{bmatrix}
-1 & 0 & 1 \\
-2 & 0 & 2 \\
-1 & 0 & 1
\end{bmatrix} * I
$$

###### 垂直变化
将图像I与奇数大小的模版进行卷积，结果为G_y。比如，当模板大小为3时, G_y为:

$$
G_y =
\begin{bmatrix}
-1 & -2 & -1 \\
0 & 0 & 0 \\
1 & 2 & 1
\end{bmatrix} * I
$$


###### 在图像的每一点，结合以上两个结果求出

$$
G = \sqrt{G_x^2 + G_y^2}
$$


统计极大值所在的位置，就是图像的边缘

#### Scharr函数
当内核大小为3时, 以上Sobel内核可能产生比较明显的误差，为解决这一问题，使用Scharr函数，但该函数仅作用于大小为3的内核。该函数的运算与Sobel函数一样快，但结果却更加精确，其计算方法为
###### 水平变化

$$
G_x =
\begin{bmatrix}
-3 & 0 & 3 \\
-10 & 0 & 10 \\
-3 & 0 & 3
\end{bmatrix} * I
$$


###### 垂直变化

$$
G_y =
\begin{bmatrix}
-3 & -10 & -3 \\
0 & 0 & 0 \\
3 & 10 & 3
\end{bmatrix} * I
$$

#### 利用OpenCV进行sobel边缘
##### API
```
Sobel_x_or_y = cv2.Sobel(src, ddepth, dx, dy, dst, ksize, scale, delta, borderType)
```
##### 参数
- src：传入的图像
- ddepth: 图像的深度，通常使用 ```cv.CV_16S```
- dx和dy: 指求导的阶数，0表示这个方向上没有求导，取值为0、1
- ksize: 是Sobel算子的大小，即卷积核的大小，必须为奇数1、3、5、7，默认为3  
*注意：如果ksize=-1，就演变成为3x3的Scharr算子*
- scale：缩放导数的比例常数，默认情况为没有伸缩系数
- borderType：图像边界的模式，默认值为 ```cv2.BORDER_DEFAULT```

*注意：Sobel函数求完导数后会有负值，还有会大于255的值。而原图像是uint8，即8位无符号数，所以Sobel建立的图像位数不够，会有截断。因此要使用16位有符号的数据类型，即 ```cv2.CV_16S```。处理完图像后，再使用 ```cv2.convertScaleAbs()``` 函数将其转回原来的uint8格式，否则图像无法显示*

##### 使用方法
###### 第1步
```
Sobel_x = cv2.Sobel(src, cv2.CV_16S, 1, 0, dst, ksize, scale, delta, borderType)
Sobel_y = cv2.Sobel(src, cv2.CV_16S, 0, 1, dst, ksize, scale, delta, borderType)
```
###### 第2步
```
Scale_x__abs = cv2.convertScaleAbs(Sobel_x)  # 格式转换函数
Scale_y__abs = cv2.convertScaleAbs(Sobel_y)
```
###### 第3步
```
result = cv2.addWeighted(Scale_x__abs, alpha, Scale_y__abs, beta, gamma) # 图像混合
```

#### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 读取图像
img = cv.imread('./image/horse.jpg',0)
# 2 计算Sobel卷积结果
x = cv.Sobel(img, cv.CV_16S, 1, 0)
y = cv.Sobel(img, cv.CV_16S, 0, 1)
# 3 将数据进行转换
Scale_absX = cv.convertScaleAbs(x)  # convert 转换  scale 缩放
Scale_absY = cv.convertScaleAbs(y)
# 4 结果合成
result = cv.addWeighted(Scale_absX, 0.5, Scale_absY, 0.5, 0)
# 5 图像显示
plt.figure(figsize=(10,8),dpi=100)
plt.subplot(121),plt.imshow(img,cmap=plt.cm.gray),plt.title('原图')
plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(result,cmap = plt.cm.gray),plt.title('Sobel滤波后结果')
plt.xticks([]), plt.yticks([])
plt.show()
```
将上述代码中计算sobel算子的部分中将ksize设为-1，就是利用Scharr进行边缘检测
```
x = cv.Sobel(img, cv.CV_16S, 1, 0, ksize = -1)
y = cv.Sobel(img, cv.CV_16S, 0, 1, ksize = -1)
```

### Laplacian算子
#### 原理
- Laplacian是利用二阶导数来检测边缘 。 因为图像是 “2维”, 我们需要在两个方向求导，如下式所示：


$$
\Delta src = \frac{\partial^2 src}{\partial x^2} + \frac{\partial^2 src}{\partial y^2}
$$


- 那不连续函数的二阶导数是:


$$
f''(x) = f'(x+1) - f'(x) = f(x+1) + f(x-1) - 2f(x)
$$


- 那使用的卷积核是:


$$
\text{kernel} =
\begin{bmatrix}
0 & 1 & 0 \\
1 & -4 & 1 \\
0 & 1 & 0
\end{bmatrix}
$$


#### OpenCV实现
##### API
```
laplacian = cv2.Laplacian(src, ddepth[, dst[, ksize[, scale[, delta[, borderType]]]]])
```
##### 参数
- Src  
需要处理的图像
- Ddepth  
图像的深度，-1表示采用的是原图像相同的深度，目标图像的深度必须大于等于原图像的深度
- ksize  
算子的大小，即卷积核的大小，必须为1,3,5,7

#### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 读取图像
img = cv.imread('./image/horse.jpg',0)
# 2 laplacian转换
result = cv.Laplacian(img,cv.CV_16S)
Scale_abs = cv.convertScaleAbs(result)
# 3 图像展示
plt.figure(figsize=(10,8),dpi=100)
plt.subplot(121),plt.imshow(img,cmap=plt.cm.gray),plt.title('原图')
plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(Scale_abs,cmap = plt.cm.gray),plt.title('Laplacian检测后结果')
plt.xticks([]), plt.yticks([])
plt.show()
```

### Canny边缘检测
Canny 边缘检测算法是一种非常流行的边缘检测算法，是 John F. Canny 于 1986年提出的，被认为是最优的边缘检测算法
#### 流程
Canny边缘检测算法是由4步构成
##### 第1步--噪声去除--高斯滤波
由于边缘检测很容易受到噪声的影响，所以首先使用5*5高斯滤波器去除噪声

##### 第2步--计算图像梯度--sobel算子，计算梯度大小和方向
对平滑后的图像使用 Sobel 算子计算水平方向和竖直方向的一阶导数（G_x 和 G_y）。根据得到的这两幅梯度图（G_x 和 G_y）找到边界的梯度和方向，公式如下

$$
\text{Edge\_Gradient}(G) = \sqrt{G_x^2 + G_y^2}
$$


$$
\text{Angle}(\theta) = \tan^{-1} \left(\frac{G_y}{G_x}\right)
$$

如果某个像素点是边缘，则其梯度方向总是垂直与边缘垂直。梯度方向被归为四类：垂直，水平，和两个对角线方向

##### 第3步--非极大值抑制--利用梯度方向像素来判断当前像素是否为边界点
- 在获得梯度的方向和大小之后，对整幅图像进行扫描，去除那些非边界上的点。对每一个像素进行检查，看这个点的梯度是不是周围具有相同梯度方向的点中最大的
- A点位于图像的边缘，在其梯度变化方向，选择像素点B和C，用来检验A点的梯度是否为极大值，若为极大值，则进行保留，否则A点被抑制，最终的结果是具有“细边”的二进制图像

##### 第4步--滞后阈值--设置两个阈值，确定最终的边界
现在要确定真正的边界。设置两个阈值： minVal 和 maxVal
- 当图像的灰度梯度高于 maxVal 时被认为是真的边界，低于 minVal 的边界会被抛弃
- 如果介于两者之间的话，就要看这个点是否与某个被确定为真正的边界点相连，如果是就认为它也是边界点，如果不是就抛弃
- 选择合适的 maxVal 和 minVal 对于能否得到好的结果非常重要


#### OpenCV实现
##### API
```
canny = cv2.Canny(image, threshold1, threshold2)
```
##### 参数
- image  
灰度图
- threshold1  
minval，较小的阈值将间断的边缘连接起来
- threshold2  
maxval，较大的阈值检测图像中明显的边缘

#### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 图像读取
img = cv.imread('./image/horse.jpg',0)
# 2 Canny边缘检测
lowThreshold = 0
max_lowThreshold = 100
canny = cv.Canny(img, lowThreshold, max_lowThreshold) 
# 3 图像展示
plt.figure(figsize=(10,8),dpi=100)
plt.subplot(121),plt.imshow(img,cmap=plt.cm.gray),plt.title('原图')
plt.xticks([]), plt.yticks([])
plt.subplot(122),plt.imshow(canny,cmap = plt.cm.gray),plt.title('Canny检测后结果')
plt.xticks([]), plt.yticks([])
plt.show()
```

### 算子比较
#### Roberts
对具有陡峭的低噪声的图像处理效果较好，但利用Roberts算子提取边缘的结果是边缘比较粗，因此边缘定位不是很准确
#### Sobel
对灰度渐变和噪声较多的图像处理效果比较好，Sobel算子对边缘定位比较准确
#### Kirsch
对灰度渐变和噪声较多的图像处理效果较好
#### Prewitt
对灰度渐变和噪声较多的图像处理效果较好
#### Laplacian
对图像中的阶跃性边缘点定位准确，对噪声非常敏感，丢失一部分边缘的方向信息，造成一些不连续的检测边缘
#### LoG/高斯差分 (Difference of Gaussians, DoG) 滤波器
LoG 算子经常出现双边缘像素边界，而且该检测方法对噪声比较敏感，所以很少用 LoG 算子检测边缘，而是用来判断边缘像素是位于图像的明区还是暗区
#### Canny
Canny算子不容易受噪声的干扰，能够检测到真正的弱边缘。Canny算子是edge函数中最有效的边缘检测方法。该方法的优点在于使用两种不同的阀值分别检测强边缘和弱边缘，并且仅当弱边缘与强边缘相连时，才将边缘包含在输出图像中。因此，这种方法不容易被噪声“填充”，更容易检测出真正的弱边缘


## 模板匹配
### 原理
模板匹配，就是在给定的图片中查找和模板最相似的区域，该算法的输入包括模板和图片，整个任务的思路就是按照滑窗的思路不断的移动模板图片，计算其与图像中对应区域的匹配度，最终将匹配度最高的区域选择为最终的结果

### 实现流程
#### 准备两幅图像
##### 原图像(I)
在这幅图中，找到与模板相匹配的区域
##### 模板(T)
与原图像进行比对的图像块

#### 滑动模板图像和原图像进行比对
将模板块每次移动一个像素 (从左往右，从上往下)，在每一个位置，都计算与模板图像的相似程度
- 对于每一个位置将计算的相似结果保存在结果矩阵（R）中。如果输入图像的大小（W*H）且模板图像的大小(w*h)，则输出矩阵R的大小为（W-w+1,H-h+1）将R显示为图像
- 获得上述图像后，查找最大值所在的位置，那么该位置对应的区域就被认为是最匹配的。对应的区域就是以该点为顶点，长宽和模板图像一样大小的矩阵

### OpenCV实现
#### API
```
res = cv.matchTemplate(img,template,method)
```
#### 参数
- img  
要进行模板匹配的图像
- Template  
模板
- method  
实现模板匹配的算法，主要有：
  - 平方差匹配(CV_TM_SQDIFF)：利用模板与图像之间的平方差进行匹配，最好的匹配是0，匹配越差，匹配的值越大
  - 相关匹配(CV_TM_CCORR)：利用模板与图像间的乘法进行匹配，数值越大表示匹配程度较高，越小表示匹配效果差
  - 利用相关系数匹配(CV_TM_CCOEFF)：利用模板与图像间的相关系数匹配，1表示完美的匹配，-1表示最差的匹配

完成匹配后，使用 ```cv.minMaxLoc()``` 方法查找最大值所在的位置即可。如果使用平方差作为比较方法，则最小值位置是最佳匹配位置

通过 ```matchTemplate``` 实现模板匹配，使用 ```minMaxLoc``` 定位最匹配的区域，并用矩形标注最匹配的区域

#### 参考代码
```
import cv2 as cv
import numpy as np
from matplotlib import pyplot as plt
# 1 图像和模板读取
img = cv.imread('./image/wulin2.jpeg')
template = cv.imread('./image/wulin.jpeg')
h,w,l = template.shape
# 2 模板匹配
# 2.1 模板匹配
res = cv.matchTemplate(img, template, cv.TM_CCORR)
# 2.2 返回图像中最匹配的位置，确定左上角的坐标，并将匹配位置绘制在图像上
min_val, max_val, min_loc, max_loc = cv.minMaxLoc(res)
# 使用平方差时最小值为最佳匹配位置
# top_left = min_loc
top_left = max_loc
bottom_right = (top_left[0] + w, top_left[1] + h)
cv.rectangle(img, top_left, bottom_right, (0,255,0), 2)
# 3 图像显示
plt.imshow(img[:,:,::-1])
plt.title('匹配结果'), plt.xticks([]), plt.yticks([])
plt.show()
```
#### 模板匹配的不足
模板匹配不适用于尺度变换，视角变换后的图像，这时我们就要使用关键点匹配算法，比较经典的关键点检测算法包括SIFT和SURF等，主要的思路是首先通过关键点检测算法获取模板和测试图片中的关键点；然后使用关键点匹配算法处理即可，这些关键点可以很好的处理尺度变化、视角变换、旋转变化、光照变化等，具有很好的不变性


## 霍夫变换
霍夫变换常用来提取图像中的直线和圆等几何形状
### 原理
- 在笛卡尔坐标系中，一条直线由两个点A=(x_1,y_1)和B=(x_2,y_2)确定
- 将直线y=kx+q可写成关于(k,q)的函数表达式


$$
q = -k x_1 + y_1
$$


$$
q = -k x_2 + y_2
$$


- 变换后的空间叫做霍夫空间
  - 笛卡尔坐标系中的一条直线，对应于霍夫空间中的一个点
  - 反过来，同样成立，霍夫空间中的一条线，对应于笛卡尔坐标系中一个点

- 如果在笛卡尔坐标系的点共线，那么这些点在霍夫空间中对应的直线交于一点
- 如果不止存在一条直线时，选择尽可能多的直线汇成的点，上图中三条直线汇成的A、B两点，将其对应回笛卡尔坐标系中的直线

- 如果直角坐标系中的直线是垂直于坐标系，需要将笛卡尔坐标系转换为极坐标
  - 直角坐标系y=ax+b和极坐标系的r=xcosθ+ysinθ是一样的，极坐标中的点对应于霍夫空间的线，这时的霍夫空间是不在是参数(k,q)的空间，而是(ρ,θ)的空间，ρ是原点到直线的垂直距离，θ表示直线的垂线与横轴顺时针方向的夹角，垂直线的角度为0度，水平线的角度是180度
- 只要求得霍夫空间中的交点的位置，即可得到原坐标系下的直线

### 实现流程
假设有一个大小为100*100的图片，使用霍夫变换检测图片中的直线，则步骤如下所示
- 直线都可以使用(ρ,θ)表示，首先创建一个2D数组，我们叫做累加器，初始化所有值为0，行表示ρ，列表示θ 
- 该数组的大小决定了结果的准确性，若希望角度的精度为1度，那就需要180列。对于ρ，最大值为图片对角线的距离，如果希望精度达到像素级别，行数应该与图像的对角线的距离相等
- 取直线上的第一个点(x,y)，将其带入直线在极坐标中的公式中，然后遍历θ的取值：0，1，2，...，180，分别求出对应的ρ值，如果这个数值在上述累加器中存在相应的位置，则在该位置上加1
- 取直线上的第二个点，重复上述步骤，更新累加器中的值。对图像中的直线上的每个点都直线以上步骤，每次更新累加器中的值
- 搜索累加器中的最大值，并找到其对应的(ρ,θ)，就可将图像中的直线表示出来

### 霍夫线检测
#### OpenCV中做霍夫线检测的API
```
cv.HoughLines(img, rho, theta, threshold)
```
#### 参数
- img  
检测的图像，要求是二值化的图像，所以在调用霍夫变换之前首先要进行二值化，或者进行Canny边缘检测
- rho、theta  
ρ 和θ的精确度
- threshold  
阈值，只有累加器中的值高于该阈值时才被认为是直线

#### 参考代码
```
import numpy as np
import random
import cv2 as cv
import matplotlib.pyplot as plt
# 1.加载图片，转为二值图
img = cv.imread('./image/rili.jpg')

gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
edges = cv.Canny(gray, 50, 150)

# 2.霍夫直线变换
lines = cv.HoughLines(edges, 0.8, np.pi / 180, 150)
# 3.将检测的线绘制在图像上（注意是极坐标噢）
for line in lines:
    rho, theta = line[0]
    a = np.cos(theta)
    b = np.sin(theta)
    x0 = a * rho
    y0 = b * rho
    x1 = int(x0 + 1000 * (-b))
    y1 = int(y0 + 1000 * (a))
    x2 = int(x0 - 1000 * (-b))
    y2 = int(y0 - 1000 * (a))
    cv.line(img, (x1, y1), (x2, y2), (0, 255, 0))
# 4. 图像显示
plt.figure(figsize=(10,8),dpi=100)
plt.imshow(img[:,:,::-1]),plt.title('霍夫变换线检测')
plt.xticks([]), plt.yticks([])
plt.show()
```

### 霍夫圆检测
#### 原理
圆的表示式是

$$
(x - a)^2 + (y - b)^2 = r
$$

其中a和b表示圆心坐标，r表示圆半径，因此标准的霍夫圆检测就是在这三个参数组成的三维空间累加器上进行圆形检测，此时效率就会很低，所以OpenCV中使用霍夫梯度法进行圆形的检测

##### 霍夫梯度法将霍夫圆检测范围两个阶段
###### 第一阶段检测圆心
圆心检测的原理：圆心是圆周法线的交汇处，设置一个阈值，在某点的相交的直线的条数大于这个阈值就认为该交汇点为圆心
###### 第二阶段利用圆心推导出圆半径
圆半径确定原理：圆心到圆周上的距离（半径）是相同的，确定一个阈值，只要相同距离的数量大于该阈值，就认为该距离是该圆心的半径

原则上霍夫变换可以检测任何形状，但复杂的形状需要的参数就多，霍夫空间的维数就多，因此在程序实现上所需的内存空间以及运行效率上都不利于把标准霍夫变换应用于实际复杂图形的检测中。霍夫梯度法是霍夫变换的改进，它的目的是减小霍夫空间的维度，提高效率

#### API
```
circles = cv.HoughCircles(image, method, dp, minDist, param1=100, param2=100, minRadius=0,maxRadius=0)
```
#### 参数
- image  
输入图像，应输入灰度图像
- method  
使用霍夫变换圆检测的算法，它的参数是CV_HOUGH_GRADIENT
- dp  
霍夫空间的分辨率，dp=1时表示霍夫空间与输入图像空间的大小一致，dp=2时霍夫空间是输入图像空间的一半，以此类推
- minDist  
圆心之间的最小距离，如果检测到的两个圆心之间距离小于该值，则认为它们是同一个圆心
- param1  
边缘检测时使用Canny算子的高阈值，低阈值是高阈值的一半。
- param2  
检测圆心和确定半径时所共有的阈值
- minRadius和maxRadius  
所检测到的圆半径的最小值和最大值

#### 返回
- circles  
输出圆向量，包括三个浮点型的元素一一圆心横坐标，圆心纵坐标和圆半径


#### 参考代码
```
由于霍夫圆检测对噪声比较敏感，所以首先对图像进行中值滤波
import cv2 as cv
import numpy as np
import matplotlib.pyplot as plt
# 1 读取图像，并转换为灰度图
planets = cv.imread("./image/star.jpeg")
gay_img = cv.cvtColor(planets, cv.COLOR_BGRA2GRAY)
# 2 进行中值模糊，去噪点
img = cv.medianBlur(gay_img, 7)  
# 3 霍夫圆检测
circles = cv.HoughCircles(img, cv.HOUGH_GRADIENT, 1, 200, param1=100, param2=30, minRadius=0, maxRadius=100)
# 4 将检测结果绘制在图像上
for i in circles[0, :]:  # 遍历矩阵每一行的数据
    # 绘制圆形
    cv.circle(planets, (i[0], i[1]), i[2], (0, 255, 0), 2)
    # 绘制圆心
    cv.circle(planets, (i[0], i[1]), 2, (0, 0, 255), 3)
# 5 图像显示
plt.figure(figsize=(10,8),dpi=100)
plt.imshow(planets[:,:,::-1]),plt.title('霍夫变换圆检测')
plt.xticks([]), plt.yticks([])
plt.show()
```

## 傅立叶变换
### 傅里叶变换的理解
傅里叶变换是由法国的一位数学家Joseph Fourier在18世纪提出来的，他认为：任何连续周期的信号都可以由一组适当的正弦曲线组合而成

傅里叶变换是描述信号的需要，它能够反映信号的特征，并可以使用特征值进行量化，比如正弦波可以使用幅值和频率进行描述

傅里叶变换是一种信号分析方法，它使我们能够对信号的构成和特点进行深入和定量的研究，把信号通过频谱的方式进行准确的、定量的描述

傅里叶变换是信号的分析方法，目的就是要简化问题，而不是将其变复杂，傅里叶选择了正弦波，而没有选择其他波形，是因为正弦波有任何其他波形不具有的特点

- 正弦波输入至任何线性系统中，不会产生新的频率成分，输出的仍是正弦波，改变的仅仅是幅值和相位
- 用单位幅值的不同频率的正弦波输入至某线性系统，记录其输出正弦波的幅值和频率的关系，就得到该系统的幅频特性，记录输出正弦波的相位和频率的关系，就得到该系统的相频特性
- 线性系统是自动控制研究的主要对象，我们只要研究系统对正弦波的输入输出关系，就可以知道该系统对任意输入信号的响应。这是傅里叶变换的最主要的意义

### 傅里叶变换中相关概念
#### 时域和频域
##### 时域
- 时域是真实的世界，是唯一存在的域。从我们出生开始，所接触的这个世界就是随着时间在变化的，如花开花落，四季变换，生老病死等。以时间作为参照来分析动态世界的方法我们称其为时域分析
- 比如说一段音乐，就是一个随时间变化的震动，这就是时域的表示

##### 频域
- 频域不是真实的，而是一个数学构造
- 频域是一个遵循特定规则的数学范畴，也被一些学者称为上帝视角
- 结合上面对时域的理解，如果时域是运动永不停止的，那么频域就是静止的
- 正弦波是频域中唯一存在的波形，这是频域中最重要的规则，即正弦波是对频域的描述，因为频域中的任何波形都可用正弦波合成

##### 时域和频域的关系
- 对于信号来说，信号强度随时间的变化规律就是时域特性，信号是由哪些单一频率的信号合成的就是频域特性,傅里叶变换实质就是是频域函数和时域函数的转换
- 时域是永远随着时间的变化而变化的，而频域就是装着装着正余弦波的空间
- 从时域来看，会看到一个近似为矩形的波，这个矩形的波可以拆分为一些正弦波的叠加。而从频域方向来看，就看到了每一个正余弦波的幅值，每两个正弦波之间都还有一条直线，那并不是分割线，而是振幅为 0 的正弦波！也就是说，为了组成特殊的曲线，有些正弦波成分是不需要的。随着叠加的递增，所有正弦波中上升的部分逐渐让原本缓慢增加的曲线不断变陡，而所有正弦波中下降的部分又抵消了上升到最高处时继续上升的部分使其变为水平线。一个矩形就这么叠加而成了

#### 频谱和相位谱
在傅里叶变换中描述变换后的结果有两个概念：频谱和相位谱
##### 频谱
将信号分解为若干不同频率的正弦波，那么每一个正弦波的幅度，就叫做频谱，也叫做幅度谱
##### 相位谱
频谱只代表了一个正弦函数的幅值，而要准确描述一个正弦函数，不仅需要幅值，还需要相位，不同相位决定了波的位置，所以对于频域分析，仅仅有频谱（振幅谱）是不够的，还需要一个相位谱

### 傅里叶变换
#### 傅里叶变换的分类
根据原信号的属性，可以将傅里叶变换分为以下几种
- 傅立叶变换(Fourier Transform)--非周期性连续信号
- 傅里叶级数(Foutier Series)--周期性连续信号
- 离散时域傅立叶变换(Discrete Time Fourier Transform)--非周期性离散信号
- 离散傅立叶变换(Discrete Fourier Transform)--周期性离散信号

在实际应用较多的是傅里叶变换、傅里叶级数和离散傅里叶变换
任意波形都可以通过正弦波的叠加来表示，正弦波可以通过欧拉公式写成指数的形式，欧拉公式如下：

$$
e^{it} = \cos(t) + i \sin(t)
$$


#### 傅里叶级数
任意的周期连续信号都可以使用正弦波叠加而成，这叫做傅里叶级数，写成指数形式如下

$$
f(t) = \sum c_n e^{i \frac{2\pi n t}{T}}
$$


其中c_n表示傅里叶级数

$$
c_n = \frac{1}{T} \int f(t) e^{-i \frac{2\pi n t}{T}} \, dt
$$

公式中的T表示时域信号的周期。从上式中可以看出周期信号的频谱是离散的非周期信号

#### 傅里叶变换
对于非周期的连续信号，也可以使用正弦信号来逼近，这时我们将非周期信号看做周期无限大的周期信号，则有：

$$
F(\omega) = \int f(t) e^{-i \omega t} \, dt
$$

其中，omega表示频率，t表示时间。我们叫做傅里叶变换。从中可以看出非周期信号的频谱是连续的非周期信号

##### 逆变换为

$$
f(t) = \frac{1}{2\pi} \int F(\omega) e^{i \omega t} \, d\omega
$$

利用上述公式就可将频域信号转换为时域信号

#### 离散傅里叶变换（DFT）
由于数字信号处理是希望在计算机上实现各种运算和变换，其所涉及的变量和运算都是离散的，因此对于数字信号处理，应该找到在时域和频域都是离散的傅里叶变换，即离散傅里叶变换

对于非周期的离散信号进行傅里叶变换就是离散傅里叶变换，其计算方法如下

$$
f(k) = \sum f(n) e^{-i \frac{2\pi n t}{N}}
$$

其中N表示傅里叶变换的点数，k表示傅里叶变换的频谱
##### 逆变换为

$$
f(n) = \frac{1}{N} \sum F(k) e^{i \frac{2\pi k n}{N}}
$$


### 傅里叶变换在图像中的应用
#### 图像中的傅里叶变换
图像是二维的离散信号，所以对图像要进行二维傅里叶变换。对于M*N的一幅图像的离散二维傅里叶变换，公式如下

$$
F(u,v) = \sum \sum f(x,y) e^{-i 2\pi \left(\frac{ux}{M} + \frac{vy}{N}\right)}
$$

其中u和v确定频率，f(x,y)是灰度值，该式的意义是两个求和号对图像进行遍历，f(x,y)取出原像素的数值，当固定x时，横轴不动，对y进行遍历时，vy/N表示变换前像素的位置比例与变换后的位置相乘，映射到新的位置，且能够反映像素沿y方向距离的差异，越靠后的像素(y越大)vy/N值越大，即vy/N能够反映出不同位置(纵轴)像素之间的差异；前一项含义为保留像素相对位置(横轴)的信息(遍历y时为常数)，2π为修正参数

##### 逆变换由下式给出

$$
f(x,y) = \sum \sum F(u,v) e^{i 2\pi \left(\frac{ux}{M} + \frac{vy}{N}\right)}
$$


*注意*
- *傅立叶过程是可逆的，图象经过傅立叶变换和逆傅立叶变换后，能恢复到原始图像*
- *可以在频域对图像进行处理，在频域的处理会反映在逆变换图像上*


#### 图像傅里叶变换的物理意义
- 图像的频率是表征图像中灰度变化剧烈程度的指标，是灰度在平面空间上的梯度。如：大面积的沙漠在图像中是一片灰度变化缓慢的区域，对应的频率值很低；而对于地表属性变换剧烈的边缘区域在图像中是一片灰度变化剧烈的区域，对应的频率值较高。傅里叶变换在实际中有非常明显的物理意义，从物理效果看，傅里叶变换是将图像从空间域转换到频率域，其逆变换是将图像从频率域转换到空间域
- 傅里叶变换的物理意义是将图像的灰度分布函数变换为图像的频率分布函数
- 傅里叶逆变换是将图像的频率分布函数变换为灰度分布函数。
- 我们在做DFT时是将图像的空域和频域沿x和y方向进行无限周期拓展的
- 为了便于频域的滤波和频谱的分析，常在变换后进行频谱的中心化，即对掉频谱的四个象限
- 在经过频谱居中后的频谱中，中间最亮的点是最低频率，属于直流分量，越往外，频率越高


### 在numpy中实现图像的傅里叶变换
#### 傅里叶变换
##### 第1步
###### API
```
np.fft.fft2()
```
实现傅立叶变换
###### 返回
```
complex ndarray
```
返回一个复数数组

##### 第2步
###### API
```
fft_shift = np.fft.fftshift(dft)
```
将零频率分量移到频谱中心

##### 第3步
###### API
```
res = 20 * np.log(np.abs(fft_shift))
```
功能是将结果映射到0到255区间，可以将结果显示出来

##### 参考代码
```
img = cv.imread('./image/deer.jpeg',0)
fft = np.fft.fft2(img)
f_shift = np.fft.fftshift(fft)
res1 = 20 * np.log(np.abs(f_shift))
fig, axes = plt.subplots(nrows=1,ncols=2,figsize=(20,8),dpi=100)
axes[0].imshow(img,cmap=plt.cm.gray)
axes[1].imshow(res1,cmap=plt.cm.gray)
plt.show()
```

#### 逆傅里叶变换
##### 第1步
###### API
```
iff_shift = np.fft.ifftshift(fft_shift)
```
fftshift的逆函数，将零频率分量从频谱中心移回原来位置

##### 第2步
###### API
```
ifft = np.fft.ifft2(iff_shift)
```
实现逆傅立叶变换
###### 返回
```
complex ndarray
```
返回一个复数数组

##### 第3步
###### API
```
res = np.abs(ifft)
```
##### 参考代码
```
ifft_shift = np.fft.ifftshift(f_shift)
ifft = np.fft.ifft2(ifft_shift)
res2 = np.abs(ifft)
fig, axes = plt.subplots(nrows=1,ncols=2,figsize=(20,8),dpi=100)
axes[0].imshow(img,cmap=plt.cm.gray)
axes[1].imshow(res2,cmap=plt.cm.gray)
plt.show()
```


### 在OpenCV中实现图像的傅里叶变换
#### 傅里叶变换
##### 第1步
###### API
```
dft = cv2.dft(src, dst=None,flags)
```
实现傅立叶变换
###### 参数
- src  
输入图像，要转换成 ```np.float32``` 格式
- dst  
参数是可选的, 决定输出数组的大小。默认输出数组的大小和输入图像大小一样。如果输出结果比输入图像大，输入图像就需要在进行变换前补 0。如果输出结果比输入图像小的话，输入图像就会被切割
- flags  
转换标识，一般设为 ```cv.DFT_COMPLEX_OUTPUT```，输出一个复数阵列
###### 返回
- dft
傅里叶变换后的结果，有两个通道，第一个通道是结果的实数部分，第二个通道是结果的虚数部分。我们需要在此基础上计算傅里叶变换的频谱和相位

##### 第2步
###### API
```
numpy.fft.fftshift(dft)
```
将零频率分量移到频谱中心

##### 第3步
###### API
```
cv2.magnitude(x,y)
```
计算幅值
###### 参数
- x  
浮点型X坐标值，即实部
- y  
浮点型Y坐标值，即虚部

##### 参考代码
```
img = cv.imread('./image/deer.jpeg',0)
dft = cv.dft(np.float32(img),flags=cv.DFT_COMPLEX_OUTPUT)
fft_shift = np.fft.fftshift(dft)
res = 20 * np.log(cv.magnitude(fft_shift[:,:,0], fft_shift[:,:,1]))
plt.imshow(res, cmap=plt.cm.gray)
```
#### 逆傅里叶变换
##### 第1步
###### API
```
np.fft.ifftshift()
```
fftshift的逆函数，将零频率分量从频谱中心移回原来位置

##### 第2步
###### API
```
img = cv.idft(dft)
```
实现逆傅立叶变换
###### 参数
- dft  
图像的频域表示，实数或复数都可以
###### 返回
- img  
图像的空域表示，取决于原始数据的类型和大小

##### 第3步
###### API
```
cv2.magnitude(x,y)
```
计算幅值
###### 参数
- x  
浮点型X坐标值，即实部
- y  
浮点型Y坐标值，即虚部

##### 参考代码
```
ifft_shift = np.fft.ifftshift(fft_shift)
idft = cv.idft(ifft_shift)
res = cv.magnitude(idft[:,:,0],idft[:,:,1])
fig,axes = plt.subplots(nrows=1,ncols=2,figsize=(20,8),dpi=100)
axes[0].imshow(img, cmap=plt.cm.gray)
axes[1].imshow(res,cmap=plt.cm.gray)
plt.show()
```

### 频域滤波
图像变换到频域后，就可以进行频域滤波，主要包括：高通滤波，低通滤波，带通滤波和带阻滤波
#### 相关概念
##### 低频
低频对应图像内变化缓慢的灰度分量。例如，在一幅大草原的图像中，低频对应着广袤的颜色趋于一致的草原
##### 高频
高频对应图像内变化越来越快的灰度分量，是由灰度的尖锐过渡造成的。例如，在一幅大草原的图像中，高频对应着狮子的边缘等信息
##### 滤波
- 接受（通过）或者拒绝一定频率的分量
- 通过低频的滤波器称为低通滤波器
- 通过高频的滤波器称为高通滤波器

##### 频域滤波
- 修改傅立叶变换以达到特殊目的，然后计算IDFT返回到图像域
- 特殊目的包括：图像增强、图像去噪、边缘检测、特征提取、压缩、加密等

#### 高通滤波器
##### 概念
- 图像在经过傅里叶变换后，经频谱中心化后，从中间到外面，频率上依次是从低频到高频的。如果把中间规定一小部分去掉，就相对于把低频信号去掉了，这也就是进行了高通滤波
- 高通滤波器衰减低频而通过高频，将增强尖锐的细节，但是会导致图像对比度降低

##### 参考代码
```
img = cv.imread('./image/deer.jpeg',0)

fft = np.fft.fft2(img)
fft_shift = np.fft.fftshift(fft)

rows,cols = img.shape
crow,ccol = int(rows/2),int(cols/2)
fft_shift[crow-100:crow+100,ccol-100:ccol+100] = 0

mask = (np.abs(fft_shift))

ifft_shift = np.fft.ifftshift(fft_shift)
ifft = np.fft.ifft2(ifft_shift)
res3 = np.abs(ifft)

fig,axes = plt.subplots(nrows=1,ncols=3, figsize=(20,8),dpi=100)
axes[0].imshow(img,cmap=plt.cm.gray)
axes[1].imshow(mask,cmap=plt.cm.gray)
axes[2].imshow(res3,cmap=plt.cm.gray)
plt.show()
```

#### 低通滤波器
##### 概念
低通滤波器衰减高频而通过低频，将模糊图像
##### 参考代码
```
img = cv.imread('./image/deer.jpeg',0)

dft = cv.dft(np.float32(img), flags=cv.DFT_COMPLEX_OUTPUT)
fft_shift = np.fft.fftshift(dft)

rows,cols = img.shape
mask = np.zeros((rows,cols,2), np.uint8)
crow,ccol = int(rows/2),int(cols/2)
mask[ccol-100:ccol+100,crow-100:crow+100] = 1
re_fft_shift = fft_shift * mask

ifft_shift = np.fft.ifftshift(re_fft_shift)
idft = cv.idft(ifft_shift)
res6 = cv.magnitude(idft[:,:,0],idft[:,:,1])

fig,axes = plt.subplots(nrows=1,ncols=2,figsize=(20,8),dpi=100)
axes[0].imshow(img, cmap=plt.cm.gray)
axes[1].imshow(res6,cmap=plt.cm.gray)
plt.show()
```

#### 带通滤波器
- 把高通和低通的一部分结合在模板中就形成了带通滤波器，它容许一定频率范围信号通过, 但减弱(或减少)频率低于於下限截止频率和高于上限截止频率的信号的通过
- 带通的效果，它既能保留一部分低频，也能保留一部分高频。根据需求选择保留多少
#### 带阻滤波器
- 带阻滤波器减弱(或减少)一定频率范围信号, 但容许频率低于於下限截止频率和高于上限截止频率的信号的通过
- 带阻滤波器保持了原图像的大部分信息，图像的主要信息都集中在低频上，而边缘轮廓信息都在高频位置。带阻滤波器滤除了中频信息，保留了低频和高频信息，所以对图像的信息破坏是比较小的


# 图像特征提取与描述
## 角点特征
### 图像的特征
- 在拼图游戏。首先拿到完整图像的碎片，然后把这些碎片以正确的方式排列起来从而重建这幅图像。如果把拼图游戏的原理写成计算机程序，那计算机就也会玩拼图游戏了
- 在拼图时，我们要寻找一些唯一的特征，这些特征要适于被跟踪，容易被比较。我们在一副图像中搜索这样的特征，找到它们，而且也能在其他图像中找到这些特征，然后再把它们拼接到一起
- 我们希望这些特征也能被计算机理解
- 图像特征要有区分性，容易被比较。一般认为角点，斑点等是较好的图像特征
#### 特征检测
找到图像中的特征
#### 特征描述
对特征及其周围的区域进行描述

### 角点的作用
- 角点是图像很重要的特征,对图像图形的理解和分析有很重要的作用
- 角点在三维场景重建运动估计，目标跟踪、目标识别、图像配准与匹配等计算机视觉领域起着非常重要的作用
- 在现实世界中，角点对应于物体的拐角，道路的十字路口、丁字路口等


## Harris算法和Shi-Tomas算法
### Harris角点检测
#### 原理
Harris角点检测的思想是通过图像的局部的小窗口观察图像，角点的特征是窗口沿任意方向移动都会导致图像灰度的明显变化
- 平坦区域  
任意方向移动，无灰度变化
- 边缘  
沿着边缘方向移动，无灰度变化
- 角点  
沿任意方向移动，明显灰度变化

将上述思想转换为数学形式，即将局部窗口向各个方向移动(u,v)并计算所有灰度差异的总和，表达式如下:

$$
E(u,v) = \sum w(x,y) \left[ I(x+u, y+v) - I(x,y) \right]^2
$$

其中I(x,y)是局部窗口的图像灰度，I(x+u,y+v)是平移后的图像灰度，w(x,y)是窗口函数，可以是矩形窗口，也可以是对每一个像素赋予不同权重的高斯窗口

角点检测中使E(u,v)的值最大。利用一阶泰勒展开有：

$$
I(x+u, y+v) = I(x,y) + I_x \cdot u + I_y \cdot v
$$

其中I_x和I_y是沿x和y方向的导数，可用sobel算子计算

M矩阵决定了E(u,v)的取值，下面我们利用M来求角点，M是I_x和I_y的二次项函数，可以表示成椭圆的形状，椭圆的长短半轴由M的特征值λ_1和λ_2决定，方向由特征矢量决定

- 共分为三种情况

  - 图像中的直线  
一个特征值大，另一个特征值小，λ_1>>λ_2或 λ_2>>λ_1。椭圆函数值在某一方向上大，在其他方向上小
  - 图像中的平面  
两个特征值都小，且近似相等；椭圆函数数值在各个方向上都小
  - 图像中的角点  
两个特征值都大，且近似相等，椭圆函数在所有方向都增大

Harris给出的角点计算方法并不需要计算具体的特征值，而是计算一个角点响应值R来判断角点。R的计算公式为：

$$
R = \det(M) - \alpha (\text{trace}(M))^2
$$

式中，detM为矩阵M的行列式；traceM为矩阵M的迹；α为常数，取值范围为0.04~0.06。事实上，特征是隐含在detM和traceM中，因为detM=λ_1 * λ_2, traceM=λ_1 + λ_2

##### 如何判断角点
- 当R为大数值的正数时是角点
- 当R为大数值的负数时是边界
- 当R为小数是认为是平坦区域


#### OpenCV实现
##### API
```
dst=cv.cornerHarris(src, blockSize, ksize, k)
```
##### 参数
- img  
数据类型为 ﬂoat32 的输入图像
- blockSize  
角点检测中要考虑的邻域大小
- ksize  
sobel求导使用的核大小
- k  
角点检测方程中的自由参数，取值参数为 [0.04，0.06]

#### 参考代码
```
import cv2 as cv
import numpy as np 
import matplotlib.pyplot as plt
# 1 读取图像，并转换成灰度图像
img = cv.imread('./image/chessboard.jpg')
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
# 2 角点检测
# 2.1 输入图像必须是 float32
gray = np.float32(gray)

# 2.2 最后一个参数在 0.04 到 0.05 之间
dst = cv.cornerHarris(gray,2,3,0.04)
# 3 设置阈值，将角点绘制出来，阈值根据图像进行选择
img[dst>0.001*dst.max()] = [0,0,255]
# 4 图像显示
plt.figure(figsize=(10,8),dpi=100)
plt.imshow(img[:,:,::-1]),plt.title('Harris角点检测')
plt.xticks([]), plt.yticks([])
plt.show()
```
#### Harris角点检测的优缺点
##### 优点
- 旋转不变性，椭圆转过一定角度但是其形状保持不变（特征值保持不变）
- 对于图像灰度的仿射变化具有部分的不变性，由于仅仅使用了图像的一介导数，对于图像灰度平移变化不变；对于图像灰度尺度变化不变
##### 缺点
- 对尺度很敏感，不具备几何尺度不变性
- 提取的角点是像素级的


### Shi-Tomasi角点检测
#### 原理
Shi-Tomasi算法是对Harris角点检测算法的改进，一般会比Harris算法得到更好的角点。Harris 算法的角点响应函数是将矩阵 M 的行列式值与 M 的迹相减，利用差值判断是否为角点。后来Shi 和Tomasi 提出改进的方法是，若矩阵M的两个特征值中较小的一个大于阈值，则认为他是角点，即：

$$
R = \min(\lambda_1, \lambda_2)
$$

只有当 λ1 和 λ 2 都大于最小值时，才被认为是角点


#### OpenCV实现
##### API
```
corners = cv2.goodFeaturesToTrack ( image, maxcorners, qualityLevel, minDistance )
```
##### 参数
- Image
输入灰度图像
- maxCorners
获取角点数的数目
- qualityLevel
该参数指出最低可接受的角点质量水平，在0-1之间
- minDistance
角点之间最小的欧式距离，避免得到相邻特征点
##### 返回
- corners  
搜索到的角点，在这里所有低于质量水平的角点被排除掉，然后把合格的角点按质量排序，然后将质量较好的角点附近（小于最小欧式距离）的角点删掉，最后找到maxCorners个角点返回

#### 参考代码
```
import numpy as np 
import cv2 as cv
import matplotlib.pyplot as plt
# 1 读取图像
img = cv.imread('./image/tv.jpg') 
gray = cv.cvtColor(img,cv.COLOR_BGR2GRAY)
# 2 角点检测
corners = cv.goodFeaturesToTrack(gray,1000,0.01,10)  
# 3 绘制角点
for i in corners:
    x,y = i.ravel()
    cv.circle(img,(x,y),2,(0,0,255),-1)
# 4 图像展示
plt.figure(figsize=(10,8),dpi=100)
plt.imshow(img[:,:,::-1]),plt.title('shi-tomasi角点检测')
plt.xticks([]), plt.yticks([])
plt.show()
```

## SIFT/SURF算法
### SIFT原理
- Harris和Shi-Tomasi角点检测算法具有旋转不变性，但不具有尺度不变性，在小图中可以检测到角点，但是图像被放大后，再使用同样的窗口，就检测不到角点了
- 尺度不变特征转换即SIFT (Scale-invariant feature transform)，是一种计算机视觉的算法。它用来侦测与描述影像中的局部性特征，它在空间尺度中寻找极值点，并提取出其位置、尺度、旋转不变量，此算法由 David Lowe在1999年所发表，2004年完善总结。应用范围包含物体辨识、机器人地图感知与导航、影像缝合、3D模型建立、手势辨识、影像追踪和动作比对等领域
- SIFT算法的实质是在不同的尺度空间上查找关键点(特征点)，并计算出关键点的方向。SIFT所查找到的关键点是一些十分突出，不会因光照，仿射变换和噪音等因素而变化的点，如角点、边缘点、暗区的亮点及亮区的暗点等
### 基本流程
Lowe将SIFT算法分解为如下四步：
- 尺度空间极值检测  
搜索所有尺度上的图像位置。通过高斯差分函数来识别潜在的对于尺度和旋转不变的关键点
- 关键点定位  
在每个候选的位置上，通过一个拟合精细的模型来确定位置和尺度。关键点的选择依据于它们的稳定程度
- 关键点方向确定  
基于图像局部的梯度方向，分配给每个关键点位置一个或多个方向。所有后面的对图像数据的操作都相对于关键点的方向、尺度和位置进行变换，从而保证了对于这些变换的不变性
- 关键点描述  
在每个关键点周围的邻域内，在选定的尺度上测量图像局部的梯度。这些梯度作为关键点的描述符，它允许比较大的局部形状的变形或光照变化

### 尺度空间极值检测
在不同的尺度空间是不能使用相同的窗口检测极值点，对小的关键点使用小的窗口，对大的关键点使用大的窗口，为了达到上述目的，我们使用尺度空间滤波器

高斯核是唯一可以产生多尺度空间的核函数

一个图像的尺度空间L(x,y,σ)，定义为原始图像I(x,y)与一个可变尺度的2维高斯函数G(x,y,σ)卷积运算 ，即：

$$
L(x,y,\sigma) = G(x,y,\sigma) * I(x,y)
$$

其中

$$
G(x,y,\sigma) = \frac{1}{2\pi\sigma^2} e^{-\frac{x^2 + y^2}{2\sigma^2}}
$$


σ是尺度空间因子，它决定了图像的模糊的程度。在大尺度下（σ值大）表现的是图像的概貌信息，在小尺度下（σ值小）表现的是图像的细节信息

在计算高斯函数的离散近似时，在大概3σ距离之外的像素都可以看作不起作用，这些像素的计算也就可以忽略。所以，在实际应用中，只计算(6σ+1)*(6σ+1)的高斯卷积核就可以保证相关像素影响

#### 高斯金字塔
高斯金字塔采用高斯函数对图像进行模糊以及降采样处理得到的

高斯金字塔构建过程中，首先将图像扩大一倍，在扩大的图像的基础之上构建高斯金字塔，然后对该尺寸下图像进行高斯模糊，几幅模糊之后的图像集合构成了一个Octave

然后对该Octave下选择一幅图像进行下采样，长和宽分别缩短一倍，图像面积变为原来四分之一。这幅图像就是下一个Octave的初始图像

在初始图像的基础上完成属于这个Octave的高斯模糊处理，以此类推完成整个算法所需要的所有八度构建，这样这个高斯金字塔就构建出来了

#### 高斯差分金字塔
利用LoG(高斯拉普拉斯方法)，即图像的二阶导数，可以在不同的尺度下检测图像的关键点信息，从而确定图像的特征点。但LoG的计算量大，效率低。所以我们通过两个相邻高斯尺度空间的图像的相减，得到DoG(高斯差分)来近似LoG

为了计算DoG我们构建高斯差分金字塔，该金字塔是在上述的高斯金字塔的基础上构建而成的，建立过程是：在高斯金字塔中每个Octave中相邻两层相减就构成了高斯差分金字塔

高斯差分金字塔的第1组第1层是由高斯金字塔的第1组第2层减第1组第1层得到的。以此类推，逐组逐层生成每一个差分图像，所有差分图像构成差分金字塔。概括为DOG金字塔的第o组第l层图像是有高斯金字塔的第o组第l+1层减第o组第l层得到的。后续Sift特征点的提取都是在DOG金字塔上进行的

在 DoG 搞定之后，就可以在不同的尺度空间中搜索局部最大值了。对于图像中的一个像素点而言，它需要与自己周围的 8 邻域，以及尺度空间中上下两层中的相邻的 18（2x9）个点相比。如果是局部最大值，它就可能是一个关键点。基本上来说关键点是图像在相应尺度空间中的最好代表

搜索过程从每组的第二层开始，以第二层为当前层，对第二层的DoG图像中的每个点取一个3×3的立方体，立方体上下层为第一层与第三层。这样，搜索得到的极值点既有位置坐标（DoG的图像坐标），又有空间尺度坐标（层坐标）。当第二层搜索完成后，再以第三层作为当前层，其过程与第二层的搜索类似。当S=3时，每组里面要搜索3层，所以在DOG中就有S+2层，在初使构建的金字塔中每组有S+3层


### 关键点定位
由于DoG对噪声和边缘比较敏感，因此在上面高斯差分金字塔中检测到的局部极值点需经过进一步的检验才能精确定位为特征点

使用尺度空间的泰勒级数展开来获得极值的准确位置， 如果极值点的 灰度值小于阈值（一般为0.03或0.04）就会被忽略掉。 在 OpenCV 中这种阈值被称为 contrastThreshold

DoG 算法对边界非常敏感，所以我们必须要把边界去除。 Harris 算法除了可以用于角点检测之外还可以用于检测边界。从 Harris 角点检测的算法中，当一个特征值远远大于另外一个特征值时检测到的是边界。那在DoG算法中欠佳的关键点在平行边缘的方向有较大的主曲率，而在垂直于边缘的方向有较小的曲率，两者的比值如果高于某个阈值（在OpenCV中叫做边界阈值），就认为该关键点为边界，将被忽略，一般将该阈值设置为10

将低对比度和边界的关键点去除，得到的就是我们感兴趣的关键点

### 关键点方向确定
经过上述两个步骤，图像的关键点就完全找到了，这些关键点具有尺度不变性。为了实现旋转不变性，还需要为每个关键点分配一个方向角度，也就是根据检测到的关键点所在高斯尺度图像的邻域结构中求得一个方向基准

 对于任一关键点，我们采集其所在高斯金字塔图像以r为半径的区域内所有像素的梯度特征（幅值和幅角），
半径r为：

$$
r = 3 \times 1.5\sigma
$$

其中σ是关键点所在octave的图像的尺度，可以得到对应的尺度图像
##### 梯度的幅值和方向的计算公式

$$
m(x,y) = \sqrt{(L(x+1,y) - L(x-1,y))^2 + (L(x,y+1) - L(x,y-1))^2}
$$


$$
\theta(x,y) = \arctan\left(\frac{L(x,y+1) - L(x,y-1)}{L(x+1,y) - L(x-1,y)}\right)
$$


完成关键点梯度计算后，使用直方图统计关键点邻域内像素的梯度幅值和方向
具体做法是：
- 将360°分为36柱，每10°为一柱
- 然后在以r为半径的区域内，将梯度方向在某一个柱内的像素找出来
- 然后将他们的幅值相加在一起作为柱的高度
- 因为在r为半径的区域内像素的梯度幅值对中心像素的贡献是不同的，因此还需要对幅值进行加权处理，采用高斯加权，方差为1.5σ

每个特征点必须分配一个主方向，还需要一个或多个辅方向，增加辅方向的目的是为了增强图像匹配的鲁棒性。辅方向的定义是，当一个柱体的高度大于主方向柱体高度的80%时，则该柱体所代表的的方向就是给特征点的辅方向

直方图的峰值，即最高的柱代表的方向是特征点邻域范围内图像梯度的主方向，但该柱体代表的角度是一个范围，所以我们还要对离散的直方图进行插值拟合，以得到更精确的方向角度值。利用抛物线对离散的直方图进行拟合

获得图像关键点主方向后，每个关键点有三个信息(x,y,σ,θ)：位置、尺度、方向。由此我们可以确定一个SIFT特征区域。通常使用一个带箭头的圆或直接使用箭头表示SIFT区域的三个值
- 中心表示特征点位置
- 半径表示关键点尺度
- 箭头表示方向

### 关键点描述
通过以上步骤，每个关键点就被分配了位置，尺度和方向信息。接下来我们为每个关键点建立一个描述符，该描述符既具有可区分性，又具有对某些变量的不变性，如光照，视角等。而且描述符不仅仅包含关键点，也包括关键点周围对其有贡献的的像素点。主要思路就是通过将关键点周围图像区域分块，计算块内的梯度直方图，生成具有特征向量，对图像信息进行抽象

描述符与特征点所在的尺度有关，所以我们在关键点所在的高斯尺度图像上生成对应的描述符。以特征点为中心，将其附近邻域划分为d∗d个子区域（一般取d=4），每个子区域都是一个正方形，边长为3σ，考虑到实际计算时，需进行三次线性插值，所以特征点邻域的为

$$
(3\sigma (d+1)) \times (3\sigma (d+1))
$$

的范围

为了保证特征点的旋转不变性，以特征点为中心，将坐标轴旋转为关键点的主方向

计算子区域内的像素的梯度，并按照σ=0.5d进行高斯加权，然后插值计算得到每个种子点的八个方向的梯度

每个种子点的梯度都是由覆盖其的4个子区域插值而得的。如图中的红色点，落在第0行和第1行之间，对这两行都有贡献。对第0行第3列种子点的贡献因子为dr，对第1行第3列的贡献因子为1-dr，同理，对邻近两列的贡献因子为dc和1-dc，对邻近两个方向的贡献因子为do和1-do。则最终累加在每个方向上的梯度大小为：

$$
\text{weight} = w \cdot dr^k (1 - dr)^{(1 - k)} \cdot dc^m (1 - dc)^{(1 - m)} \cdot do^n (1 - do)^{(1 - n)}
$$

其中k，m，n为0或为1。如上统计4∗4∗8=128个梯度信息即为该关键点的特征向量，按照特征点的对每个关键点的特征向量进行排序，就得到了SIFT特征描述向量

SIFT在图像的不变特征提取方面拥有无与伦比的优势，但并不完美，仍然存在实时性不高，有时特征点较少，对边缘光滑的目标无法准确提取特征点等缺陷，自SIFT算法问世以来，人们就一直对其进行优化和改进，其中最著名的就是SURF算法


### SURF原理
使用 SIFT 算法进行关键点检测和描述的执行速度比较慢， 需要速度更快的算法。 2006 年 Bay提出了 SURF 算法，是SIFT算法的增强版，它的计算量小，运算速度快，提取的特征与SIFT几乎相同
#### SIFT算法和SURF算法对比
##### SIFT算法
- 特征点检测
使用不同尺度的图片与高斯函数进行卷积
- 方向
关键点邻接矩形区域内，利用梯度直方图计算
- 描述符生成
关键点邻域内划分d*d子区域，每个子区域内计算8个方向的直方图
##### SURF算法
- 特征点检测
使用不同大小的盒滤波器与原始图像做卷积，易于并行
- 方向
关键点邻接圆域内，计算x,y方向的haar小波
- 描述符生成
关键点邻域内划分d*d个子区域，每个子区域计算采样点的haar小波相应，记录:


$$
\sum dx, \quad \sum dy, \quad \sum |dx|, \quad \sum |dy|
$$


### OpenCV实现
#### 实例化sift
##### API
```
sift = cv.xfeatures2d.SIFT_create()
```
#### 利用 ```sift.detectAndCompute()``` 检测关键点并计算
##### API
```
kp,des = sift.detectAndCompute(gray,None)
```
##### 参数
- gray  
进行关键点检测的图像，注意是灰度图像
##### 返回
- kp  
关键点信息，包括位置，尺度，方向信息
- des  
关键点描述符，每个关键点对应128个梯度信息的特征向量

#### 将关键点检测结果绘制在图像上
##### API
```
cv.drawKeypoints(image, keypoints, outputimage, color, flags)
```
##### 参数
- image  
原始图像
- keypoints  
关键点信息，将其绘制在图像上
- outputimage  
输出图片，可以是原始图像
- color  
颜色设置，通过修改（b,g,r）的值,更改画笔的颜色，b=蓝色，g=绿色，r=红色
- flags  
绘图功能的标识设置
  - ```cv2.DRAW_MATCHES_FLAGS_DEFAULT```：创建输出图像矩阵，使用现存的输出图像绘制匹配对和特征点，对每一个关键点只绘制中间点

  - ```cv2.DRAW_MATCHES_FLAGS_DRAW_OVER_OUTIMG```：不创建输出图像矩阵，而是在输出图像上绘制匹配对

  - ```cv2.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS```：对每一个特征点绘制带大小和方向的关键点图形

  - ```cv2.DRAW_MATCHES_FLAGS_NOT_DRAW_SINGLE_POINTS```：单点的特征点不被绘制

#### SURF算法的应用与上述流程是一致

#### 参考代码
```
利用SIFT算法在中央电视台的图片上检测关键点，并将其绘制出来：
import cv2 as cv 
import numpy as np
import matplotlib.pyplot as plt
# 1 读取图像
img = cv.imread('./image/tv.jpg')
gray= cv.cvtColor(img,cv.COLOR_BGR2GRAY)
# 2 sift关键点检测
# 2.1 实例化sift对象
sift = cv.xfeatures2d.SIFT_create()

# 2.2 关键点检测：kp关键点信息包括方向，尺度，位置信息，des是关键点的描述符
kp,des=sift.detectAndCompute(gray,None)
# 2.3 在图像上绘制关键点的检测结果
cv.drawKeypoints(img,kp,img,flags=cv.DRAW_MATCHES_FLAGS_DRAW_RICH_KEYPOINTS)
# 3 图像显示
plt.figure(figsize=(8,6),dpi=100)
plt.imshow(img[:,:,::-1]),plt.title('sift检测')
plt.xticks([]), plt.yticks([])
plt.show()
```

## Fast算法
### 原理
SIFT和SURF算法效果都很好，但是从实时处理的角度来看，效率还是太低了。为了解决这个问题，Edward Rosten和Tom Drummond在2006年提出了FAST算法，并在2010年对其进行了修正

FAST (全称Features from accelerated segment test)是一种用于角点检测的算法，该算法的原理是取图像中检测点，以该点为圆心的周围邻域内像素点判断检测点是否为角点

通俗的讲就是若一个像素周围有一定数量的像素与该点像素值不同，则认为其为角点

### FAST算法的基本流程
- 在图像中选取一个像素点 p，来判断它是不是关键点。I_p等于像素点 p的灰度值
- 以r为半径画圆，覆盖p点周围的M个像素，通常情狂下，设置 r=3，则 M=16
- 设置一个阈值t，如果在这 16 个像素点中存在 n 个连续像素点的灰度值都高于I_p + t，或者低于I_p - t，那么像素点 p 就被认为是一个角点。n 一般取值为 12
- 由于在检测特征点时是需要对图像中所有的像素点进行检测，然而图像中的绝大多数点都不是特征点，如果对每个像素点都进行上述的检测过程，那显然会浪费许多时间，因此采用一种进行非特征点判别的方法：
  - 首先对候选点的周围每个 90 度的点：1，9，5，13 进行测试（先测试 1 和 19, 如果它们符合阈值要求再测试 5 和 13）
  - 如果 p 是角点，那么这四个点中至少有 3 个要符合阈值要求，否则直接剔除
  - 对保留下来的点再继续进行测试（是否有 12 的点符合阈值要求）

#### 虽然这个检测器的效率很高，但它有以下几条缺点：
- 获得的候选点比较多
- 特征点的选取不是最优的，因为它的效果取决与要解决的问题和角点的分布情况。
- 进行非特征点判别时大量的点被丢弃
- 检测到的很多特征点都是相邻的

前 3 个问题可以通过机器学习的方法解决，最后一个问题可以使用非最大值抑制的方法解决

#### 机器学习的角点检测器
- 选择一组训练图片（最好是跟最后应用相关的图片）
- 使用 FAST 算法找出每幅图像的特征点，对图像中的每一个特征点，将其周围的 16 个像素存储构成一个向量P
- 每一个特征点的 16 像素点都属于下列三类中的一种


$$
S_{(p \to x)} =
\begin{cases} 
d, & I_{(p \to x)} \leq I_p - t \quad (\text{darker}) \\
s, & I_p - t < I_{(p \to x)} < I_p + t \quad (\text{similar}) \\
b, & I_{(p \to x)} \geq I_p + t \quad (\text{brighter})
\end{cases}
$$



- 根据这些像素点的分类，特征向量 P 也被分为 3 个子集：Pd ，Ps ，Pb
- 定义一个新的布尔变量K_p，如果 p 是角点就设置为 Ture，如果不是就设置为 False
- 利用特征值向量p，目标值是K_p，训练ID3 树（决策树分类器）
- 将构建好的决策树运用于其他图像的快速的检测

#### 非极大值抑制
- 在筛选出来的候选角点中有很多是紧挨在一起的，需要通过非极大值抑制来消除这种影响
- 为所有的候选角点都确定一个打分函数V，V的值可这样计算：先分别计算I_p与圆上16个点的像素值差值，取绝对值，再将这16个绝对值相加，就得到了V的值


$$
V = \sum |I_p - I_i|
$$


- 最后比较毗邻候选角点的 V 值，把V值较小的候选角点筛除掉


FAST算法的思想与我们对角点的直观认识非常接近，化繁为简。FAST算法比其它角点的检测算法快，但是在噪声较高时不够稳定，这需要设置合适的阈值

### OpenCV实现FAST检测算法
OpenCV中的FAST检测算法是用传统方法实现的
#### 实例化fast
##### API
```
fast = =cv.FastFeatureDetector_create(threshold, nonmaxSuppression)
```
##### 参数
- threshold  
阈值t，有默认值10
- nonmaxSuppression  
是否进行非极大值抑制，默认值True
##### 返回
- Fast  
创建的FastFeatureDetector对象

#### 利用fast.detect检测关键点，没有对应的关键点描述
##### API
```
kp = fast.detect(grayImg, None)
```
##### 参数
- gray  
进行关键点检测的图像，注意是灰度图像
##### 返回
- kp  
关键点信息，包括位置，尺度，方向信息

#### 将关键点检测结果绘制在图像上，与在sift中是一样的
##### API
```
cv.drawKeypoints(image, keypoints, outputimage, color, flags)
```

#### 参考代码
```
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt
# 1 读取图像
img = cv.imread('./image/tv.jpg')
# 2 Fast角点检测
# 2.1 创建一个Fast对象，传入阈值，注意：可以处理彩色空间图像
fast = cv.FastFeatureDetector_create(threshold=30)

# 2.2 检测图像上的关键点
kp = fast.detect(img,None)
# 2.3 在图像上绘制关键点
img2 = cv.drawKeypoints(img, kp, None, color=(0,0,255))

# 2.4 输出默认参数
print( "Threshold: {}".format(fast.getThreshold()) )
print( "nonmaxSuppression:{}".format(fast.getNonmaxSuppression()) )
print( "neighborhood: {}".format(fast.getType()) )
print( "Total Keypoints with nonmaxSuppression: {}".format(len(kp)) )


# 2.5 关闭非极大值抑制
fast.setNonmaxSuppression(0)
kp = fast.detect(img,None)

print( "Total Keypoints without nonmaxSuppression: {}".format(len(kp)) )
# 2.6 绘制为进行非极大值抑制的结果
img3 = cv.drawKeypoints(img, kp, None, color=(0,0,255))

# 3 绘制图像
fig,axes=plt.subplots(nrows=1,ncols=2,figsize=(10,8),dpi=100)
axes[0].imshow(img2[:,:,::-1])
axes[0].set_title("加入非极大值抑制")
axes[1].imshow(img3[:,:,::-1])
axes[1].set_title("未加入非极大值抑制")
plt.show()
```

## ORB算法
### ORB算法原理
SIFT和SURF算法是受专利保护的，在使用时我们是要付费的，但是ORB（Oriented Fast and Rotated Brief）不需要，它可以用来对图像中的关键点快速创建特征向量，并用这些特征向量来识别图像中的对象

ORB算法结合了Fast和Brief算法，提出了构造金字塔，为Fast特征点添加了方向，从而使得关键点具有了尺度不变性和旋转不变性

### ORB算法流程
- 构造尺度金字塔，金字塔共有n层，与SIFT不同的是，每一层仅有一幅图像。第s层的尺度为：


$$
\sigma_s = (\sigma_0)^s
$$


其中，σ_0是初始尺度，默认为1.2，原图在第0层
- 第s层图像的大小：


$$
\text{SIZE} = \left(H \cdot \frac{1}{\sigma_s}\right) \times \left(W \cdot \frac{1}{\sigma_s}\right)
$$


在不同的尺度上利用Fast算法检测特征点，采用Harris角点响应函数，根据角点的响应值排序，选取前N个特征点，作为本尺度的特征点

计算特征点的主方向，计算以特征点为圆心半径为r的圆形邻域内的灰度质心位置，将从特征点位置到质心位置的方向做特征点的主方向

计算方法如下：

$$
m_{pq} = \sum_{x,y} (x^p \cdot y^q \cdot I(x,y))
$$

质心位置：

$$
C = \left( \frac{m_{10}}{m_{00}}, \frac{m_{01}}{m_{00}} \right)
$$

主方向：

$$
\theta = \arctan\left(\frac{m_{01}}{m_{10}}\right)
$$

为了解决旋转不变性，将特征点的邻域旋转到主方向上利用Brief算法构建特征描述符，至此就得到了ORB的特征描述向量

### BRIEF算法
#### BRIEF算法原理
BRIEF是一种特征描述子提取算法，并非特征点的提取算法，一种生成二值化描述子的算法，不提取代价低，匹配只需要使用简单的汉明距离(Hamming Distance)利用比特之间的异或操作就可以完成

因此，时间代价低，空间代价低，效果还挺好是最大的优点

#### BRIEF算法步骤
##### 图像滤波
原始图像中存在噪声时，会对结果产生影响，所以需要对图像进行滤波，去除部分噪声
##### 选取点对
以特征点为中心，取S*S的邻域窗口，在窗口内随机选取N组点对，一般N=128,256,512，默认是256，关于如何选取随机点对，提供了五种形式，结果如下所示：
- x,y方向平均分布采样
- x,y均服从Gauss(0,S^2/25)各向同性采样
- x服从Gauss(0,S^2/25)，y服从Gauss(0,S^2/100)采样
- x,y从网格中随机获取
- x一直在(0,0)，y从网格中随机选取 
##### 构建描述符
- 假设x,y是某个点对的两个端点，p(x),p(y)是两点对应的像素值，则有：


$$
t(x,y) =
\begin{cases} 
1, & \text{if } p(x) > p(y) \\
0, & \text{otherwise}
\end{cases}
$$


- 对每一个点对都进行上述的二进制赋值，形成BRIEF的关键点的描述特征向量，该向量一般为 128-512 位的字符串，其中仅包含 1 和 0

### 实现
在OPenCV中实现ORB算法
#### 实例化ORB
##### API
```
orb = cv.xfeatures2d.orb_create(nfeatures)
```
##### 参数
- nfeatures  
特征点的最大数量

#### 利用 ```orb.detectAndCompute()``` 检测关键点并计算
##### API
```
kp,des = orb.detectAndCompute(gray,None)
```
##### 参数
- gray  
进行关键点检测的图像，注意是灰度图像
##### 返回
- kp  
关键点信息，包括位置，尺度，方向信息
- des  
关键点描述符，每个关键点BRIEF特征向量，二进制字符串
#### 将关键点检测结果绘制在图像上
- API
```
cv.drawKeypoints(image, keypoints, outputimage, color, flags)
```
#### 参考代码
```
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt
# 1 图像读取
img = cv.imread('./image/tv.jpg')
# 2 ORB角点检测
# 2.1 实例化ORB对象
orb = cv.ORB_create(nfeatures=500)
# 2.2 检测关键点,并计算特征描述符
kp,des = orb.detectAndCompute(img,None) print(des.shape)
# 3 将关键点绘制在图像上
img2 = cv.drawKeypoints(img, kp, None, color=(0,0,255), flags=0)
# 4. 绘制图像
plt.figure(figsize=(10,8),dpi=100)
plt.imshow(img2[:,:,::-1])
plt.xticks([]), plt.yticks([])
plt.show()
```

# 视频操作
## 视频读写
### 从文件中读取视频并播放
在OpenCV中，要获取一个视频，需要创建一个 ```VideoCapture``` 对象，指定要读取的视频文件
#### 创建读取视频的对象
##### API
```
cap = cv.VideoCapture(filepath)
```
##### 参数
- filepath  
视频文件路径

### 视频的属性信息--获取视频的属性
#### API
```
retval = cap.get(propId)
```
#### 参数
- propId  
从0到18的数字，每个数字表示视频的属性
常用属性有
  - cv2.CAP_PROP_POS_MSEC
    - index:0
    - 视频文件的当前位置(ms)
  - cv2.CAP_PROP_POS_FRAMES
    - index:1
    - 从0开始索引帧，帧位置
  - cv2.CAP_PROP_POS_AVI_RATIO
    - index:2
    - 视频文件的相对位置（0表示开始，1表示结束）
  - cv2.CAP_PROP_FRAME_WIDTH
    - index:3
    - 视频流的帧宽度
  - cv2.CAP_PROP_FRAME_HEIGHT
    - index:4
    - 视频流的帧高度
  - cv2.CAP_PROP_FPS
    - index:5
    - 帧率
  - cv2.CAP_PROP_FOURCC
    - index:6
    - 编解码器四字符代码
  - cv2.CAP_PROP_FRAME_COUNT
    - index:7
    - 视频文件的帧

### 视频的属性信息--修改视频的属性信息
#### API
```
cap.set(propId，value)
```
#### 参数
- proid  
属性的索引，与上面的表格相对应
- value  
修改后的属性值

### 判断图像是否读取成功
#### API
```
isornot = cap.isOpened()
```
#### 若读取成功则返回true，否则返回False

### 获取视频的一帧图像
#### API
```
ret, frame = cap.read()
```
#### 参数
- ret  
若获取成功返回True，获取失败，返回False
- Frame  
获取到的某一帧的图像

调用 ```cv.imshow()``` 显示图像，在显示图像时使用 ```cv.waitkey()``` 设置适当的持续时间，如果太低视频会播放的非常快，如果太高就会播放的非常慢，通常情况下设置25ms

最后，调用 ```cap.realease()``` 将视频释放掉

### 参考代码
```
import numpy as np
import cv2 as cv
# 1.获取视频对象
cap = cv.VideoCapture('DOG.wmv')
# 2.判断是否读取成功
while(cap.isOpened()):
    # 3.获取每一帧图像
    ret, frame = cap.read()
    # 4. 获取成功显示图像
    if ret == True:
        cv.imshow('frame',frame)
    # 5.每一帧间隔为25ms
    if cv.waitKey(25) & 0xFF == ord('q'):
        break
# 6.释放视频对象
cap.release()
cv.destoryAllwindows()
```

### 保存视频
在OpenCV中，保存视频使用的是VedioWriter对象，在其中指定输出文件的名称
#### 创建视频写入的对象
##### API
```
out = cv2.VideoWriter(filename,fourcc, fps, frameSize)
```
##### 参数
- filename  
视频保存的位置
- fourcc  
指定视频编解码器的4字节代码
- fps  
帧率
- frameSize  
帧大小

### 设置视频的编解码器
#### API
```
retval = cv2.VideoWriter_fourcc( c1, c2, c3, c4 )
```
#### 参数
- c1,c2,c3,c4   
是视频编解码器的4字节代码，在fourcc.org中找到可用代码列表，与平台紧密相关，常用的有：
- 在Windows中  
DIVX（.avi） MP4v(.mp4)
- 在OS中  
MJPG（.mp4），DIVX（.avi），X264（.mkv）

利用 ```cap.read()``` 获取视频中的每一帧图像，并使用out.write()将某一帧图像写入视频中。

使用cap.release()和out.release()释放资源

### 参考代码
```
import cv2 as cv
import numpy as np

# 1. 读取视频
cap = cv.VideoCapture("DOG.wmv")

# 2. 获取图像的属性（宽和高，）,并将其转换为整数
frame_width = int(cap.get(3))
frame_height = int(cap.get(4))

# 3. 创建保存视频的对象，设置编码格式，帧率，图像的宽高等
out = cv.VideoWriter('outpy.avi',cv.VideoWriter_fourcc('M','J','P','G'), 10, (frame_width,frame_height))
while(True):
    # 4.获取视频中的每一帧图像
    ret, frame = cap.read()
    if ret == True: 
        # 5.将每一帧图像写入到输出文件中
        out.write(frame)
    else:
        break 

# 6.释放资源
cap.release()
out.release()
cv.destroyAllWindows()
```


## 视频追踪
### meanshift
#### 原理
- meanshift算法的原理很简单。假设有一堆点集，还有一个小的窗口，这个窗口可能是圆形的，现在可能要移动这个窗口到点集密度最大的区域当中
- 最开始的窗口是蓝色圆环的区域，命名为C1。蓝色圆环的圆心用一个蓝色的矩形标注，命名为C1_o
- 而窗口中所有点的点集构成的质心在蓝色圆形点C1_r处，显然圆环的形心和质心并不重合。所以，移动蓝色的窗口，使得形心与之前得到的质心重合。在新移动后的圆环的区域当中再次寻找圆环当中所包围点集的质心，然后再次移动，通常情况下，形心和质心是不重合的。不断执行上面的移动过程，直到形心和质心大致重合结束。这样，最后圆形的窗口会落到像素分布最大的地方，也就是图中的绿色圈，命名为C2
#### 应用
meanshift算法除了应用在视频追踪当中，在聚类，平滑等等各种涉及到数据以及非监督学习的场合当中均有重要应用，是一个应用广泛的算法
#### 使用meanshift算法来追踪一个运动的物体流程
- 首先在图像上选定一个目标区域
- 计算选定区域的直方图分布，一般是HSV色彩空间的直方图
- 对下一帧图像b同样计算直方图分布
- 计算图像b当中与选定区域直方图分布最为相似的区域，使用meanshift算法将选定区域沿着最为相似的部分进行移动，直到找到最相似的区域，便完成了在图像b中的目标追踪
- 重复3到4的过程，就完成整个视频目标追踪
- 通常情况下使用直方图反向投影得到的图像和第一帧目标对象的起始位置，当目标对象的移动会反映到直方图反向投影图中，meanshift 算法就把窗口移动到反向投影图像中灰度密度最大的区域了


#### 直方图反向投影的流程是
假设有一张100x100的输入图像，有一张10x10的模板图像，查找的过程是这样的：
- 从输入图像的左上角(0,0)开始，切割一块(0,0)至(10,10)的临时图像
- 生成临时图像的直方图
- 用临时图像的直方图和模板图像的直方图对比，对比结果记为c
- 直方图对比结果c，就是结果图像(0,0)处的像素值
- 切割输入图像从(0,1)至(10,11)的临时图像，对比直方图，并记录到结果图像
- 重复1～5步直到输入图像的右下角，就形成了直方图的反向投影


#### 在OpenCV中实现
##### API
```
cv.meanShift(probImage, window, criteria)
```
##### 参数
- probImage  
ROI区域，即目标的直方图的反向投影
- window  
初始搜索窗口，就是定义ROI的rect
- criteria  
确定窗口搜索停止的准则，主要有迭代次数达到设置的最大值，窗口中心的漂移值大于某个设定的限值等

##### 实现Meanshift的主要流程是
- 读取视频文件
```
cv.videoCapture()
```
- 感兴趣区域设置
获取第一帧图像，并设置目标区域，即感兴趣区域
- 计算直方图
计算感兴趣区域的HSV直方图，并进行归一化
- 目标追踪
设置窗口搜索停止条件，直方图反向投影，进行目标追踪，并在目标位置绘制矩形框

#### 参考代码
```
import numpy as np
import cv2 as cv
# 1.获取图像
cap = cv.VideoCapture('DOG.wmv')

# 2.获取第一帧图像，并指定目标位置
ret,frame = cap.read()
# 2.1 目标位置（行，高，列，宽）
r,h,c,w = 197,141,0,208  
track_window = (c,r,w,h)
# 2.2 指定目标的感兴趣区域
roi = frame[r:r+h, c:c+w]

# 3. 计算直方图
# 3.1 转换色彩空间（HSV）
hsv_roi =  cv.cvtColor(roi, cv.COLOR_BGR2HSV)
# 3.2 去除低亮度的值
# mask = cv.inRange(hsv_roi, np.array((0., 60.,32.)), np.array((180.,255.,255.)))
# 3.3 计算直方图
roi_hist = cv.calcHist([hsv_roi],[0],None,[180],[0,180])
# 3.4 归一化
cv.normalize(roi_hist,roi_hist,0,255,cv.NORM_MINMAX)

# 4. 目标追踪
# 4.1 设置窗口搜索终止条件：最大迭代次数，窗口中心漂移最小值
term_crit = ( cv.TERM_CRITERIA_EPS | cv.TERM_CRITERIA_COUNT, 10, 1 )

while(True):
    # 4.2 获取每一帧图像
    ret ,frame = cap.read()
    if ret == True:
        # 4.3 计算直方图的反向投影
        hsv = cv.cvtColor(frame, cv.COLOR_BGR2HSV)
        dst = cv.calcBackProject([hsv],[0],roi_hist,[0,180],1)

        # 4.4 进行meanshift追踪
        ret, track_window = cv.meanShift(dst, track_window, term_crit)

        # 4.5 将追踪的位置绘制在视频上，并进行显示
        x,y,w,h = track_window
        img2 = cv.rectangle(frame, (x,y), (x+w,y+h), 255,2)
        cv.imshow('frame',img2)

        if cv.waitKey(60) & 0xFF == ord('q'):
            break        
    else:
        break
# 5. 资源释放        
cap.release()
cv.destroyAllWindows()
```

### Camshift
#### meanShift的局限性
meanShift检测的窗口的大小是固定的，而检测对象如果由近及远，则是一个逐渐变小的过程，固定的窗口是不合适的。所以我们需要根据目标的大小和角度来对窗口的大小和角度进行修正。CamShift可以解决这个问题

#### Camshift算法定义
- CamShift算法全称是“Continuously Adaptive Mean-Shift”（连续自适应MeanShift算法），是对MeanShift算法的改进算法，可随着跟踪目标的大小变化实时调整搜索窗口的大小，具有较好的跟踪效果

- Camshift算法首先应用meanshift，一旦meanshift收敛，它就会更新窗口的大小，还计算最佳拟合椭圆的方向，从而根据目标的位置和大小更新搜索窗口
#### OpenCV实现
Camshift在OpenCV中实现时，只需将上述的meanshift函数改为Camshift函数即可

将Camshift中的
```
    # 4.4 进行meanshift追踪
        ret, track_window = cv.meanShift(dst, track_window, term_crit)

        # 4.5 将追踪的位置绘制在视频上，并进行显示
        x,y,w,h = track_window
        img2 = cv.rectangle(frame, (x,y), (x+w,y+h), 255,2)
```

改为
```
  #进行camshift追踪
    ret, track_window = cv.CamShift(dst, track_window, term_crit)

        # 绘制追踪结果
        pts = cv.boxPoints(ret)
        pts = np.int0(pts)
        img2 = cv.polylines(frame,[pts],True, 255,2)
```



### Meanshift和camshift算法对比
#### Meanshift算法
##### 优点
简单，迭代次数少
##### 缺点
无法解决目标的遮挡问题并且不能适应运动目标的的形状和大小变化
#### camshift算法
##### 优点
可适应运动目标的大小形状的改变，具有较好的跟踪效果
##### 缺点
当背景色和目标颜色接近时，容易使目标的区域变大，最终有可能导致目标跟踪丢失


# opencv中人脸识别
## opencv中人脸识别的流程
### 读取图片，并转换成灰度图
### 实例化人脸和眼睛检测的分类器对象
#### API
##### 实例化级联分类器
```
classifier =cv.CascadeClassifier( "haarcascade_frontalface_default.xml" ) 
```
##### 加载分类器
```
classifier.load('haarcascade_frontalface_default.xml')
```
### 进行人脸和眼睛的检测
#### API
```
rect = classifier.detectMultiScale(gray, scaleFactor, minNeighbors, minSize,maxsize)
```
### 将检测结果绘制出来

































