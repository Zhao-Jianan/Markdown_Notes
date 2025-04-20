# Project Settings/项目设置
## Render Extents and Normal Build Resolution
### Location
调节地形整体尺寸
### Normal Build Resolution
调节输出地形图的分辨率

## General Setup
### Terrain Altitudes
调节地形的最高海拔


# 节点
## Tools/工具
- Filter Devices by Data Type/按数据类型分类节点
- Filter Devices by Device Type/按类型分类节点
- Define Favorites List/编辑收藏夹
- Grouping Tool/群组工具
用来将节点打组

## Macros/宏指令
宏相当于预设的指令，存储的是布线流程
### Coverage Library/范围选择库
#### Height Coverage/高度范围
基于高度选择创建范围图。可以控制所选的高程带、高程带边缘的羽化以及分形覆盖。分形覆盖允许指定选择的强度，并为范围选择添加一些可选的随机性
##### 参数
- Selection Altitude---------------选择高度，调节选择的高度范围
- Selection Width------------------选择宽度，控制高度范围边缘的羽化
- Selection Blend------------------分形混合强度
- Coverage Value-------------------覆盖值，调节坡度范围的整体亮度
- Fractal Coverage-----------------分形燥波整体强度
- Fractal Scale--------------------分形燥波尺寸

#### Local Heights/局部高度
生成包含“局部高度”数据的遮罩。局部高度考虑到周围环境的高度，并根据其是否高于或低于这些高度进行计算。这样，可以让所有尺度的山脊和山峰都显示为白色，而低处则是黑色。这些信息对于创建纹理遮罩非常有用

#### Mask Breakup/遮罩离散
输出一个高度图，这个节点会在原有高度图上叠加一层燥波或泰森多边形，让黑白的效果有一定随机
##### 参数
- Masking Type---------------------遮罩类型
  - Perlin Noise---------------------柏林燥波
  - Voronoi--------------------------泰森多边形
- Masking Amount-------------------遮罩数量
- Masking Scale--------------------遮罩尺寸

#### Slope Coverage/坡度范围
基于坡度选择创建范围图。可以控制所选坡度的范围、坡度边缘的羽化以及分形覆盖率。分形覆盖允许指定选择的强度，并为范围选择添加一些可选的随机性
##### 参数
- Slpoe----------------------------坡度，调节选择的坡度范围
- Slope Band-width-----------------调节选择的坡度边缘羽化
- Selection Blend------------------分形混合强度
- Coverage Value-------------------覆盖值，调节坡度范围的整体亮度
- Fractal Coverage-----------------分形燥波整体强度
- Fractal Scale--------------------分形燥波尺寸

### Surface Maps/表面图库
#### Basic Coverage/基础范围
一个非常有用的纹理创建宏，具有多种预设。可以自定义各种基于高度/坡度的纹理的颜色。当使用侵蚀时，输入绘制侵蚀的水流、植被、沉积图时，效果最佳
##### 参数
- Sand-----------------------------沙土颜色
- Rock-----------------------------岩石颜色
- Vegetation-----------------------植被颜色
- Erosion--------------------------侵蚀颜色
- Height Cutoff--------------------高度界限
- Slope Cutoff---------------------坡度界限
- Lighting-------------------------开启灯光效果
- Invert Height Cover--------------反转高度覆盖物
- Presets
  - Dover----------------------------雨林三角洲
  - Grass and Dusty Rock-------------草丛和尘土覆盖的颜色
  - Pacific Northwest----------------太平洋西北部
  - Snowy Dusting--------------------粉状雪花
  - Sandy Desert---------------------沙化荒漠

#### Basic Splatmap

#### Colorizer 2

### Blend Layers/混合层
提供了13种图片混合模式
##### 参数
- Blend Mode-----------------------混合模式
  - Normal---------------------------正常
  - Darken---------------------------变暗
  - Lighten--------------------------植被颜色
  - Multiply-------------------------相乘
  - Dissolve-------------------------融解
  - Screen---------------------------屏幕
  - Difference-----------------------不同
  - Hue------------------------------色相
  - Saturation-----------------------饱和度
  - Luminosity-----------------------发光
  - Add------------------------------相加
  - Substract------------------------相减
  - Overlay--------------------------覆盖
