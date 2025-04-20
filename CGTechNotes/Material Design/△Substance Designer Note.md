# 基础知识
## 材质创建流程
- 第1步：创建灰度图（Greyscale）包括：Basic Shapes/基本形状、Large-Medium Shapes/大-中形状、Small Details/小细节、Height/高度
- 第2步：创建贴图（Create Maps）包括：Normal/法线贴图、Ambient Occlusion/环境吸收贴图、Roughness/粗糙度贴图
- 第3步：调整反射和颜色（Albedo）
- 第4步：材质混合（Material Blending）
- 第5步：输出（Outputs）
## 主要贴图类型
### Base Color/Diffuse/Albedo
特点：
1. 纯色调，类似矢量，提供物体在不依赖光照条件下的颜色，即本色
2. 不带任何光影信息
3. 不存在纯白和纯黑，因为自然界不存在，PBR的宗旨是模拟真实世界，制作贴图时要特别注意
4. 颜色明度控制在30-240（0.11-0.94）之间
### Normalmap
是低模展现高模细节的手段
### Metallic
特点：
1. 定义是否为金属
2. Metallic贴图是0-1的灰度图
3. 0代表此处不是金属，1代表此处是金属
### Ambient Occlusion/AO/Occ
特点：
1. 环境光遮蔽
2. 物体自身夹角产生的阴影
3. 是0-1的灰度图
4. 有了AO，模型之间就有了层次
### Roughness
特点：
1. 定义模型表面某一区域的光滑程度
2. Microscopic（微表面理论）
3. 是0-1的灰度图
4. 操作性很大，可以充分发挥想象力，通过绘制不同光滑度来表现真实感
5. Glossiness与Roughness描述的属性相同，只是数值相反

# Library/库
## Graph Items
- Comment/注释节点
- Frame/打组节点
- Pin/大头针节点
## Atomic Nodes/原子节点
最基础最优化的节点
### Bitmap/位图（源素材输入节点）
- 导入参数
  - From File-------------------通过文件导入一张图片
  - From New Resource-----------新建资源，新建资源可以设置背景色，然后可以在二维视图中用笔刷自由绘制
- Base Parameters-------------基础参数
  - Output Size-----------------输出尺寸
  - Output Format---------------输出位数
  - Pixel Size------------------像素尺寸
  - Random Seed-----------------随机种子
- Specific Parameters---------特殊参数
  - Color Mode------------------颜色模式
    - Color-----------------------颜色模式
    - Grayscale-------------------灰度模式
  - Resize Method---------------调整尺寸模式
    - Smooth Stretch---------------平滑拉伸
    - Nearest Stretch--------------附近像素点拉伸

### Blend/混合
- Specific Parameters---------特殊参数
  - Opacity---------------------透明度，混合程度，1为完全显示主节点Background，0为完全显示辅节点Foreground
  - Blending Mode---------------混合模式
    - Copy------------------------复制，直接输出辅节点，改变Opacity 的数值可在两个节点间往返，相当于PS中的正常
    - Add(Linear Dodge)-----------相加（线性减淡），将辅节点的颜色加到主节点上，相当于PS中的线性减淡
    - Subtract--------------------相减，主节点颜色减去辅节点颜色
    - Multiply--------------------相乘，两个节点颜色相乘，任何色与白色混合保持不变，与黑色混合则变暗
    - Add Sub---------------------添加减去，添加黑色区域、减去白色区域，相当于PS中的线性光
    - Max(Lighten)----------------最大（变亮），两个节点的颜色取最大值
    - Min(Darken)-----------------最小（变暗），两个节点的颜色取最小值
    - Switch----------------------转换，改变Opacity 的数值可从主节点逐渐转化到辅节点，数值从1到0，前景透明度慢慢提高，背景不透明度慢慢降低，由于图片像素不是均匀的，因此在中间输出的图片可能会出现半透明
    - Divide----------------------相除，依据辅节点的灰度对主节点颜色进行区域划分，如果辅节点该区域为黑色，则主节点颜色在该区域不显示，如果辅节点该区域不为黑色，则主节点颜色在该区域显示，相当于PS中的划分
    - Overlay---------------------叠加
    - Screen----------------------屏幕，将辅节点颜色的互补色与主节点颜色混合
    - Soft Light------------------柔光
  - Alpha Blending--------------Alpha混合模式，通常使用前两种模式，后两种模式是为了和不同的软件之间相互兼容
    - Use Source Alpha------------使用纹理来源Alpha通道混合
    - Ignore Alpha----------------忽略Alpha通道
  - Cropping Area---------------对前景Foreground进行修剪


### Blur/模糊（图像处理节点）
简单模糊，效果比较简单

### Channels Shuffle/通道随机混合（色彩调整节点）
输入两个颜色节点，获取两个颜色节点的RGBA通道信息，可以设置输出的颜色的RGBA通道分别使用哪个通道

### Curve/曲线（色彩调整节点）
- Specific Parameters---------特殊参数
  - Curve Addressing------------曲线寻址方式
    - Repeat----------------------当有像素大于1或小于0时，进行标准化映射到0-1
    - Clamp-----------------------当有像素大于1或小于0时，将全部大于1的像素钳制到1，将全部小于0的像素钳制到0


### Directional Blur/方向模糊（图像处理节点）

### Directional Wrap/方向变形
对形状进行变形，由另一个形状来控制变形的方向

### Distance/距离（图像处理节点）
输入节点的灰度大于0.5的像素都会向外产生线性渐变，向外扩展的渐变在遇到另一个单位为止，渐变不会发生重叠

主要使用情况是使用比模糊和调整对比度更可靠的方式扩展现有的遮罩，生成燥波，并用一个尖锐的线性轮廓斜切现有形状（之后可以重新映射）

### Emboss/浮雕（图像处理节点）
与PS中的浮雕效果相同

### FX-Map/FX映射（复杂原子节点）
最强大的原子节点之一，对输入的节点或自带的图形进行平铺或随机分布
- 输入端口
  - Background------------------背景图
  - Input Image-----------------输入的图片
- Specific Parameters---------特殊参数
  - Background------------------背景色
  - Roughness-------------------粗糙度，如果平铺后颜色太暗，可以调节粗糙度，粗糙度为0时显示原图片颜色
- Edit------------------------编辑，点击进入FX-Map的节点内部编辑器进行编辑
#### Quadrant/象限节点
用来进行分象限细分，上面端口为输出，下面四个端口为输入，分别对应一、二、三、四象限
- Color/Luminosity------------整体颜色和亮度调节
- Branch Offset---------------整体偏移
- Pattern---------------------图案，选择输入的图案
  - No Pattern------------------没有图案
  - Input Image-----------------使用节点输入的图片
  - Square----------------------正方形
- Pattern Offset--------------图案偏移
- Pattern Size----------------图案尺寸
- Pattern Rotation------------图案旋转
- Blending Mode---------------图案混合模式
- Input Image Index-----------输入图案索引
#### Iterate/迭代节点
相当于For循环，在原位置迭代复制多次，再通过参数调节移动旋转缩放
- Iterations------------------迭代次数
#### Switch/转换节点
在两个输入端切换


### Gradient(Dynamic)/动态渐变（色彩调整节点）
输入一个灰度节点和一个颜色节点，获取颜色节点的颜色渐变信息给灰度节点上色
- Specific Parameters---------特殊参数
  - Gradient Orientation--------渐变方向
    - Horizontal------------------水平方向
    - Vertical--------------------垂直方向
  - Gradient Input Position-----渐变开始位置
**Gradient(Dynamic)节点只能输出颜色，不能直接输出灰度，要输出灰度，需要Grayscale Conversion节点转换**

### Gradient Map/渐变映射（色彩调整节点）
非常重要和常用的节点，可以把灰度节点映射为颜色节点，也可以生成渐变，改变映射颜色等
- Specific Parameters---------特殊参数
  - Gradient Editor-------------渐变编辑器
    - Pick Gradient---------------拾取渐变，可以在屏幕中绘制一条线来拾取线上的颜色生成渐变