- Opacity--------------------------透明度

### Object Placer/放置对象
用来在地形上放置对象，这个对象可以用File Input连接，导入一个高度图，可以用来导入logo放置在地形上
##### 参数
- Object resize--------------------对象尺寸
- Move from left to right----------左右偏移
- Move from top to bottom----------上下偏移
- Placing method-------------------放置模式
  - Add to Terrain-------------------添加对象让其对于地形之上，对象仅在高于地形的位置出现
  - Substract from Terrain-----------让对象相减，看起来像刻在地形上一样，对象只会出现在低于地形的位置
- Insertion strength---------------插入强度，控制对象的置换强度
- Object clamp---------------------对象钳制，控制对象高度
- Terrain clamp--------------------地形钳制，控制地形高度

**使用Object clamp和Terrain clamp配合调整对象放置的形态，Add to Terrain模式下Terrain clamp数值增大会降低地形高度，Substract from Terrain模式下Terrain clamp数值增大会提升地形高度**


### Seamless Map/无缝地图
### Sharpen-(pro)/陡峭pro
陡峭的高级样式，用来使地形变得陡峭，细节很好
##### 参数
- Sharpening Strength--------------陡峭强度
- Method Balance-------------------平衡方法，Sharpen-(pro)使用了两种不同的锐化方法。一种是通过增加地形来锐化地形，另一种是通过从某些区域减去高度来锐化地形。如果小于0.5，则执行更多的减影锐化。大于0.5则执行更多的加法锐化。等于0.5意味着两者都被同等使用
- Style----------------------------风格
  - Basic----------------------------基础
  - Advanced-------------------------高级，高级样式更类似于“遮罩取消锐化”，锐化效果的强度更大
- Radius---------------------------半径

### Simple Layer/简单层

## Generator/生成器
### Layout Generator/布局生成器
很重要，手动创建地形
##### 参数
- Layout Properties----------------布局属性
  - Precision vs Speed---------------精准度和生成速度
  - Display as Mask------------------作为黑白遮罩
  - Use Breakup----------------------使用解体，让规整的地形变的不规整
    - Fractal Breakup------------------分形解体强度
    - Breakup Scale--------------------解体尺寸，值越大，分形的块越大，值越小，分形的块越小
    - Roughness------------------------粗糙度
  - Invert Values--------------------翻转值，会让凸出的地方变成凹陷
  - Shape List-----------------------形状列表，所有添加的形状都在形状列表里显示
  - Shape Common Properties----------形状通用设置，双击形状可以弹出
    - Default Value(Height)------------地形高度
    - Opacity(Strength)----------------透明度
    - Falloff Distance-----------------衰减距离，控制形状影响的范围
    - Falloff Profile Curve------------曲线控制地形衰减形态
    - Shape Breakup Participation------控制解体的影响强度

### Perlin Noise/柏林燥波
传统的柏林燥波
##### 参数
- Heightfield Generation Parameters-
  - Noise Type-----------------------燥波类型
  - Octave---------------------------细节阶度
  - Persisstence---------------------持续量
  - Offset---------------------------偏移量
  - Gain-----------------------------偏移增益
### Advanced Perlin/高级柏林燥波地形
即新版本的柏林燥波
##### 参数
- Feature Scale--------------------地形尺寸
  - Boulders-------------------------巨石
  - Hills----------------------------山丘
  - Mountains------------------------山脉
  - Continents-----------------------大陆
- Basic Parameters-----------------基本参数
  - Style----------------------------地形风格
    - Basic----------------------------基本
    - Ridged---------------------------山脊
    - Billowy--------------------------山谷
    - Smooth Ridged--------------------平滑山脊
    - Smooth Billowy-------------------平滑山谷
    - Sharp Ridged---------------------锐利山脊
    - Flat Middle----------------------中间平坦
    - Terraced-------------------------阶地
    - Stephen's Choice 1---------------斯蒂芬的选择1
  - Octaves--------------------------细节阶度
  - Persistence----------------------地形持续时间
  - Elevation Center-----------------海拔，整体提高或降低地形的海拔
  - Steepness------------------------陡峭程度
  - Random Seed----------------------随机种子
- Guide Levels&Input---------------导向器级别和输入，在连接相应的节点后可以调整导向器影响级别
- Multiscale Fractal Parameters----多尺度分形参数
  - Activity-------------------------地形活动，可以增加燥波模糊度
  - Offset---------------------------地形偏移
- Presets--------------------------地形预设
  - Canyons--------------------------峡谷
  - Swiss Cheese---------------------瑞士奶酪状地形
  - Very Fractal---------------------非常不规则
  - Wrinkled-------------------------褶皱
- Customize Fractal Profile--------勾选后可以叠加多层风格
  - +Octave--------------------------添加风格层
  - -Octave--------------------------移除当前所选风格层
  - Clear All------------------------移除所有风格层
  - Edit selected noise level--------选择当前风格层的风格
  - Strength-------------------------当前风格层影响强度
##### 端口
- 输入端口
  - Shaping Guide(Heightfield)-------形状导向器，最基础和常用的输入端口
  - Distortion guide(Heightfield)----扭曲导向器
  - Persistence guide(Heightfield)---持续导向器
  - Mask Input-----------------------作为遮罩输入，非常常用，通常使用Radial Grad节点输入时使用这个端口


### Constant/常数
生成一个等高的地形基础形状
##### 参数
- Height---------------------------高度


### Gradient/渐变
生成一个梯度渐变的地形基础形状
##### 参数
- Direction------------------------方向
- Width----------------------------宽度
- Tiling---------------------------平铺模式
  - None-----------------------------不平铺
  - Linear---------------------------线性，平铺是连续的
  - Discontinuous--------------------不连续的


### Radial Grad/径向渐变
最常用的生成地形的基础形状
##### 参数
- Radius---------------------------渐变半径
- Type-----------------------------渐变类型
  - Spherical------------------------球形渐变
  - Gaussian-------------------------高斯渐变
  - Diamond--------------------------菱形渐变
  - Square---------------------------方形渐变
  - Cone-----------------------------锥形渐变
##### 端口
- 输出端口
  - Primary Output(Heightfield)------基础输出端口，通常输出到Advanced Perlin节点的Mask Input端口

### Voronol/泰森多边形
##### 参数
- Scale----------------------------尺寸
- Style----------------------------风格，最常使用F2风格
- Shape----------------------------形状
- Randomize------------------------随机

### Color Generator/颜色生成器
用来加载颜色，与OC中的RGB节点功能相同
##### 参数
- Color----------------------------颜色

### File Input/导入文件
可以加载纹理贴图来控制地形，只支持png格式
##### 参数
- File Details---------------------文件详情
  - Load-----------------------------导入文件
  - Interpret as RGB-----------------读取RGB信息，如果不勾选，默认会只读取纹理的灰度信息
- World Placement------------------布局
  - XY-------------------------------默认为0m，即原点在左下角，缩放时会以左下角为基准点，一般设为4km
  - Quick Scaling--------------------快速缩放
- Outside Behavivor----------------分布
  - Blank----------------------------无
  - Tile-----------------------------平铺
  - Mirror---------------------------镜像

## Output/输出
### Height Output/高度图输出
用来最终导出高度图
##### 参数
- Filename-------------------------文件名
- Set------------------------------设置输出路径和文件名
- Write output to disk-------------输出高度图到硬盘
- File Format----------------------选择文件格式
**通常选择16位PNG或16位TIFF**
##### 端口
- 输入端口
  - Primary Input(Heightfield)-------高度图输入端口

### Mesh Output/模型输出
将地形输出为OBJ格式的模型