### Grayscale Conversion/灰度转换（色彩调整节点）
把带颜色的节点转化为灰度节点
- Specific Parameters---------特殊参数
  - Channels Weights------------单独调节每个通道的亮度
  - Flatten Alpha---------------压平Alpha通道，如果不激活，输入节点Alpha通道不会被识别，激活后可以识别输入节点的Alpha通道
  - Background Value------------激活压平Alpha通道后，设置将Alpha输出为一个灰度值

### HSL（色彩调整节点）
调整色相、饱和度、明度

### Levels/色阶（色彩调整节点）
一般用来调整灰度图的对比度、亮度、Gamma等

### Normal/法线
- Base Parameters-------------基础参数
- Specific Parameters---------特定参数
  - Intensity-------------------强度，默认的数值太小，可以手动输入
  - Normal Format---------------法线构成

### Output/输出

### Pixel Process/像素处理

### Sharpen/锐化（图像处理节点）

### SVG/矢量图（源素材输入节点）
与位图类似，可以导入SVG格式的矢量文件，也可以创建一个空文件在2D视图中绘制矢量图形

### Text/文字（源素材输入节点）
文字输入，对英文支持很好，对中文支持不太好，输入中文可以在PS中制作成贴图导入
- Specific Parameters---------特定参数
  - Color Mode------------------颜色模式
    - Color-----------------------颜色模式
    - Grayscale-------------------灰度模式
  - Text------------------------输入文字
  - Font------------------------字体
  - Alignment-------------------对齐方式
  - Transformation--------------变换

### Transformation 2D/2D变换（图像处理节点）
添加Transformation 2D节点后，会在2D窗口出现一个控制框，控制2D形状的移动旋转缩放

**有的燥波自带参数无法调节移动旋转缩放，可以添加一个Transformation 2D节点进行调节，但是要注意有的燥波在使用Transformation 2D缩放和旋转后会有接缝，此时可以使用**

### Uniform Color/统一颜色（源素材输入节点）
可以用来输出一个带有RGBA四通道的纯色或一个单通道的灰度
- Specific Parameters---------特定参数
  - Color Mode------------------颜色模式
    - Color-----------------------四通道颜色模式
    - Grayscale-------------------灰度模式
  - Output Color----------------输出颜色
    - sRGB------------------------激活后使用sRGB颜色
    - Float-----------------------激活后颜色值为0-1，取消激活颜色值为0-255
    - HSV-------------------------激活后使用HSV模式调节，取消激活使用RGB模式调节


### Warp/变形
可以和Shape节点配合，生成随机形态的形状。也可以让燥波方向跟随形状发生变化


## Function Nodes/函数节点
函数节点的使用类似UE中的蓝图，使用逻辑节点进行可视化编程，使用时在要创建函数的节点参数右上角点击Empty Function,为参数创建函数面板，在函数面板中使用函数节点
### Constant/常量
### Vector/向量
### Variables/变量
### Samplers/采样器
### Cast/数据转换
### Operator/运算符
### Logical/逻辑运算
### Comparison/比较运算
### Function/函数
#### Ceil/最高限度
对浮点数向上取整
### Control/控制


## Generators/生成器
### Noises/燥波
#### Dirt3/肮脏3
带有块状结构，可以制作泥块等
#### Dirt4/肮脏4
带有条状结构，可以制作沟状凹槽等
#### Grunge Map2
可以用来制作树皮的纹理
#### Grunge Map15
有大片的白色区域和大片的黑色区域，黑白分明，并且带有很多划痕，用来制作地面细节
#### Perlin Noise/柏林燥波
制作大形时常用
  - Base Parameters-------------基础参数
  - Instance Parameters---------实例参数
    - Scale-----------------------缩放尺寸
    - Disorder--------------------混乱程度