### Bitmap Output/位图输出
用来最终导出颜色贴图或法线贴图等带颜色信息的贴图
##### 参数
- Specify Output File---------------设置输出路径和文件名
- File Name-------------------------文件名
- File Format-----------------------设置文件格式
**通常选择16位PNG或16位TIFF**
- Write output to disk-------------输出位图到硬盘
##### 端口
- 输入端口
  - RGB Input(Bitmap)----------------位图输入端口

### Overlay View/覆盖视图
用来预览最终效果
##### 端口
- 输入端口
  - Primary Input(Heightfield)-------高度图输入端口
  - Overlay Input(Mixed)-------------效果图输入端口


## Combiner/合并器
### Height Chooser/高度合并器
##### 端口
- 输入端口
  - Guide Input(Heightfield)---------基础地形输入端口
  - Lowest Values(Mixed)-------------最低位置输入端口，输入的地形与基础地形的低位进行混合
  - Middle 1 Values(Mixed)-----------中间1位置输入端口
  - Highest Values(Mixed)------------最高位置输入端口，输入的地形与基础地形的高位进行混合

### Chooser/选择合并器

### Combiner/合并器
非常常用，将两个节点混合
##### 参数
- Method---------------------------混合模式
  - Average--------------------------平均，两个地貌的高度相加除以2,平均在一起的两种地形，其强度参数控制的加权平均
  - Add------------------------------相加,添加地形二到地形一。强度控制添加量进行调整
  - Subtract-------------------------相减,从地形一中减去地形二。强度控制调整的减量
  - Multiply-------------------------相乘,将地形乘在一起。 从零到乘法的强度控制混合强度
  - Max------------------------------最大值,在每个点使用任何地形的最高高度
  - Min------------------------------最小值，在每个点使用任何地形的最低高度
  - Power----------------------------幂，把第一个地形的幂与不同的基于第二的幂相加
  - Root-----------------------------根，一般用于高度图黑白通道的直接叠加，使用时一般强度为1，原理是把第一个地形的根与不同的幂基于第二的根相加
  - Detail---------------------------细节，一般用于添加细节的贴图，使用时一般强度调整到非常小
- Strength-------------------------混合强度

## Filter/过滤器
对地貌进行细节刻画
### Clamp/钳制
用来对高度、对比度等进行约束
##### 参数
- Clamp Style----------------------钳制模式
  - Clamp----------------------------挤压，把高海拔往低压，把低海拔往高压
  - Clio-----------------------------剪切，将高海拔或低海拔直接剪切掉
  - Expard---------------------------延展，将高海拔面积增大，把低海拔面积减小
- Fand Extents---------------------自动布局
### Simple Transform/简单变换
##### 参数
- Height Transforms----------------高度变换
  - Caryonize------------------------让地形最高点与周围地形更加顺滑
  - Glaciate-------------------------使低位更加顺滑
  - Cubic Midands--------------------使中间位置产生平滑平台
  - Midard Plateau-------------------使中间位置产生锐利平台
- Kernel Transforms----------------核心变换
  - Smoothing Filter-----------------平滑度
  - Height-varying lowpass filter----高度变换低通过滤器，对锐利程度进行调节

### Terrace/梯度
用来制作梯田等效果
##### 参数
- Terrace Method-------------------梯度方式
- Number of Terraces---------------梯度值，一般设为30左右
- Terrace Shape--------------------梯度强度，0.5强度为0，大于0.5为正方向越来越强，小于0.5为负方向越来越强
- Terrace Layering-----------------梯度层，一般调到最大

### Curves/曲线
用曲线来控制斜坡形态

### Simple Displacement/简单置换变形

### Ramp/斜坡
使地形变为波浪形
##### 参数
- Type of Ramp---------------------斜坡类型
- Frequency------------------------斜坡频率

### Height Splitter/高度分离
可以将地形按高度分离，可以分离出高位、低位、多个中间位

### Add Noise/添加燥波
在现有地形基础上再添加一层燥波