### Patterns/样式
#### Shape/形状
非常常用，一些基本的形状
#### Shape Splatter/形状溅射
非常重要，用来将形状随机分布
  - Instance Parameters---------实例参数
    - X Amount--------------------横向平铺数
    - Y Amount--------------------纵向平铺数
    - Pattern---------------------样式
      - Pattern Input Number--------输入数量，控制有几个输入端口，几个形状参与溅射
      - Pattern Distribution Mode---分布模式
      - Pattern Rotation------------样式旋转
      - Pattern Rotation Random-----样式旋转随机强度
    - Size------------------------尺寸
      - Scale-----------------------缩放
      - Scale Random----------------缩放随机强度
      - Scale Map Multiplier--------尺寸贴图影响强度，尺寸贴图连接到Shape Scale端口
      - Size Ratio from Bg Slope----依据背景坡度调节尺寸半径
    - Position--------------------位置
      - Position Random-------------位置随机强度
      - Random Distribution---------随机分布模式
      - Offset Horizontal-----------水平偏移
      - Offset Vertical-------------垂直偏移
    - Rotation--------------------旋转
      - Rotation--------------------旋转角度
      - Rotation Random-------------旋转随机值
      - Rotation from Bg Slope------依据背景坡度旋转
    - Height----------------------高度
      - Height Scale Auto Adjust----高度尺寸自动调整
      - Height Offset---------------高度偏移
      - Height Offset Random--------高度偏移随机强度
      - Height Scale----------------高度尺寸
      - Height Scale Random---------高度尺寸随机强度
      - Conform to Background-------垂直于背景地形
      - Smooth Conformed Background-由背景确定平滑，会根据背景对高度进行平滑，减少噪点
    - Masking---------------------遮罩
      - Mask Random-----------------随机遮罩

#### Shape Splatter Blend Color/形状溅射颜色混合
用来给形状溅射添加颜色，使用时把Shape Splatter节点的Splatter Data 1和Splatter Data 2输出端口分别连接到Shape Splatter Blend Color节点的Splatter Data 1和Splatter Data 2输入端口，将背景色的节点连接到Background Color端口，溅射颜色分别输入到几个Pattern端口

## Filters/滤镜
### Adjustments/调整
#### Histogram Scan/直方图扫描
和Levels功能类似，对黑白范围进行调整，相当于Levels直方图上方的三个游标，比Levels好的一点是可以进行参数暴露
#### Histogram Range/直方图范围
和Levels功能类似，对黑白范围进行调整，相当于Levels直方图下方的两个游标，比Levels好的一点是可以进行参数暴露
#### Highpass/高通
用来降低对比度

### Blurs/模糊
#### Blur HQ/高品质模糊
比原子节点中的Blur效果好一点
#### Non Uniform Blur/不统一模糊
会根据灰度的不同和各向异性强度，进行不同程度的模糊
  - Instance Parameters---------实例参数
    - Intensity-------------------强度
    - Anisotropy------------------各向异性
    - Asymmetry-------------------不对称性
    - Samples---------------------采样，采样值越高，黑白过渡越平滑，一般设为8


#### Slope Blur/倾斜模糊
原理类似于雕刻，会基于渐变方向对输入的图像进行模糊处理
  - Instance Parameters---------实例参数
    - Samples---------------------采样，采样值越高，黑白过渡越平滑，一般设为8
    - Intensity-------------------强度
    - Mode------------------------模式
      - Blur------------------------整体进行倾斜
      - Min-------------------------黑色部分向白色部分推离
      - Max-------------------------白色部分向黑色部分推离

### Effects/效果
#### Curvature Smooth/曲率平滑
一般用这个节点将法线贴图中的细节提取出来生成一张灰度图，获取法线信息
#### Ambient Occlusion(HBAO)/基于水平的环境吸收

### Transforms/变换
#### Safe Transform/安全变换
和原子节点中的变换作用相同，且在变换中不会产生接缝



## Material Filters/材质滤镜
### Blending
#### Material Color Blend/材质颜色混合
可以用来最后给材质添加灰尘、污渍等效果，还可以对最终输出的各通道贴图进行最后的调整

### PBR Utilities
#### Base Material/基础材质
  - Base Parameters-------------基础参数
  - Instance Parameters---------实例参数
    - PBR Workflow----------------PBR工作流程
      - Metal-Roughness-------------金属材质
      - Specular-Glossiness---------绝缘体材质
    - Material Preset-------------材质预设
    - Base Color------------------基础颜色
    - Height----------------------高度参数
      - Height Range----------------高度范围
※※※※※注意如果想让材质输出的高度图与制作的高度保持一致，需要把Height Range设为1
    - User-Defind Maps------------自定义映射，用来激活输入端口

#### PBR BaseColor(Metallic) Validate/PBR颜色（金属性）验证
检验颜色是否在PBR颜色范围内，如果验证为绿色，则在PBR颜色范围内，如果验证为红色，则不在PBR颜色范围内

### Scan Processing
#### Crop/裁切
会出现一个选框，从整个纹理上裁切一部分


## Mesh Adaptive/网格自适应
用来在最后给材质表面增加一些灰尘、污渍等效果
### Mask Generators/遮罩生成器
用来生成灰尘、污渍遮罩，再通过Material Color Blend与原来的材质混合
#### Dirt/肮脏
用来给材质表面增加污渍
- 输入端口
  - Ambient Occlusion-----------与Base Material的Ambient Occlusion输出端口连接
  - Curvature-------------------Base Material的Normal输出端口连接一个Curvature Smooth节点，将法线信息转化为曲率，再连入Curvature端口
- 输出端口
  - Mask------------------------连接到Material Color Blend的Greyscale Mask输入端口

## Functions/函数节点
程序提供的函数预设，在函数面板中使用



# Graph
## 菜单栏
### Link Creation Mode/切换材质节点的模式
- Standard--------------------标准模式，快捷键1
- Material--------------------材质模式，快捷键2
- Compact Material------------符合材质模式，快捷键3

## 右键菜单
### Creat
- Output Nodes----------------点击后会在所有输出端口自动创建节点，一般在输出贴图时使用


# 3D View
## Scnce

## Materials
### Difinitions/定义
#### blinn着色器
#### Lambert着色器
#### mesh_info/网格信息
#### physically_metallic_roughness/基于物理的金属粗糙度着色，这个着色器所有的光线都是来自HDRI贴图的
  - Parallax Occlusion----------视差映射
  - Tesselation-----------------曲面细分，一般都要选择为曲面细分

## Environment/环境
### Edit/设置
- Display Component-----------显示控制，控制HDR是否可见
- Environment Component-------环境控制
  - Exposure--------------------曝光度
  - Rotation Angle--------------HDR旋转,快捷键Shift+Ctrl+鼠标右键左右拖动

## Light
专门针对Blinn材质使用的，制作金属等大部分常用材质时用不到

## Camera

# 2D View
**快捷键Alt+鼠标右键拖动缩放视图**
## 菜单栏
### Toggle Repeated Tiling on or off/开启或关闭平铺
快捷键 空格


*将子面板数值暴露到主面板的方法*
将子面板中重要的、在使用中可以调节的参数暴露到主面板，可以方便以后在引用这个子面板时调节。在将材质导入UE时可以有暴露参数可以调节材质细节
方法：
1. 点击要暴露的参数右上角的曲线图标，选择Expose
2. 设置暴露参数的名称，SD会自动根据数据类型提供一个默认的参数名，但提供的参数名可能有好几个节点的相同参数共同使用，一般要修改成一个唯一的参数名
3. 在子面板的空白处双击进入面板父层级设置，在Input Parameters中设置暴露参数的数据类型、数据编辑方式、默认值、最小值、最大值，还可以将暴露参数打组，点击右上角的眼睛，可以预览暴露参数实际显示状态


# Roughness贴图制作方法
添加一个Invert节点将AO贴图反相，添加一个Level节点进行调整，再添加一个Histogram Range节点来控制粗糙强度，再连接到主节点的Roughness输入端口