### Probability/随机概率
功能类似于随机遮罩，会生成一个随机的黑白遮罩

### Flipper/翻转
可以水平和垂直翻转地形

### Equalizer/均衡器
将地形的整体进行均衡

### Blur/模糊

### Expander/地形燥波像素增益
不常用，一般做荒漠时使用，会将地形像素化

### Inverter/反向
用来把高度图黑白反向

### Bias/Gain


## Natural/自然
### Erosion/雨水河流侵蚀
非常重要的节点
##### 参数
- Erosion Parameters---------------侵蚀参数
  - Erosion Method-------------------侵蚀方法
    - Standard Erosion-----------------标准侵蚀，沟壑比较浅
    - Channeled Erosion----------------通道侵蚀，沟壑比较深
  - Erosion base duration------------侵蚀时间，数值越大，侵蚀强度越强，一般设为50-100之间
  - Rock hardness--------------------岩石硬度
  - Sediment carry amount------------沉积物携带
  - Randomize------------------------随机种子
- Presets--------------------------预设
  - A Flood of Slurry----------------泥浆泛滥，最常用
  - Classic WM Erosion---------------传统侵蚀
  - Cool Erossion--------------------寒冷侵蚀
  - Full Strength--------------------全强度
  - Good with Terraces---------------好的阶度效果，如果添加了梯度节点，一般使用这个预设
- Geological-time Enhancement------二次侵蚀，会有更多细节
  - Enable---------------------------激活二次侵蚀
  - Erosive Power--------------------二次侵蚀强度
- Channeling Erosion Parameters----控制通道侵蚀
  - Channel depth--------------------通道深度
##### 端口
- 输入端口
  - Primary Input(Heightfield)-------高度图输入端口
- 输出端口
  - Primary Output(Heightfield)------高度图输出端口
  - Flow Map(Heightfield)------------水流图输出端口
  - Wear Map(Heightfield)------------植被图输出端口
  - Deposition(Heightfield)----------沉积图输出端口

### Thermal Weathering/热空气侵蚀

### Snow/雪侵蚀

### Coast Erosion/海岸侵蚀


## Selector/选择器
### Select Height/选择高度
这个节点通过读取高度图可以选择高度范围，可以制作积雪等效果
##### 参数
- Slider---------------------------滑块调节高度范围
- Falloff Adjustment---------------对比度调整

### Select Slope/选择坡度
这个节点通过读取高度图可以选择坡度范围，再输出到Select Height节点的Mask Input端口，可以制作积雪等效果
##### 参数
- Slider---------------------------滑块调节高度范围
- Falloff Adjustment---------------对比度调整

### Select Angle/选择角度
通过设置灯光角度来生成黑白贴图
##### 参数
- Heading--------------------------灯光角度
- Elevation------------------------海拔

### Select Convexity/选择凸起

### Select Color/选择颜色

## Converter/转换器
### Coverage Maker/

### Normal Map Maker/制作法线贴图
将高度信息输入到Normal Map Maker节点，再输出到Bitmap Output节点，制作法线贴图

### Splat Converter/分裂变换器
用来生成Setmap,不常用

### Channel Splitter/通道分离器
用来生成Setmap,不常用

### Channel Combiner/通道合并器
用来生成Setmap,比较常用
给RGB三个通道各一个输入，生成颜色
### Colorizer/颜色

### Light-Map Maker/制作光照贴图
##### 参数
- Illumination Model---------------全局光照模型
  - Direct Lighting------------------定向光源
  - Raytraced Lighting---------------光线追踪
- Included Lighting----------------包含的光照信息
- Produce RGB Lightmap-------------产生RGB光照图，一般要勾选
- Soft Clipping--------------------软裁切，默认勾选
- Use Global Light Direction-------使用全局光照方向
- Sun Heading----------------------日光方向
- Sun Altitude---------------------日光强度
- Sky Lighting Level---------------天空光级别
- Diffuse Level--------------------漫射光级别


## Parameter

## Flow Control